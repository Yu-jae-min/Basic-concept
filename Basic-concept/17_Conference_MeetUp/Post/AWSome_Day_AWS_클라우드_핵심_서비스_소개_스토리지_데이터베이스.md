# **[AWSome Day] AWS 클라우드 핵심 서비스 소개: 스토리지, 데이터베이스**

23년 06월 14일

<br>

## **3. AWS 클라우드 핵심 서비스 소개:  스토리지, 데이터베이스**

### **3-1. 데이터베이스**

<img width="674" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_01" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/70990e3c-0669-402a-85ab-999716a829d6">

AWS 제공하는 데이터베이스에 대해서 알아보자. 먼저 AWS에서 데이터베이스를 사용하는 두 가지 방법에 대해 알아보자. AWS의 Amazon EC2 인스턴스 위에 직접 데이터베이스를 구축해서 사용하는 옵션이 왼쪽에 나와있고 오른쪽에는 AWS 관리형 데이터베이스를 사용하는 옵션이 있는데 각기 다른 장점을 가지고 있다.

먼저 왼쪽과 같이 Amazon EC2 인스턴스에서 데이터베이스 소프트웨어를 호스팅할 때의 이점이다. 운영 체제 수준에 액세 해야할 수 있는 세밀한 조정이 필요한 경우에 이렇게 Amazon EC2 인스턴스 위에서 데이터베이스를 직접 호스팅 할 수 있다. 또한 현재 AWS에서 지원하지 않는 상용 DB 소프트웨어를 직접 구축할 수 있다.

다음은 AWS 데이터베이스 서비스를 사용할 때의 이점이다. 데이터베이스 프로비저닝, 백업과 복구 작업 실행, 보안 패치와 스토리지 및 사소한 버전 업데이트와 같은 관리 작업은 AWS가 해결하므로 본연의 비지니스와 애플리케이션에 집중할 수 있다. 예를 들면 스탠바이 데이터베이스를 직접 설치하고 관리할 필요 없이 원 클릭으로 다른 가용영역에 스탠바이 DB를 구성하고 데이터를 동기화하는 Multi AZ기능을 사용할 수 있다. 백업 또는 특정 시점으로 데이터베이스를 복구하는 작업을 관리할 필요가 없다. 일상적인 데이터베이스 관리 대신 성능 조정이나 스키마 최적화 같은 고차원적인 DB작업에 집중할 수 있다. 요약하면 AWS에서 제공하는 관리형 서비스를 이용하여 DB관리와 관련 된 여러 복잡한 작업을 AWS에 위임하고 이외의 중요한 비지니스에 집중할 수 있게 된다.

<br>
<br>

### **3-2. 목적별 데이터베이스**

<img width="677" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_02" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/cf26842f-7ba7-4ae0-be0c-b197000380af">

AWS에서는 다양한 DB 옵션을 제공한다. 관계형, 키 값, 인메모리, 문서, 와이드 컬럼, 그래프, 원장 및 시계열 데이터베이스를 비롯하여 다양한 데이터 모델을 지원하는 15개 이상의 목적별 엔진을 제공한다. 이렇게 다양한 AWS DB는 다양한 데이터 모델을 지원하므로 고객은 사용사례에 기반하여 확장성이 뛰어난 분산 애플리케이션을 손쉽게 구축할 수 있다. 위 이미지에 보이듯이 AWS에서 제공하는 대표적인 관리형 SQL DB로는 `Amazon RDS`가 있으며 MySQL 및 PostgreSQL과 호환되는 완전 관리형 SQL DB 엔진으로는 `Amazon Aurora`가 있다. 데이터 웨어하우스 서비스로는 `Amazon Redshift` 서비스를 제공하고 있다. 비관계형 데이터베이스, 즉 NoSQL DB는 완전관리형 키값 데이터 베이스인 `Amazon DynamoDB`가 있고 MongoDB와 같이 문서형 데이터를 처리할 수 있는 `Amazon DocumentDB`, 인메모리 캐시 서비스로서 Redis와 Memcached를 사용할 수 있는 `Amazon ElastiCache`, 그래프 DB로 `Amazon Neptune`을 사용할 수 있다. `Amazon QLDB`는 원장 DB 서비스로 모든 애플리케이션의 트랜잭션에 대하여 확장 가능하고 변경 불가능하며 암호화 방식으로 검증 가능한 기록을 유지하는 중앙에 집중되고 신뢰할 수 있는 권한을 제공한다. 시계열 데이터베이스인 `Amazon Timestream`은 여러 시간 간격에 걸친 쿼리를 포함하고 시간이 지남에 따라 변하는 데이터를 효율적으로 수집 및 통합하고 이런 데이터에서 인사이트를 도출한다. AWS DB를 사용하면 서버 프로비저닝, 패치 작업 구성 또는 백업과 같은 DB 관리 테스크에 대해 걱정할 필요가 없다. 따라서 사용자는 애플리케이션 개발에 더욱 집중할 수 있다.

