# Proxy

# Proxy 란?

![Untitled](https://user-images.githubusercontent.com/48611456/100953717-761cf180-3556-11eb-95df-29ea0fc7a823.png)

## Proxy 정의

- Proxy 란 '대리'라는 의미로 네트워크 상에서 대리로 통신을 수행하는 기능을 말 함

# Proxy 서버

- 네트워크 상에서 Proxy 기능을 수행하는 서버
- 보안상의 목적으로 사용 가능
- 캐싱을 통해 전송 시간 절약 및 트래픽을 줄여 병목 현상을 방지 가능
- Proxy 서버는 Forward Proxy와 Reverse Proxy로 나눔

## Forward Proxy

![Untitled 1](https://user-images.githubusercontent.com/48611456/100953722-77e6b500-3556-11eb-87a2-aba24eb4d0ae.png)

### Forward Proxy 란?

- 클라이언트와 서버 사이 중 클라이언트와 가깝게 위치하는 Proxy 서버
- 클라이언트가 서버에 리소스를 요청하면 Forward Proxy 서버가 대신 리소스를 요청 후 전달 및 캐싱
- 클라이언트가 서버에 요청한 리소스가 캐싱되어있다면 서버에 요청을 하지 않고 캐싱 된 데이터를 응답

### 장점

- 서버로 요청이 가는 트래픽을 줄이며, 비용이 저렴
- 클라이언트의 사용 요청을 제한할 수 있음

## Reverse Proxy

![Untitled 2](https://user-images.githubusercontent.com/48611456/100953725-7a490f00-3556-11eb-9114-ff75b992d5e0.png)

### Reverse Proxy 란?

- 인터넷 리소스 또는 인트라넷 리소스 앞에 위치시킨 Proxy 서버
- 클라이언트의 요청을 Reverse Proxy 서버가 대신 받아 WAS로 전달
- 정적 리소스 또는 캐싱이 되어있다면 WAS로 요청을 전달하지 않고 응답

### 장점

- 요청에 대한 정적 데이터 및 캐싱 된 데이터를 전달하여 서버의 부하를 줄임
- WAS의 직접 접근을 막아 보안에 용이

# 비교

## Proxy

- IP 헤더가 바뀜
- 클라이언트와 서버사이에 TCP Connection이 두번 일어남

## NAT

- IP 헤더가 바뀌는 것은 동일
- TCP Connection은 원래 클라이언트와 원래 서버끼리 맺음

## VPN

- IP 헤더가 바뀌는 것이 아님
- Tunneling을 통해서 Packet을 한번 더 Encapsulation 함