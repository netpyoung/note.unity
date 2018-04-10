UdpClient // server & client
UdpClient.JoinMulticast()


SocketOptionLevel.Udp
ChecksumCoverage Boolean 0, 1 Get/set UDP checksum coverage.
NoChecksum Boolean 0, 1 UDP datagrams sent with checksum set to
zero.


Broadcast
255.255.255.255
서브네트워크 내의 모든 컴퓨터에 데이타를 전달하는 기능으로 일반적으로 한 라우터 내에서만 사용된다


Multicast
* 224.0.0.0 ~ 239.255.255.255
* 224.0.0.0 ~ 224.0.0.255
  - 까지가 라우팅 프로토콜과 네트워크 트래픽 제어용으로 사용되어 이미 예약되어 있기
* 224.0.1.0 ~ 239.255.255.255