<br>
<br>

### **3-3. Amazon RDS**

<img width="674" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_03" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/589a7d59-028a-4d85-aea8-989fee76b459">

우선 첫번째로 살펴볼 것은 `Amazon RDS`이다. Amazon Relational Database Service의 약자로 하드웨어 프로비저닝, 데이터베이스 설정, 패치 및 백업과 같은 시간 소모적인 관리 작업을 자동화하는 한편 비용 효율적이고 확장 가능한 용량을 제공하는 관리형 SQL 데이터베이스이다. 사용자는 애플리케이션 개발에 집중할 수 있도록 애플리케이션에 필요한 빠른 성능, 고가용성, 보안 및 호환성을 제공할 수 있도록 지원한다. `Amazon RDS`는 다양한 데이터베이스 엔진을 제공한다. Amazon RDS for Aurora, PostgreSQL, MySQL, MariaDB, Oracle 및 Microsoft SQL Server 엔진 중에서 선택할 수 있다. `Amazon RDS`는 데이터베이스 생성 시작 후 몇 분이면 프로덕션 급 관계형 DB의 성능을 사용할 수 있다. DB 구축을 위해서 해야하는 하드, 랙 등 하드웨어 설치 작업, DB 패치, 업데이트, 백업 등 여러가지 복잡한 작업을 AWS에 위임하고 사용자는 비지니스에 더욱 집중할 수 있다. 대부분의 경우 DB 가동을 중단하지 않고 마우스 클릭 몇 번만으로 데이터베이스 컴퓨팅 및 스토리지 리소스의 용량을 확장할 수 있다. `Amazon RDS`는 안정성이 높은 AWS 인프라에서 실행된다. 또한 Multi AZ 기능을 통해서 여러 가용 영역에 DB 인스턴스를 여러 대 프로비저닝 할 수 있어 DB 이중화를 쉽게 구축할 수 있다.

<br>
<br>

### **3-4. Amazon Aurora**

<img width="678" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_04" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/72665fb1-b021-4060-ab43-4795751db033">

앞에서 살펴본 것과 같이 기존의 상용 또는 오픈소스 데이터 베이스 엔진 외에 AWS에서 자체적으로 개발한 `Amazon Aurora` 데이터베이스 엔진도 제공한다. `Amazon Aurora`는 클라우드를 위해 구축된 관계형 데이터베이스이며 MySQL 및 PostgreSQL 엔진과 호환된다. `Amazon Aurora`는 상용 데이터베이스와 비교하여 데이터베이스 비용을 90% 이상 낮추면서도 데이터베이스의 안정성과 가용성은 높일 수 있다. `Amazon Aurora`는 완전 관리형 서비스로서 프로비저닝, 패치 적용, 백업, 복원, 장애 탐지, 복구 등 시간이 많이 소요되는 작업을 자동화함으로서 시간을 절약하는데 도움이 된다. 또한 성능은 표준 MySQL 데이터베이스보다 최대 5배 빠르고 표준 PostgreSQL 데이터베이스보다 3배 빠르다. `Amazon Aurora`는 내결함성을 갖춘 자가 복구 분산 스토리지 시스템으로 데이터베이스 인스턴스당 최대 64TB까지 자동으로 확장된다. 읽기 복제본은 최대 15개까지 생성할 수 있다. 따라서 기존의 SQL DB에서 읽기, 쓰기 성능의 한계를 느꼈다면 `Amazon Aurora`의 사용을 고려해볼 수 있다.

