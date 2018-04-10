# Layer
| TCP/IP Model         | OSI Mode           |
|----------------------|--------------------|
| Application Layer    | Application Layer  |
|                      | Presentation Layer |
|                      | Session Layer      |
| Transport Layer      | Transport Layer    |
| Internet Layer       | Network Layer      |
| Network Access Layer | Data Link Layer    |
|                      | Physical Layer     |


reliable sequenced
reliable fragmented
unreliable sequenced

RTO(Retransmition TimeOut)
새로운 평균RTT = 현재평균RTT * 0.875 + 마지막 RTT * 0.125
새로운 RTT편차 평균 = 현재RTT편차평균 * 0.875 + 마지막 RTT의 편차 * 0.125
RTO = 평균RTT + (4 * RTT편차평균)


UDP
집WIFI=>밖의4g이용시
https://www.youtube.com/watch?v=qotJiFii0hU
https://www.youtube.com/watch?v=UsSRNgIXmW8

로그인서버N - 로비서버N - 게임서버N
스트레스테스트
통계






* 전달 미보장 데이터 : 그다지 중요하지 않은 데이터
* 전달 보장 데이터 : 수신/순서 보장 - 매우 중요한 데이터
* 최신 상태 데이터 : 최신 상태만 중요한것(hp 현재상태 등)
* 특급 전달 보장 데이터 : 최우선으로 보내야 하는것 / 전달 보장

Multiplayer Game Programming: Architecting Networked Games


# [platform packet module]
신뢰성 계층 직접 구현.
ghost / move / event manager


# [connection manager]
DNS(delivery status notification)을 보장.
수신측의 ACKnowledge에 따라 비트 필드를 이용한 sliding window 기법으로 구현.

# [stream manager]
전송 대역폭 관리

#[ghost / move / event manager]
## event manager
## ghost manager
## move manager

이동은 30fps가 적당할까?

Turn timer - 일정 기간마다 명령을 쌓아 둔다.(엠파이어인 경우 200ms)
수신측은 2턴 이후, 즉 200 + 2 * 200 ms의 지연이 생김.
200ms를 따라가지 못하면?
* 올스톱을 하거나
* 렌더링 프레임레이트를 동적으로 조절

# PRNG(Pseudo-random number generator)
난수발생기 호출 순서 횟수를 어떻게 보장할까?

7계층 – 응용 계층(Application): 디핑 소스 비유를 확장하면 응용 계층은 가장 위에 있다. 사용자에게 보이는 부분이다. OSI 모형에서는 “최종 사용자에게 가장 가까운” 계층이다. 7층에서 작동하는 응용프로그램은 사용자와 직접적으로 상호작용한다. 구글 크롬(Google Chrome), 파이어폭스(Firefox), 사파리(Safari) 등 웹 브라우저와 스카이프(Skype), 아웃룩(Outlook), 오피스(Office) 등의 응용 프로그램이 대표적이다.

6계층 – 표현 계층(Presentation): 표현 계층은 응용 계층의 데이터 표현에서 독립적인 부분을 나타낸다. 일반적으로 응용프로그램 형식을 준비 또는 네트워크 형식으로 변환하거나 네트워크 형식을 응용프로그램 형식으로 변환하는 것을 나타낸다. 다시 말해 이 계층은 응용프로그램이나 네트워크를 위해 데이터를 “표현”하는 것이다. 대표적인 예로는 데이터를 안전하게 전송하기 위해 암호화, 복호화하는 것인데, 이 작업이 바로 6계층에서 처리된다.

5계층 – 세션 계층(Session): 2대의 기기, 컴퓨터 또는 서버 간에 “대화”가 필요하면 세션(session)을 만들어야 하는데 이 작업이 여기서 처리된다. 이 계층에는 설정, 조율(예: 시스템의 응답 대기 기간), 세션 마지막에 응용프로그램 간의 종료 등의 기능이 필요하다.

