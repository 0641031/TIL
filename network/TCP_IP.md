### TCP / IP

인터넷을 포함하여 일반적으로 사용하고있는 네트워크는 TCP/IP라는 프로토콜에서 움직인다. TCP/IP는 다양한 프로토콜의 집합. 

1. Application Layer : 유저에게 제공되는 애플리케이션에서 사용하는 통신의 움직임을 결정. ex) FTP, DNS, HTTP

2. Transport Layer : 애플리케이션 계층에 네트워크로 접속되어있는 2대의 컴퓨터 사이의 데이터 흐름을 제공. ex) TCP(Transmission Control Protocol), UDP(User Data Protocol)

3. Network Layer : 네트워크 상에서 패킷(전송하는 데이터의 최소단위)의 이동을 다룸. 어떠한 경로로 데이터를 전송할 지 결정.

4. Link Layer(Data Link Layer) : 네트워크에 접속하는 하드웨어적인 면을 다룸. 각 계층을 거칠 때는 반드시 해당 계층에 필요한 정보를 담고있는 헤더가 추가되고, 수신측에서는 사용한 헤더를 삭제함 → 캡슐화


#### 배송을 담당하는 IP (Internet Protocol)

* IP주소와는 다름. 프로토콜의 명칭.
* 역할 : 개개의 패킷을 상대방에게 전달.
* 여러요소가 필요하지만 그 중에서도 IP주소, MAC주소가 중요.
* IP 주소 : 각 노드에 부여된 주소. (변경가능)
* MAC(Media Access Control Address) 주소 : 데이터 링크 계층에서 통신을 위한 네트워크 인터페이스에 할당된 고유식별자. (변경불가)
* IP통신은 MAC주소에 의해서 통신. 여러대의 컴퓨터와 네트워크 기기를 중계해서 상대방에게 도착. 중계하는 동안 다음의 MAC주소를 사용하여 목적지를 찾음. 이때 ARP(Address Resolution Protocol)가 사용됨.
* ARP : 수신지의 IP주소를 바탕으로 MAC주소 조사.
* 송신측의 전달과정 전체를 알고있지 않음. 그저 다음 목적지만 알고 있음.


#### 신뢰성을 담당하는 TCP(Transfer Control Protocol)

* 신뢰성있는 바이트스트림 서비스제공
* 바이트스트림 서비스 : 용량이 큰 데이터를 보내기 쉽게 TCP세그먼트라는 단위 패킷으로 분해하여 관리. → 대용량의 데이터를 보내기 쉽게 작게 분해하여 상대방에게 보내고, 정확하게 도착했는지 확인.
* 확실하게 데이터를 보내기 위해 'three way handshaking' 방법을 사용함 : 패킷을 보낸 후, 'SYN', 'ACK'라는 TCP 플래그를 사용하여 보내졌는지 상대방에게 확인하러 감. 
<sub>SYN : synchronize sequence numbers, ACK : acknowledgment</sub>


#### 이름해결을 담당하는 DNS(Domain Name Service)

* 응용계층 시스템에서 도메인 이름과 IP주소 이름 확인. 도메인명에서 IP주소를 조사하거나, 반대로 IP주소로부터 도메인명을 조사하는 서비스를 제공.


###### reference
* 우에노 센, 「그림으로 배우는 HTTP & Network Basic」, 이병억 옮김, 영진닷컴(2015)
