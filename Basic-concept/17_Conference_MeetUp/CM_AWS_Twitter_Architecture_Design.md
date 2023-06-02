# **[23/04/27] AWS 소모임 트위터 아키텍처 설계**

23년 4월 27일 AWS 소모임에서 주최하는 트위터 아키텍처 설계 밋업에 참여했다. 참여한 이유는 일단 라인쓰리 다음 feature가 feed였으며 아키텍처 설계에 대해 고민하던 찰나에 매우 적절한 밋업이 있어 참여하게 되었다.

밋업 장소는 성수역 무신사에서 진행되었으며 밋업 순서는 처음으로 무신사의 서비스 소개부터 시작되었다. 무신사 서비스 소개가 끝난 뒤 막간에 블랙프라이데이 썰(?)을 풀어주셨다. 블프 때 특정 시간에 몰리는 트래픽이 어마어마하고 그에 대응하기 위해 2-3달 전부터 준비(ex DB 증설)한다고 하셨다. 또 무신사 기술 블로그에 대해서도 소개해주셨는데 출퇴근 시간에 한번 씩 확인해봐야겠다. 무신사 소개가 끝난 후에는 20-30분 가량 네트워킹 시간을 가졌다. 무신사, 당근, 여러 스타트업 등 다양한 곳에서 근무하시는 개발자 분들과 대학생 분들도 계셨다. 이 때 입사한지 3개월 되신 나와 같은 0년차 뉴비분이 계셨는데 정말 잘하시는 것 같았다. 많이 반성하게 되는.. 흑흑..

네크워킹 시간이 끝나고 난 후 본격적으로 아키텍처를 설계하는 시간을 가졌다. phase 1~6으로 각각 다른 상황이 주어졌고 그 상황에 맞게 아키텍처 설계를 하는 것이었다. 설계하는 방식은 잼보드 앱을 활용하여 밋업에 참여한 개발자 중 해당 상황에 맞는 아키텍처가 떠오른 개발자가 손을 들어 구두로 아키텍처를 설명한 뒤 잼보드 앱에 시각화하여 표현하는 방식으로 진행되었다.

<br>
<br>

## **# 트위터 아키텍처 설계**

<br>

![CM_AWS_Twitter_Architecture_Design_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/108430dd-3631-49fa-9292-b90cc1c0c24e)

![CM_AWS_Twitter_Architecture_Design_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/fca067a3-42d8-4b2c-ba5c-ef8bce3b8d69)

![CM_AWS_Twitter_Architecture_Design_03](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/b0e2380b-abe3-4755-a02b-af1d9ebfb515)

<br>

- Phase 1

  - Browser - Server - DB

- Phase 2

  - Web Browser Public Subnet에 둘 수 있도록 하고 Public Subnet에 둘 때에 LB를 맨 앞에 둔다. 그리고 이게 ALB를 두면 WAF를 두고, NLB 라면 IP Base를 차단하고, Server의 Subnet위치는 크게 중요하지 않으니 Public Subnet에 둔다. DB는 private에 둔다. Public에는 구성상 실제 노출되는 instance가 없어야한다.

- Phase 3

  - Browser - WAF - Public Server : ALB - Server, Auto scaling - NAT - Private Server : DB

- Phase 4

  - Pre-Signed URL은 S3 Bucket을 바라본다. S3 앞에 Cloudfront를 붙힌다. (전략 중 하나는 엣지로케이션)

- Phase 5

  - 의견 1 : DynamoDB에 userid를 파티션키로 하나씩 옮겨간다. → DynamoDB에 있는 Stream 기능을사용한다. 그러면 실시간 처리가 가능하다. 현실은 Kafka를 써야한다. → Stream에서 컨슘하는 역할은 람다를 써서 가져간다.

    - 추가 질문 : 이전의 데이터는 어떻게 가져가겠는가?

      - 1. dynamoDB write unit왕창 때려넣어서 요기에 때려넣은 데이터를 DB로 넣겠다.

      - 2. DMS 성공사례가 없다. 또 TAM도 보장하지 않는다.

  - 의견 2 : PAI 단에서 dual write, 뒷단에서는 batch write 를 한다.

  - 의견 3 : Snapshot이 가장빠르다. 해당 snapshot 을 이용해서 만들어진다. 최신의 정보는 bin 로그를 정한다.

- Phase 6 : 이미지 참고

<br>
<br>

## **# 느낀점**

<br>

phase1~2까지는 알고 있었던 내용이었다. but.. phase3부터 전혀 몰랐던 내용들이 상당히 많았다. 그나마 phase4에서 aws에서 cdn을 담당하는 cloudfront, s3 bucket 등 개념 정도만 알고 있는 키워드들이 나와서 조금은 알아들었다. 하지만 나머지는 정말 넘사벽이었다.

사실 이번 밋업에 참여해서 내 개발적 지식이 증가했다라고 느낄 수는 없었다. 왜냐하면 인프라에 대해 백그라운드 지식이 너무 부족했기에 고수분들이 토론하는 내용에 대해 이해하는 것이 무리가 있었다. 하지만 얻어가는 것이 전혀 없지 않았다. 오히려 인프라를 공부해야겠다는 큰 동기 부여를 얻게 되었다.

<br>
<br>

## **# 참고 URL**

<br>

- https://www.youtube.com/watch?v=G5JvMWXldL4
- https://www.notion.so/2023-04-dc26956a126c464b8a16ee9b5ef46daa