<br>
<br>

### **3-5. Amazon DynamoDB**

<img width="677" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_05" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/fe83a931-669f-425b-aaa8-746bb9296232">

다음은 대표적인 NoSQL 데이터베이스인 `Amazon DynamoDB`이다. `Amazon DynamoDB`는 규모와 상관없이 10밀리초 미만의 지연 시간이 일관되게 요구되는 모든 애플리케이션을 위한 빠르고 유연성이 뛰어난 비관계형 데이터베이스 서비스이다. 또한 완전 관리형 클라우드 데이터베이스로서 키 값과 문서 데이터 모델을 모두 지원한다. `Amazon DynamoDB`의 특징에 대해 살펴보자.

1. `Amazon DynamoDB`는 완전 관리형 NoSQL 데이터베이스 서비스이다. 서버를 프로비저닝하거나 패치를 적용하거나 관리할 필요가 없으며 소프트웨어를 설치하거나 관리하거나 운영할 필요도 없다. 가용성과 내결함성을 지원하는 기능이 내장되어 있어서 이러한 기능을 위해 애플리케이션을 설계할 필요가 없다. 사용자가 데이터베이스 테이블을 생성하고 읽기, 쓰기 용량 모드를 설정하기만 하면 나머지는 시스템에서 자동으로 처리한다.
2. 지연 시간이 낮다. `Amazon DynamoDB`의 평균 처리 시간은 10밀리초 미만이다. 데이터 볼륨이 늘어나고 애플리케이션 성능에 대한 요구가 증가하게 되면 `Amazon DynamoDB`는 용량에 맞게 테이블을 자동으로 조정하므로 별도로 관리하지 않아도 성능을 유지한다.
3. `Amazon DynamoDB`에서는 세분화된 액세스 제어를 할 수 있다. AWS Identity and Access Management(IAM)를 사용하여 `Amazon DynamoDB`에 대한 액세스 권한을 관리하고 보안 정책을 구현할 수 있다. 각 사용자의 액세스를 특정 아이템, 특정 속성별로 세부적으로 권한을 제어할 수 있다.
4. 유연성이 뛰어나다. `Amazon DynamoDB`는 AWS Management Console, AWS CLI 또는 AWS SDK를 사용하여 `Amazon DynamoDB` 테이블에 항목을 쓰고, 읽고, 업데이트하고 삭제할 수 있다. AWS SDK를 사용해서 원하는 프로그래밍 언어로 코드를 작성해서 `Amazon DynamoDB` 테이블을 생성하거나 항목에 대한 CRUD 애플리케이션을 개발할 수 있다.

<br>
<br>

### **3-6. 데모 테스트**

이번 데모에서 Amazon EC2, Amazon DynamoDB 그리고 Amazon S3를 이용해 사진 공유 웹 애플리케이션을 배포하고 테스트해보자. 앞선 시간에 설명한 AWS 서비스들을 연동하여 End-to-End 솔루션을 구현해보고 전체적인 아키텍처를 확인해볼 수 있을 것이다. 주요 아키텍처 구조를 살펴보자.

<img width="712" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_06" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/f6fe022f-2628-4dfb-ac52-b84242f991dd">

먼저 사진 공유 웹 사이트는 Amazon EC2 인스턴스에 호스팅 된 웹서버에 배포된다.

<img width="821" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_07" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/fdff33ee-f411-493a-985d-c7f442d38cc3">

또 이 데모의 마지막 부분에서 최종 사용자의 입장에서 사진을 웹 사이트에 업로드하여 테스트 해볼 것이다.

<img width="740" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_08" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/9d4f1fc8-6445-46b7-b3de-6631465ea6c3">

웹 애플리케이션이 사진을 전달받으면 사진의 썸네일을 생성한다. 이후 원본 이미지와 썸네일 이미지를 Amazon S3 버킷에 저장한다.

<img width="722" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_09" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/e36eb36a-a85f-444c-8862-28efdb172fbb">

