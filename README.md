# GCP

## introduce
- 기본 server 관리의 문제점
   - 구글이 조사해본 바로는 전세계 있는 기업들이 서버를 운영할 때 Utilization이 10% 이하
혹시라도 서버가 터질 수 있기 때문에.. 그리고 서버를 관리하는 과정에서 baby sitting이라 불리는 온갖 잡다한 문제가 많이 발생함.
   - 문제를 해결하기 위해서 나왔던 개념 중의 하나가 Virtual Machine
   - 그 다음이 cloud. cloud의 목적은 완전 자동화
   - [구글 클라우드 서버가 위치한 지역](clould.google.com/about/locations)
   
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

## Autoscaling
- 전통적 computer architecture는 CPU-Memory-Disk 구조로 flexible 하게 resource 조절이 힘들다.
- 그래서 VM를 구성할때, CPU, Memory만 결정하고 Disk를 따로 분리시켜서 network로 **1.3pbps(peta bit per sec)** 의 성능으로 데이터를 주고 받을 수 게 구성. 실제적으로 disk를 분리 시키면 데이터를 disk로 부터 load 하는 시간이 오래 걸리기 때문에 수많은 선으로 연결된 현재의 architecture가 구성이 됨. 이런 구성을 하게되면 disk를 마음껏 늘리고 줄일 수 있다. disk가 분리되어 있는 것이 핵심.

## 용어
- zone
- region : 전세계 24개의 region
- pop : region과 region을 연결하기 전 위치한 거.. 자세한건 잘 모름

- template : H/W & image (OS type)구성. MIG(Managed Instance Group)
- template을 통해서 instance group을 만들고 IG를 통해서 여러개의 VM을 만든다.
- User <-> Load Balancing(External IP) <-> Server(service 제공) 구성
  - Load Balancing 이하는 역할
    - 사용자의 traffic을 control
    - 지역별로 적합한 VM에 job을 할당
    - 문제가 있는 VM 체크 후, 정상 동작하는 VM에만 job을 할당**(health check)**
    - PoP에 Load Balancing이 구축이 된다.
    - 갑자기 traffic이 몰릴때 이를 알려주는 신호(pre-warming)도 필요없다.
    - pre-warming은 수강신청이라던가, black-friday라던가 등등 특정 이벤트에 트래픽이 마구 몰릴때, 이를 미리 알려주는 신호.
    - Protocol에 따른 다양한 load balancing이 존재함.
- VPC N/W Peering : 서로 다른 network 끼리 통신
- Shared VPC : 서로 다른 Project 끼리 통신
- SAL(Service Agreement Level) : 얼마나 해당 service가 잘 동작하는지 보장해주는 수치 (100은 100%)








