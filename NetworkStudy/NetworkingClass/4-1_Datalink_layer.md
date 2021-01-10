# Datalink Layer
- 상위 IP Layer에서 넘어온 정보(Packet)에 Ethernet header 추가 -> Frame
## Ethernet Protocol
- Source(자신의 Interface MAC), Destination(Next Hop IP에대한 MAC)-> MAC Address가 저장이 됨
- LAN에서만 사용되었다가 현재는 WAN에서도 사용되고 있다.
### MAC vs IP
- MAC : Phyical Address
- IP : Logical Address(바뀔 수 있음)
- +왜 얘네 둘이 있어야 할까?!

## ARP(Address Resolution Protocol)
- Ethernet 환경에서 가장 중요한 프로토콜
- Ethernet Header 상의 DMAC 주소를 완성하기 위해 사용
- IP Header에서 DIP 확인, 어디로 보낼지를 결정
- Broadcast 방식(Source Mac | FFFF | Next hop IP)
- arp -a로 arp table 확인 가능

### GARP
- 라우터가 이중화되어있을 때 사용(뒤에 설명할 것임)