추가로 사진의 제목, 설명, 태그와 같은 메타데이터를 Amazon DynamoDB 테이블에 저장할 것이다.

<br>

#### **3-6-1. S3 버킷 생성 및 정책 설정**

첫번째 작업은 사진과 같은 미디어 컨텐츠를 저장할 S3 버킷을 생성하고 권한을 설정하는 작업이다.

1. AWS Management Console에서 S3를 검색하고 선택하여 S3 대시보드로 이동한다.
2. Create Bucket 버튼을 클릭하고 Bucket name을 설정한다.
3. 기본적으로 S3 버킷은 퍼블릭 액세스할 수 없다. 데모에서는 컨텐츠를 다운로드 받을 수 있도록 퍼블릭 액세스를 허용하도록 설정할 것이다. 따라서스크롤을 내려 Block all public access 체크 박스를 해제한다.
4. 스크롤을 다시 내려 아래의 확인 창에서 버킷과 객체가 퍼블릭 상태가 되는 것을 이해했는지 확인하는데 I acknowledge that the ~ becoming public 체크 박스를 선택한다.
5. 나머지는 기본 설정으로 두고 최하단 Create bucket 버튼을 클릭한다.
6. 버킷 내 컨텐츠의 다운로드는 허용하지만 버킷 내 다른 객체 리스트를 확인하거나 삭제하지 않도록 해야 한다. 버킷리스트에서 방금 전 생성한 버킷 링크를 클릭한다. 그 후 버킷과 객체에 대한 액세스를 제어하기 위해 S3 버킷 정책을 설정한다. 상단 Permissions 탭으로 이동한다.
7. 스크롤하여 Bucket policy 섹션으로 이동하여 Edit 버튼을 클릭한다.
8. 준비한 정책을 Policy 편집창에 입력하고 방금 전 생성한 버킷의 이름으로 수정한다. 정책의 Action에서 S3의 GetObject만 허용된 것을 확인할 수 있다.

   <img width="978" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_10" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/a1cd371f-359b-4d26-a7e7-fa852c131dfd">

9. 스크롤하여 Save changes를 클릭하여 저장한다.

이렇게 미디어 컨텐츠를 저장할 S3 버킷을 성공적으로 생성했고 버킷 정책을 설정하는 작업을 마쳤다.

<br>

#### **3-6-2. 메타데이터 저장을 위한 데이터베이스 생성**

이제 사진의 제목, 설명, 태그 등의 메타데이터를 저장하기 위한 데이터베이스를 생성한다. 이를 위해서 `Amazon DynameDB` 서비스를 이용해 데이터를 저장해볼 것이다.

1. 검색창에서 DynamoDB를 검색하고 선택한다.
2. Create table 버튼을 클릭하여 테이블을 생성한다.
3. 테이블 이름과 기본 키인 파티션 키를 지정한다.

   <img width="973" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_11" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/0072ef44-0088-41d4-b9e2-b28185486c84">

4. 나머지는 기본 설정으로 두고 하단으로 스크롤하여 Create table 버튼을 클릭하여 테이블을 생성한다. DynamoDB는 간단한 설정만으로도 데이터를 저장할 수 있는 데이터베이스이다. 아래 이미지는 테이블이 생성 중인 상태이며 새로고침 버튼을 누르면 수 초만에 사용가능한 상태가 된다.

   <img width="982" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_12" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/33686a0f-dc77-4967-b36c-ce3115ccf263">

   <img width="994" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_13" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/6d35df2a-3b3e-4b93-8630-dcca1fd5f679">

<br>

#### **3-6-3. 웹서버 생성**

다음 작업은 사진 공유 웹 애플리케이션을 실행할 웹서버를 생성하기 위해서 `Amazon EC2` 서비스를 이용해볼 것이다.