Segment 4계층 – 전송 계층(Transport): 전송 계층은 최종 시스템 및 호스트 간의 데이터 전송 조율을 담당한다. 보낼 데이터의 용량과 속도, 목적지 등을 처리한다. 전송 계층의 예 중에서 가장 잘 알려진 것이 전송 제어 프로토콜(TCP)이다. TCP는 인터넷 프로토콜(IP) 위에 구축되는데 흔히 TCP/IP로 알려져 있다. 기기의 IP 주소가 여기서 작동한다.

Packet 3계층 – 네트워크 계층(Network): 네트워킹 전문가 대부분이 관심을 두고 좋아하는 라우터 기능 대부분이 여기 네트워크 계층에 자리잡는다. 가장 기본적으로 볼 때 이 계층은 다른 여러 라우터를 통한 라우팅을 비롯한 패킷 전달을 담당한다. 보스턴에 있는 컴퓨터가 캘리포니아에 있는 서버에 연결하려고 할 때 그 경로는 수백 만 가지다. 이 계층의 라우터가 이 작업을 효율적으로 처리한다.

Frame 2계층 – 데이터 링크 계층(Data Link): 데이터 링크 계층은 (두 개의 직접 연결된 노드 사이의) 노드 간 데이터 전송을 제공하며 물리 계층의 오류 수정도 처리한다. 여기에는 2개의 부계층도 존재한다. 하나는 매체 접근 제어(MAC) 계층이고 다른 하나는 논리적 연결 제어(LLC) 계층이다. 네트워킹 세계에서 대부분 스위치는 2계층에서 작동한다.

Bit 1계층 – 물리 계층(Physical): OSI 디핑 소스의 밑바닥에는 물리 계층이 있다. 시스템의 전기적, 물리적 표현을 나타낸다. 케이블 종류, (802.11 무선 시스템에서와 같은) 무선 주파수 링크는 물론 핀 배치, 전압, 물리 요건 등이 포함된다. 네트워킹 문제가 발생하면 많은 네트워크 전문가가 물리 계층으로 바로 가서 모든 케이블이 제대로 연결돼 있는지, 라우터나 스위치 또는 컴퓨터에서 전원 플러그가 빠지지 않았는지 확인한다.



# physical layer


# link layer - 전자기학을 벗어나 컴퓨터학이 본격적으로 적용되기 시각.
 • 특정 목적지에 주소를 부여해서 각 프레임에 기재토록 하여 호스트를 식별할 수단 제공
 • 수신 측 주소와 데이터를 담을 수 있는 프레임 포맷 정의
 • 한 번에 데이터를 얼마까지 보낼 수 있는지 윗단 계층에서 알 수 있게끔 프레임의 최대 길이를 정의
 • 물리 계층을 거쳐 전달된 신호를 의도된 호스트가 수신할 수 있게 `Frame`을 물리적인 전기 신호로 변환하는 방법을 정의

## 이더넷 프로토콜(Ethernet) / 802.3
NIC(network interface controller) - MAC address(Media Access Control address) - 48 bit
하드웨어 식별자 - UUID(universally unique identifier)
24 - OUI(Organizationally unique identifier) : 제조사 고유번호
24 - 제조업체 고유번호.

프리어셈블 | SFD
목적지 MAC | 길이/종류
발신지 MAC | 길이/종류
페이로드 (46 ~ 1500 bytes)
프레임 체크 시퀀스(frame check sequence, FCS) - CRC32 값.

MTU(maximum transmission unit)
0x0600 = 1536
1536 이하는 길이. 이상이면 프로토콜의 종류

16진법
55 55 55 55 55 55 55 D5 : preamble | SFD(start frame delimiter)



# network layer
네트워크 계층이 없다면, 인터넷을 보다 작은 네트워크 망으로 나눌 수 없다.

이더넷 : 각 프레임을 네트워크상 모든 호스트에 전달하고, 전송자가 애초 의도한 수신자가 바로 자신이지 여부는 호스트 스스로 판단.
네트워크 계층이 없으면, 프레임하나 보낼때마다 지구상 연결된 모든 호스트로 전달해야 할 것임(모든 컴퓨터가 단일망)

