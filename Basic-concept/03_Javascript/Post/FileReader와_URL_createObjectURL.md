# **[Javascript] FileReader와 URL.createObjectURL**

23년 06월 21일

<br>

## **# FileReader와 URL.createObjectURL**

이미지 미리보기와 같이 파일 입출력 관련 기능을 구현할 때 사용하는 대표적인 메소드로는 `FileReader`와 `URL.createObjectURL` 방식이 있다.

<br>
<br>

## **1. FileReader**

첫 번째로 `FileReader` 방식이다. `FileReader` 객체는 File객체나 Blob객체에 저장된 바이너리 데이터를 비동기적으로 읽어들이는 객체이다. 데이터를 읽는 방식에 따라 4가지 메서드가 제공된다.

1. **FileReader.prototype.readAsArrayBuffer(File | Blob) :** result로 ArrayBuffer 반환
2. **FileReader.prototype.readAsBinaryString(File | Blob) :** result로 String 반환
3. **FileReader.prototype.readAsDataURL(File | Blob) :** result로 객체 URL 반환
4. **FileReader.prototype.readAsText(File | Blob) :** result로 텍스트 반환

읽기가 완료되면 `FileReader` 객체에 onload 이벤트가 발생하며, `FileReader객체.result`로 결과물을 참조할 수 있다.

```jsx
import { useState, useRef } from "react";

const FileUploadTest = () => {
  const [fileReaderThumbnail, setFileReaderThumbnail] = useState<any>();
  const ref = useRef<any>(null);

  const onClick = () => {
    ref.current.click();
  };

  const encodeFile = (fileBlob: any) => {
    // FileReader 방식
    const reader = new FileReader();

    if (!fileBlob) return;

    reader.readAsDataURL(fileBlob);

    return new Promise((resolve: any) => {
      reader.onload = () => {
        const result = reader.result;

        setFileReaderThumbnail(result);

        resolve();
      };
    });
  };

  const onFileReaderChange = (e: any) => {
    const { files } = e.target;

    if (!files || !files[0]) return;

    const uploadImage = files[0];

    encodeFile(uploadImage);
  };

  return (
    <div>
      <div className="main">
        <div className="section">
          <h1>File Input by FileReader</h1>
          <div className="image-wrapper">
            {fileReaderThumbnail ? (
              <img src={fileReaderThumbnail} alt="thumbnail" />
            ) : (
              "이미지 미리보기"
            )}
          </div>
          <button onClick={onClick}>
            File Reader Upload
            <input
              hidden
              type="file"
              accept="image/jpg,image/png,image/jpeg,image/gif"
              name="image-input"
              onChange={onFileReaderChange}
              ref={ref}
            />
          </button>
        </div>
      </div>
    </div>
  );
};

export default FileUploadTest;
```

<br>
<br>

## **2. URL.createObjectURL**

두 번째로 `URL.createObjectURL` 방식이다. File객체나 Blob객체를 인자로 받아 임시 URL을 생성하여 상사용한다. 해당 URL은 생성된 페이지 내에서만 유효하다.

`URL.createObjectURL` 사용 시 주의할 점은 문서가 닫히거나(페이지 이동) `URL.revokeObjectURL` 를 호출하지 않으면 생성한 고유 URL은 메모리에 계속 상주하게 된다. 즉 메모리 누수가 발생할 수 있다. 그러므로 사용하지 않을 때에는 `URL.revokeObjectURL`를 통해 생성한 객체 URL을 제거해주어야한다.

```jsx
import { useState, useRef } from "react";

const FileUploadTest = () => {
  const [URLThumbnail, setURLThumbnail] = useState<any>();
  const ref = useRef<any>(null);

  const onClick = () => {
    ref.current.click();
  };

  const createImageURL = (fileBlob: any) => {
    // createObjectURL 방식
    if (URLThumbnail) URL.revokeObjectURL(URLThumbnail);

    const url = URL.createObjectURL(fileBlob);

    setURLThumbnail(url);
  };

  const onImageChange = (e: any) => {
    const { files } = e.target;

    if (!files || !files[0]) return;

    const uploadImage = files[0];

    createImageURL(uploadImage);
  };

  return (
    <div>
      <div className="main">
        <div className="section">
          <h1>File Input by createObjectURL</h1>
          <div className="image-wrapper">
            {URLThumbnail ? (
              <img src={URLThumbnail} alt="thumbnail" />
            ) : (
              "이미지 미리보기"
            )}
          </div>
          <button onClick={onClick}>
            create object URL Upload
            <input
              hidden
              type="file"
              accept="image/jpg,image/png,image/jpeg,image/gif"
              name="image-input"
              onChange={onImageChange}
              ref={ref}
            />
          </button>
        </div>
      </div>
    </div>
  );
};

export default FileUploadTest;
```

<br>
<br>

## **3. FileReader vs URL.createObjectURL**

그렇다면 두 가지 방식의 차이점은 무엇일까? 두 가지 방식에 대해 비교해보자.

![FileReader와_URL_createObjectURL_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/3a6f13e8-1397-42ca-99af-5df64b3e2473)

<br>

### **3-3-1. 메모리**

![FileReader와_URL_createObjectURL_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/d3a14d2f-be05-47ca-88f7-32a1e271fd53)

- `FileReader` : base64 인코딩 string을 사용한다. createObjectURL에 비해 메모리를 더 사용하지만 사용하지 않을 때에는 가비지컬렉터에 의해 수집되어 제거된다. (위 이미지 중 파란 마카 표시 문자열)
- `URL.createObjectURL` : 포인터를 사용한다. FileReader에 비해 메모리를 덜 사용하지만 사용하지 않을 때에도 가비지컬렉터에 의해 수집되지 않기 때문에 수동으로 제거해주거나 페이지를 이탈해야한다. (위 이미지 중 빨간 밑줄 표시 문자열)

<br>

### **3-3-2. 속도 및 편의성**

- `FileReader` : File, Blob 객체를 읽고 base64 인코딩 string으로 변환하는데 까지 많은 작업을 거치고(read, load, result) 비동기적으로 처리되어야 하기 때문에 속도가 느리다.
- `URL.createObjectURL` : 동기적으로 동작하며 읽기 과정 없이 File, Blob 객체의 고유한 URL를 즉시 생성하므로 속도가 빠르다.

<br>

### **3-3-3. 수용 가능 용량**

- `FileReader` : 10mb 정도의 용량을 수용한다.
- `URL.createObjectURL` : Blob의 최대치에 가까운 800mb 정도의 용량까지 수용한다.

<br>