1. 검색창에 EC2를 검색하여 Amazon EC2 서비스로 이동한다.
2. Instances(running) 클릭 → Instance state = running의 우측 X표 버튼 클릭 → 아래 인스턴스 리스트가 변경된 후 Launch Instance 버튼을 클릭한다.
3. 새롭게 생성할 인스턴스의 구성 정보를 설정한다. 인스턴스의 이름을 My Photo Website로 지정해본다.
4. Amazon Machine Image 즉 AMI를 선택한다. AMI는 생성할 EC2 인스턴스에서 사용할 운영체제 등에 대한 정보를 제공한다. Quick Start에서 자주 사용되는 AMI를 확인할 수 있으며 사용자가 직접 생성한 AMI나 마켓 플레이스에서 제공하는 AMI를 선택할 수 있다. 이 데모에서는 Amazon Linux 2를 선택하겠다.

   <img width="989" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_14" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/7b8c4f5c-28e2-4a5d-afba-afa5d6de396e">

5. 다음으로 인스턴스 타입을 선택한다. 인스턴스 타입은 CPU, 메모리, 네트워크 조합으로 이루어져 있으며 원하는 타입을 선택하여 인스턴스를 생성할 수 있다. 해당 데모에서는 간단한 웹 애플리케이션이므로 범용적으로 사용하는 t2.micro 타입을 선택한다.
6. EC2 인스턴스에 원격 접속을 위해서 Key Pair를 설정할 수 있으나 이번 데모에서는 EC2 원격 접속을 하지 않기 때문에 Proceed without a key pair를 선택한다.

   <img width="995" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_15" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/b825b6dc-48ca-4127-b01f-bb3a7dc0c954">

7. Network settings 섹션에서 Edit 버트을 눌러 네트워크 환경을 설정한다. VPC는 데모를 위해 생성한 Awsome Day VPC를 선택한다. Subnet은 Public Subnet1을 선택한다.
8. Firewall은 Select existing security group을 선택한다.
9. Common security groups에서는 Security Group으로 Web Server Security Group(Web Server SG)을 선택한다. 이 보안 그룹은 HTTP트래픽을 허용하는 인바운드 룰을 가지고 있다.
10. Storage 설정은 기본값으로 남겨둔다. EC2의 데이터는 블록 스토리지인 EBS에 저장된다.
11. 이제 Advanced details 섹션을 확장하여 상세 설정을 한다. IAM instance profile까지 스크롤을 내린 후 드랍 다운 버튼에서 EC2에서 설정할 역할을 선택한다.

    <img width="999" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_16" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/877db126-ac2d-46e0-a826-08574044a68d">

12. 하단으로 스크롤 한 뒤 Termination protection을 활성화하여 인스턴스가 실수로 종료되지 않도록 지정한다. Enable로 바꾸면 된다.
13. User data를 입력하는 부분까지 스크롤을 내린다. 인스턴스가 런치할 때 수행할 설정 작업 또는 스크립트를 User data에 입력하면 인스턴스가 런치될 때 User data의 내용이 자동으로 실행된다. 지금 생성하려고 하는 인스턴스는 Linux 운영체제를 사용하므로 shell script를 작성하여 입력한다. 스크립트에 앞서 생성한 S3 버킷의 이름과 리전을 적절히 채워 넣는다. 스크립트에는 yum install 명령을 이용해 필요한 라이브러리를 설치하고 웹 애플리케이션의 소스 코드를 다운로드 받아 배포하고 웹 서버를 시작하여 활성상태로 만드는 과정이 작성되어 있다.

    <img width="997" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_17" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/dbd4767c-b4d3-40cc-991d-fdbe4d13fd7b">

14. 설정이 문제 없는지 확인한 후 문제가 없다면 Launch instance 버튼을 클릭하여 인스턴스를 생성한다. Success 화면으로 넘어가 인스턴스가 성공적으로 생성되었음을 확인할 수 있다.

    <img width="997" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_18" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/e25339a6-fd36-47dd-8f71-161ff888fe6f">

15. 위 페이지에서 하단으로 스크롤한 뒤 View all instances를 선택하여 인스턴스 페이지로 이동한다. 방금 전 생성한 인스턴스가 Pending 상태임을 확인할 수 있다. 인스턴스 런칭이 시작되었다는 의미이며 부팅이 시작되면 Running 상태로 변경된다. 인스턴스 상태가 Running이고 Status check가 모두 완료될 때까지 중간 중간 새로고침하며 잠시 기다린다. 하단 두번째 이미지와 같이 instance state와 status check에 초록불이 들어오면 인스턴스가 성공적으로 확인할 수 있다.

    <img width="998" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_19" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/8923a976-4b1b-4f96-8fc8-b4dac7e12e24">

    <img width="998" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_20" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/84b4cad4-9db6-4d2a-bf1f-b92ac36bbbf7">

