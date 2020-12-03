# CDN

# CDN 이란?

CDN은 Content Delivery Network의 약자로 사용자 위치, Contents 원본 서버, 에지 서버 위치를 기준으로 Contents를 최종 사용자에게 전송할 수 있는 분산 노드로 구성된 네트워크

Contents란?
동영상, 오디오 스트림, 앱/게임/OS 업데이트와 같은 소프트웨어 다운로드, 의료 정보와 금융정보가 포함된 데이터 레코드 등 디지털 화 될 수 있는 모든 데이터

## 사용 예시

### 기본적인 예시

사용자가 원격지에 있는 서버로부터 Contents를 다운로드 받을 때 사용자의 위치 즉 물리적 거리에 따라 시간 지연이 발생할 수 있음

이를 보완하기 위해 CDN 서비스는 서버 자체를 여러곳에 두고 사용자가 Contents를 요청했을 때 제일 근접한 서버에서 처리하여 지연되는 시간을 줄여 줌

### 온라인 게임

온라인 게임은 OBT(Open Beta Test)나 정식 서비스 시작 시점에 클라이언트 다운로드 수요가 급격하게 증가함

이때 콘텐츠 병목 현상이 일어나거나, 심한 경우 서버 다운도 발생할 수 있기 때문에 CDN이 필수적으로 사용

또한 대규모 업데이트를 위한 패치가 있을 경우에도 CDN을 사용

### 동영상 또는 e러닝 서비스

동영상과 음성은 적절한 트래픽 관리가 필수적

따라서 CDN을 많이 사용

# CDN 작동 원리

![Untitled](https://user-images.githubusercontent.com/48611456/100953338-bd56b280-3555-11eb-9373-29d7b69f795d.png)

1. End User가 특정 주소에 접근하여 Contents를 서버에 요청
2. DNS는 Contents에 대한 요청이 발생하면 End User와 가장 가까운 위치에 최적으로 배치된 CDN 서버에 End User가 매핑되고, 해당 서버는 요청된 파일의 캐싱 된 버전으로 응답
3. Contents를 캐싱하는 종류는 두 가지이며, Origin Server와 CDN에 있는 Edge Server의 동기화 진행

# CDN 캐싱 방식의 종류

## Static Caching

- 사용자의 요청이 없어도 Origin Server에 있는 Contents를 운영자가 미리 Cache Server에 복사
- 사용자가 Cache Server에 접속하여 Contents를 요청하면 무조건 그 Contents는 Cache Server에 있음
- 대부분의 국내 CDN에서 이 방식을 사용 (ex. 동영상 스트리밍 / 다운로드, NCSOFT 게임 파일 다운로드 등)

## Dynamic Caching

- 최초 Cache Server에는 Contents가 없음
- 사용자가 Contents를 요청하면 해당 Content가 있는지 확인하고, 없으면 Origin Server로 부터 다운로드 받아 사용자에게 전달
- 동일 Contents를 요청 받으면 캐싱된 Contents를 사용자에게 전달
- Contents는 일정 시간 (TTL)이 지나면 Cache Server에서 삭제될 수 있고, Origin Server를 통해 Contents Freshness 확인 후에 계속 가지고 있을 수 있음
- Akamai, Amazon과 같은 Global CDN 업체에서 이 방식을 사용

# CDN 장점

### 웹사이트 로딩 속도 개선

- 사용자가 신속하게 자신이 원하는 웹사이트에 접속 가능

### 인터넷 회선 비용 절감

- 사용 대역폭을 절약하여 비용을 절감 할 수 있음

### 컨텐츠 제공의 안정성

- 순간적으로 집중되는 인터넷 상의 트래픽을 분산
- 호스팅 서버의 고장이 발생할 경우 CDN 서버에서 일시적으로 대응 가능

### 웹사이트 보안 개선

- CDN 업체는 웹사이트 오리진 서버의 보호에 신경써야 함
- DDOS 사전 예방 가능