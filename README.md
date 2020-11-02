# GCP

## introduce
- 기본 server 관리의 문제점
   - 구글이 조사해본 바로는 전세계 있는 기업들이 서버를 운영할 때 Utilization이 10% 이하
혹시라도 서버가 터질 수 있기 때문에.. 그리고 서버를 관리하는 과정에서 baby sitting이라 불리는 온갖 잡다한 문제가 많이 발생함.
   - 문제를 해결하기 위해서 나왔던 개념 중의 하나가 Virtual Machine
   - 그 다음이 cloud. cloud의 목적은 완전 자동화
   - [구글 클라우드 서버가 위치한 지역](clould.google.com/about/locations)
   
## 용어
- zone
- region : 전세계 24개의 region
- pop : region과 region을 연결하기 전 위치한 거.. 자세한건 잘 모름

## Resource hierarchy level
- Org-node : Samsung.com (회사 전체)
- folders : 조직도 (project를 관리하기 위한 개념)
- Project : 조직 내부 태스크
   - ID, name, number
   - 권한 관리 : 이메일로 유저 id를 관리함. clould identity로 동기화 시킬 수 있다.
      - 3가지 role이 존재,
         - primitive : project level에서 권한 설정 (Owner, Editor, Viewer, Billing Administrator, Brwoser) GCP -> IAMM admin -> add. service account를 통해서 resource 별 권한 설정이 가능한 것.
         - predefind : resource level에서 권한 설정
         - custom

## cloud 제품
- SASS(Software AS a Service) : market place에 있는 여러 application이 있음.
- VPC(Vertual Private Cloud) : SDN(Software-Defined Network)
- 외부 IP, 내부 IP
- project 하위에 여러 resource를 만들수 있고 각 resource 끼리는 VPC로 통신한다. 같은 네트워크로 묶이면 서로 통신 가능(서로 zone이 다르더라도..)