<br>

#### **3-6-4. 데모 웹 애플리케이션 테스트**

마지막 작업으로 웹 애플리케이션을 테스트해보자.

1. 방금 전 생성한 인스턴스를 선택한 후 Detail 탭에서 인스턴스의 상세정보를 확인한다.

   <img width="999" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_21" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/0d79c3f2-a8b5-4090-adbb-55d1c938b398">

2. Public IPv4 address를 클립보드에 복사한 뒤 웹 브라우저 주소창에 붙여넣기 하여 웹 애플리케이션에 접속해본다. 이번 데모에서 구현한 사진 공유 웹 애플리케이션이 잘 확인된다.

   <img width="992" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_22" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/16735c87-be85-453f-aa5a-34995395a200">

3. 간단히 테스트해보기 위해 제목, 설명, 태그 등 데이터를 입력하고 사진을 업로드한다.

   <img width="995" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_23" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/8a9de780-a977-4d12-a3c9-cbaa7a480baf">

4. 테스트를 위해 입력한 정보와 사진의 썸네일이 웹 페이지에 성공적으로 표시된다.

   <img width="992" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_24" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/9f9f6695-7852-4470-91a3-8f7c25a65763">

5. 우리가 입력한 데이터가 저장되어 있는 DynamoDB로 가서 정말 데이터가 잘 저장되어 있는지 확인해본다. Amazon Web 사이트로 돌아가 DynamoDB 서비스로 이동한다.
6. 왼쪽의 메뉴 중 Tables 아래의 Explore items를 선택한다.

   <img width="992" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_25" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/fc1de48a-f459-4034-aada-619a1f5d1acb">

7. 앞서 생성한 테이블인 myTable을 선택한다.

   <img width="990" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_26" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/9e9c9045-8534-47d4-a599-73a57ce3b1e0">

8. 하나의 아이템이 검색되면 링크를 클릭하여 속성을 확인할 수 있다.

   <img width="998" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_27" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/6ada41ff-3667-4468-ab65-14bca670cd5a">

9. 웹 애플리케이션에서 입력한 데이터가 DynamoDB 테이블에 입력되어 있는 것을 확인할 수 있다.

   <img width="994" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_28" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/bdd68863-4bc0-4666-a251-a3837d8e62df">

10. 다음은 업로드한 사진이 저장되어 있는 Amazon S3로 이동해보자. Amazon Web 사이트로 돌아가 S3 서비스로 이동 후 앞서 생성한 버킷으로 접근한다.
11. Objects 탭으로 이동한다.

    <img width="999" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_29" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/f2e148c7-7c77-47ce-9558-acf9bc6ac249">

12. 새로고침을 눌러 원본 사진과 썸네일로 생성한 사진 모두 객체로 저장되어 있는지 확인한다.

    <img width="999" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_30" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/b56f7f68-8c00-4b33-b6e7-2da4438d9e45">

이번 데모에서는 `Amazon EC2`와 `Amazon DynamoDB`, `Amazon S3`를 이용하여 사진 공유 웹 사이트를 성공적으로 배포하고 테스트했다.

<br>
<br>

### **3-7. 핵심 사항 요약**

<img width="675" alt="AWS_클라우드_핵심_서비스_소개_스토리지_데이터베이스_31" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/e0988d43-4f4d-4fa0-b172-b429b4555726">

- AWS에서는 `관계형 데이터베이스`와 `비관계형 데이터베이스`에 대한 다양한 옵션을 제공하며 각 목적에 따라 다양한 엔진을 제공하므로 사용자는 원하는 서비스를 선택할 수 있다.
- NoSQL 데이터베이스, 대표적으로 `Amazon DynamoDB`는 모든 규모에서 고성능 애플리케이션을 실행하도록 설계된 완전관리형 서버리스 키 값 NoSQL 데이터베이스이다.

<br>