서로 상의한 네트워크 사이에서 용도에 가장 알맞은 최적의 구현을 각자 선택하자=> 여러 종류의 물리계층, 링크계층.
서로 다른 링크 프로토콜이 서로 통신 할 방법을 규정하는것은 네트워크 계층.

" 네트워크 계층의 역할은 링크 계층 위에 논리 주소 체계 인프라를 구축하는 것  "
(주소 걱정 없이 쉽게 호스트 하드웨어를 교체, subnetwork로 격리 하거나, 멀리 떨어진 서브네트워크 사이에 링크 계층 프로토콜이나 물리적 매체가 각기 다르더라도 서로 통신 할 수 있다)


IPv4 - 직접/간접 라우팅 시스템 및 패킷 분열 기능(링크 계층에 보낼 큰 패킷을 쪼개는) 등을 제공
IPv6 주소 공간 제약 문제 해결, IPv4의 여러가지 큰 병목을 제거

IP 주소는 네트워크 계층에서 사용 - 링크 계층은 IP주소에 대응하는 MAC 주소로 변환하는 방법을 알고 있어야 함 => 링크계층 ARP(Address Resolution Protocol)

18.19.100.1 | 255.255.255.0 (11111111 11111111 1111111 00000000) | 18.19.100.0 / 24 (CIDR classless inter-domain routing)


네트워크 계층은 packet단위(IPv4 - 65,535 bytes) - 이더넷 frame단위(1,5000 bytes)
packet을 frame으로 분열하는것을 fragmentation이라 한다. 이 분열을 합치는 것을 도와주기 위해 추가 필드 필요.


패킷 크기는 1500에 가깝게 맞추는게 좋다
why : 이더넷 frame단위에 가깝다.  단위가 적으면 자주 보내야 하며, 단위가 크면 분열이 일어나기 때문이다.

why IPv6
IPv4 - 32bit - 42억개 고유ip
IPv6 - 128 bit
ARP에서 하던 역활을 IPv6의 NDP(neighbor discovery protocol)이 대체.
라우터 레벨에서 패킷 분열을 지원하지 않음(분열 관련 필드를 IP헤더에서 제거, 대역폭 절약 가능)
* 기존헤더에 분열 정보를 기록하지 않고, 분열확장헤더를 이용해 단편화를 함.
* 출발지에서만 분열 수행

IPv4 - MTU(Maximum Transmission Unit) - 최소 576bytes
IPv6 - 최소 또는 기본 1280 bytes



# transfer layer

process <binding> port

포트(16 bit) 라는 개념을 통해 원격 호스트 프로세스 사이의 종단 간 통신을 지원
0 ~ 1023 - system port, reserved port
1024 ~ 49151 : user port, registered port
49152 ~ 65535 : dynamic port

TCP(transmission control protocol) - 6
UDP(user datagram protocol) - 17
DCCP(datagram congestion control protocol) - 33
SCTP(stream control transmission protocol) - 132


TCP (Transmission Control Protocol)
Ack(Acknowledgment) | Timeout | Resend

sliding window
cumulative ACK
selective ACK

1986/10 -router problem - Van Jacobson - TCP Tahoe
Nagle algorithm

#### 왜 TCP가 느린가
데이터를 보내고 다음 데이터를 보내기 까지 ACK를 기다림
상태초기화 시간 - 3way hand shake
네이글(Nagles’ algorithm) 세그먼트 보내기 전에 데이터를 쌓아둠
* 게임에선 혼잡제어(flow control)을 꺼버림


UDP


# application layer
DHCP / DNS

NAT(Network Address Translation) - 네트워크 주소 변환.
공인 IP주소 하나를 네트워크 전체가 공유하여 쓸 수 있게 해 준다.
미리 약속되지 않은 외부 연결 접속을 허용하지 않음
 (서버 구동시 외부 연결 접속 허용 필수. STUN이나 TCP 홀 펀칭 같은 기법을 이용 우회하기도 한다)

STUN(Simple traversal of UDP though NAT)
* udp

TCP hole punching
IGDP(Internet gateway device protocol)
* 항상 지원하는것도 아니고, 학술 가치도 적음
