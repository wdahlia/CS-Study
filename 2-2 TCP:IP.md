# TCP/IP 4계층 모델

[참고 자료](https://velog.io/@averycode/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-TCPUDP%EC%99%80-3-Way-Handshake4-Way-Handshake)

> TCP/IP 모형은 현재의 인터넷에서 컴퓨터들이 서로 정보를 주고받는데 쓰이는 통신규약(프로토콜)의 모음으로 **각 계층은 담당하는 위치마다 처리 역할을 구분해 진행**함으로 **서로 간의 간섭을 최소화**하여 사용의 편리성을 높힌다
>
> - 호환성 보장(다른 제조사 장비들끼리도 통신 가능)으로 인한 비용 절감
> - 쉬운 문제 해결(계층별로 문제 확인 가능)
> - 다른 계층끼리는 각 전달 과정을 알 필요없어 데이타의 캡슐화(헤더첨부)와 은닉이 가능

<br>

## OSI 7계층

- 네트워크 전송 시 **데이터표준을 정리**한 것 OSI 7계층

|     OSI 7계층     |
| :---------------: |
| 애플리케이션 계층 |
| 프레젠테이션 계층 |
|     세션 계층     |
|     전송 계층     |
|   네트워크 계층   |
| 데이터 링크 계층  |
|     물리 계층     |

## TCP/IP 4계층

- TCP/IP는 OSI 참조 모델을 기반으로 **상업적으로 실무적으로 이용**될 수 있도록 단순화된 모형

|             TCP/IP 4계층             |
| :----------------------------------: |
| 애플리케이션 계층  ***Application*** |
|      전송 계층 ***Transport***       |
|      인터넷 계층 ***Internet***      |
|    링크 계층 ***Network Access***    |

- **데이터 전송 시, 데이터는 상위 계층에서 하위 계층으로 이동하고, 계층 이동 마다 필요한 정보(헤더)가 추가됩니다.**
  - 이를, 캡슐화라고 합니다.
- **데이터 수신 시, 데이터는 하위 계층에서 상위 계층으로 이동하고, 계층 이동 마다 추가된 헤더를 읽고 알맞은 행동을 취한 후, 헤더를 제거합니다.**
  - 이를, 역캡슐화라고 합니다.

<br>

<p align="center"><img src="https://user-images.githubusercontent.com/108653518/204094378-40853bda-d95a-412d-abd1-768934497f72.png" alt="스크린샷 2022-11-24 오후 5 37 19"  /></p>

<br>

### 📂 애플리케이션(응용) 계층

- `데이터 단위` : Data/Message

- 응용 프로그램들이 데이터를 교환하기 위해 사용되는 프로토콜
  - 웹 서비스, 이메일 등 서비스를 **실질적으로** **사람들에게** **제공**하는 층

    <img width="1331" alt="image-20221124145257323" src="https://user-images.githubusercontent.com/108653518/204094380-0328ff94-21d1-4939-94c5-801fc7e6c475.png">
  
- `FTP` : 장치와 장치간의 파일을 전송하는 데 사용되는 표준 통신 프로토몰

- `SSH` : 보안되지 않은 네트워크에서 네트워크 서비스를 안전하게 운영하기 위한 암호화 네트워크 프로토콜

- `HTTP` : WWW를 위한 데이터 통신의 기초이자 웹 사이트를 이용하는데 쓰는 프로토콜

- `SMT ` : 전자 메일 전송을 위한 인터넷 표준 통신 프로토콜

- `DNS` : 도메인 이름과 IP 주소를 매핑해주는 서버

<br>

### 📂 전송 계층

- `데이터 단위` : Segment
  
  - 트랜스포트 계층의 패킷을 의미
  
  - 실질적인 데이터 전송을 위해 데이타를 일정 크기로 나눈 것. 발신, 수신, 포트주소, 오류검출코드가 붙게된다
  
    <img width="1172" alt="image-20221124152417464" src="https://user-images.githubusercontent.com/108653518/204094385-9402805b-9e7f-486f-8386-ca4b00d14591.png">

#### TCP

- 인터넷상에서 데이터를 메세지의 형태로 보내기 위해 IP와 함께 사용하는 프로토콜

- TCP는 애플리케이션에게 **신뢰적이고 연결지향성** 서비스를 제공한다. 일반적으로 TCP와 IP는 함께 사용되며 **IP는 배달을, TCP는 `패킷`의 추적 및 관리**를 하게 됩니다.

  TCP는 연결형 서비스로, 신뢰적인 전송을 보장하기에 hanshaking하고 데이터의 흐름제어와 혼잡제어를 수행합니다. 하지만 이러한 기능으로 인해 TCP의 속도는 느립니다.



- **TCP 특징**

  - 3-way handshaking과정을 통해 연결을 설정하고 4-way handshaking을 통해 해제한다.
  - 흐름 제어 및 혼잡 제어.
  - 높은 신뢰성을 보장한다.
  - UDP보다 속도가 느리다.
  - 전이중(Full-Duplex), 점대점(Point to Point) 방식.
  - 가상회선 패킷 교환 방식

  

  <img src="https://user-images.githubusercontent.com/108653518/204094358-f49a9b11-b892-4b08-86df-d2f8543b7af6.png" alt="스크린샷 2022-11-24 오후 3 45 23"  />

  <br>

  ![스크린샷 2022-11-24 오후 3 48 26](https://user-images.githubusercontent.com/108653518/204094366-eaeb59f2-17df-420c-9e40-5989b26e603c.png)

> **TCP의 3-Way Handshake**

- TCP 통신을 이용하여 데이터를 전송하기 위해 네트워크 **연결을 설정(Connection Establish)** 하는 과정
- 양쪽 모두 데이터를 전송할 준비가 되었다는 것을 보장하고, 실제로 데이터 전달이 시작하기 전에 한 쪽이 다른 쪽이 준비되었다는 것을 알 수 있도록 한다.
- 즉, TCP/IP 프로토콜을 이용해서 통신을 하는 응용 프로그램이 데이터를 전송하기 전에 먼저 정확한 전송을 보장하기 위해 상대방 컴퓨터와 사전에 세션을 수립하는 과정을 의미한다.

<br>

###### 작동방식

- **SYN 단계** 
  - 클라이언트는 서버에 클라이언트의 ISN을 담아 SYN을 보냅니다. ISN은 새로운 TCP 연결의 첫 번째 패킷에 할당된 임의의 시퀀스 번호를 의미 이는 장치마다 다를 수 있음

> **ISN** : 초기 네트워크 연결을 할 때 할당된 32비트 고유 시퀀스 번호
>
> **SYN** : 연결 요청 플래그
>
> **ACK** : 응답 플래그

- **SYN + ACK 단계**
  - 서버는 클라이언트의 SYN 수신 서버에 ISN을 보내며 승인번호로 클라이언트의 ISN + 1을 보냅니다

- **ACK단계**
  - 클라이언트는 서버의 ISN + 1 한 값인 승인번호를 담아 ACK를 서버에 보낸다



> **TCP의 4-Way Handshake**

- 4-Way Handshake은 **연결을 해제 (Connecntion Termination)**하는 과정

![스크린샷 2022-11-24 오후 4 05 20](https://user-images.githubusercontent.com/108653518/204094372-82195b9d-48b8-413e-8b04-9530334da9a8.png)

- 클라이언트가 연결을 닫으려고 할 대 FIN으로 설정된 세그먼트를 전송. 클라이언트가 FIN_WAIT_1 상태로 들어가고 서버의 응답 대기
- 서버는 클라이언트로 ACK라는 승인 세그먼트를 보내고 CLOSE_WAIT 상태에 들어감. 클라이언트가 세그먼트를 받으면 FIN_WAIT_2 상태에 들어갑니다
- 서버는 ACK 보내고 일정 시간 이후에 클라이언트에 FIN이라는 세그먼트를 보냄
- 클라이언트는 TIME_WAIT 상태가 되고 다시 서버로 ACK를 보내 서버가 CLOSED 상태가 됨 이후 클라이언트는 **어느 정도의 시간을 대기**한 후 연결 닫히고 클라이언트와 서버의 모든 자원의 연결이 해제



- `TIME_WAIT`
  - 지연 패킷이 발생할 경우를 대비하기 위함 패킷이 뒤늦게 도달하고 이를처리하지 못한다면 데이터 무결성 문제가 발생
  - 두 장치가 연결이 닫혔느지 확인하기 위함 LAST_ACK 상태에서 닫히게 되면 다시 새로운 연결을 하려고 할 때 장치는 줄곧 LAST_ACK로 되어 있기 때문에 접속 오류가 나타나게 됨



### 📂 인터넷 계층

- 장치로부터 받은 네트워크 패킷을 IP 주소로 지정된 목적지로 전송하기 위해 사용되는 계층\

- 패킷을 수신해야 할 상대의 주소를 지정하여 데이터 전달, 상대방이 제대로 받았는지에 대해 보장하지 않는 비연결형적인 특징을 가지고 있습니다

  <img width="1244" alt="image-20221124164532973" src="https://user-images.githubusercontent.com/108653518/204094388-0b5067fd-606b-4cf8-9c79-f904b073af4f.png">

### 📂 링크 계층

- 전선, 광섬유, 무선 등으로 실질적으로 데이터를 전달하며 장치 간에 신호를 주고받는 **규칙**을 정하는 계층
- 알맞은 하드웨어로 데이터가 전달되도록 MAC주소를 핸들링 하는것 뿐 아니라, 데이터 패킷을 전기신호로 변환하여 선로를 통하여 전달할 수 있게 준비해준다





- **만약, [www.google.com](http://www.google.com/) 을 웹 브라우저에 입력하면 무슨 일이 일어날까요?**

  - 구글 웹서버에 80번 포트로 HTTP Request 를 보낸다는 의미와 동일합니다.

- **우선, 구글 웹 서버에 HTTP Request 를 보내기 위해선, 아래와 같이 각 계층에 필요한 정보들을 담은 패킷을 만들어야합니다.**

  

  ![img](https://blog.kakaocdn.net/dn/b2guU0/btrEuyDK3ZU/KHXSRuiMz6FZdQCkCueO7k/img.png)

  

  - 해당 예제에선, 각 계층 별로 HTTP, TCP, IP, Ethernet 프로토콜을 사용한다고 가정해보겠습니다.

- **따라서, Application, Transport, Internet, Network Access Layer 순으로 어떤 데이터가 들어가는지 순서대로 살펴보겠습니다.**

- **먼저, 패킷의 Application Layer 에는 HTTP Request 헤더가 들어갑니다.**

  

  ![img](https://blog.kakaocdn.net/dn/bPHkQt/btrEtaqINu2/7XkMnAD3PlWHgt9eff7u8K/img.png)

  

  ```python
    :authority: www.google.com
    :method: GET
    :path: /
    :scheme: https
    ...
    ...
  ```

- **이후,Transport Layer 에는 TCP 헤더가 들어갑니다.**

  

  <img src="https://blog.kakaocdn.net/dn/9TMi5/btrEuQYqs4H/Fwykf6D8Kvn2BGqubkKHW0/img.png" alt="img" style="zoom:200%;" />

  

  - **TCP 헤더에서 중요하게 볼 것은 SP(출발지 포트번호)와 DP(목적지 포트번호)입니다.**
  - 출발지 포트번호는 내 컴퓨터에서 만든 소켓의 포트 번호이므로, 내 컴퓨터는 알고 있으며, 목적지 포트 번호 또한 80으로 알고 있습니다.

- **이후, Internet Layer 에는 IP 헤더가 들어갑니다.**

  

  ![img](https://blog.kakaocdn.net/dn/mikzS/btrEukFHTcw/Lrrpt2SW2YMEfDPdMycD81/img.png)

  

  - **IP 헤더에서 중요하게 볼 것은 SA(출발지 IP주소) 와 DA(목적지 IP주소)입니다.**
  - 현재, [www.google.com](http://www.google.com/) 이라는 도메인 정보만 알고 있기 때문에
  - 나의 시작 IP 주소는 알고 있지만, 목적지의 IP 주소는 아직 모릅니다.
  - 따라서, 도메인 정보로 목적지의 IP 주소를 알아내기 위해,
  - 도메인 서버에 DNS 쿼리를 보내고, IP 주소를 응답받습니다.

- **이후, Network Access Layer 에는 Ethernet 헤더가 들어갑니다.**

  

  ![img](https://blog.kakaocdn.net/dn/ok6Rj/btrEulxP4Fj/tpIqb2MAaIUkKrJkcMEAp0/img.png)

  

  - **Ethernet 헤더에서 중요하게 볼 것은 SA(출발지 MAC 주소)와 DA(목적지 MAC 주소)입니다.**
  - 여기서 목적지 MAC 주소는, 구글의 MAC 주소가 아닌,
  - 물리적으로 연결된, 패킷이 전달될 라우터(예를 들어, 공유기) 또는 게이트웨이의 MAC 주소를 의미합니다.
  - 따라서, 라우터의 MAC 주소를 알아내기 위해, ARP 프로토콜을 사용합니다.
    - ARP 프로토콜에 대한 개념은 아래 링크를 통해 배우실 수 있습니다.
    - https://wooono.tistory.com/110
  - 이제, ARP 프로토콜을 통해 라우터의 MAC 주소까지 알아냈습니다.

- **이후 패킷을 전송하기 전, TCP는 연결지향형 프로토콜이기 때문에, 송신측과 수신측이 서로 연결되는 작업이 필요합니다.**

  

  ![img](https://blog.kakaocdn.net/dn/wjaFl/btrEs9L8xiz/lXBFKF38oUIvfcD9WLCu40/img.png)

  

  - **이러한 작업을 3 Way Handshaking 이라고 부릅니다.**

  - 3 Way Handshaking 을 수행하기 위해서는, TCP 헤더에 표시한 플래그들이 사용되며, 이러한 플래그들을 컨트롤 비트라고 부릅니다.

  - 3 Way Handshaking 은 SYN(동기화) 과 ACK(승인) 로 진행됩니다.

    

    ![img](https://blog.kakaocdn.net/dn/dkm2mE/btrEuk6NQ54/GwMLyfFFiIqGnqGYRMwKSK/img.png)

    

  - 먼저, 클라이언트는 서버에게, 접속을 요청하는 SYN 패킷을 보냅니다.

  - 서버는 SYN 패킷을 받고, 클라이언트에게 요청을 수락한다는 ACK 와 SYN 플래그가 설정된 패킷을 보냅니다.

  - 클라이언트는 다시 서버에게 ACK 패킷을 보냅니다.

  - 이제 3 Way Handshaking 으로 기기 간 연결이 성립되었으니, 데이터 통신이 가능해집니다.

- **이제 라우팅을 통해 패킷을 목적지 서버에게 전송합니다.**

  

  ![img](https://blog.kakaocdn.net/dn/9Mzq7/btrEtNnV799/iLqHXDM0DgNMmOD8P7sAX1/img.png)

  

  - 패킷은 Network Access Layer의 MAC 주소와 Internet Layer의 IP 주소로 라우팅을 반복해 목적지 구글 서버까지 도착합니다.

  - 따라서, Transport Layer부터 설명을 진행하겠습니다.

  - 먼저, 구글 서버가 받은 패킷 내부 Transport Layer의 목적지 포트 번호에는 80번이 적혀져있습니다.

  - 따라서, Transport Layer는 80번 포트를 사용하고 있는 Application Layer에 데이터를 전송합니다.

  - 이후, Application Layer는 HTTP Request 데이터를 받아, “/” 에 매핑된 GET 요청을 처리합니다.

  - 이후, 적절한 HTML을 클라이언트에게 응답합니다.

  - 따라서, 클라이언트는 라우팅을 통해 전달 받은, “[www.google.com”](http://www.google.xn--com-9o0a/) 에 해당하는 HTML 을 브라우저에 띄우게 됩니다.

    

    ![img](https://blog.kakaocdn.net/dn/b4DlFT/btrEu7yRg0C/zvmnFLANv1VzlnjKolvkSK/img.png)

    

- **이제 HTTP 요청 및 응답 과정이 끝났으므로, 연결을 종료해야합니다.**

  

  ![img](https://blog.kakaocdn.net/dn/57S7q/btrEuVFi43G/TKUjuKieC59eAANkr9OpVk/img.png)

  

  - 여기서도 TCP의 컨트롤 비트가 사용되며, 해당 단계에서는 ACK, FIN 플래그가 사용됩니다.

    

    ![img](https://blog.kakaocdn.net/dn/bxu2b0/btrEuP6kSGs/RwYY6VoSE7316gdnnaPva0/img.png)

    

  - 클라이언트와 서버의 연결 종료 작업을 4 Way Handshaking 이라고 부르며, 총 4단계로 진행됩니다.

  - 먼저, 클라이언트는 서버에게, 연결을 종료하겠다는 의미인 FIN 패킷을 전송합니다.

  - 서버는 클라이언트에게 ACK 패킷을 보내고, 클라이언트가 보냈던 요청들에 대해 마저 응답을 보냅니다.

  - 이후, 서버의 응답이 끝나면 클라이언트에게 FIN 패킷을 전송합니다.

  - 클라이언트는 서버의 통신 종료를 확인한 뒤, 서버에게 ACK 패킷을 전송하고, 연결이 종료됩니다.

  - 하지만, 서버가 클라이언트에게 FIN 을 보내는 과정에서 한가지 문제가 발생할 수 있습니다.

    

    ![img](https://blog.kakaocdn.net/dn/RVn4D/btrEtNIdCdp/BsvT2C2k9UTjb9cKJl6odK/img.png)

    

  - 서버가 클라이언트에게 FIN 을 보내기 전에, 이전에 서버가 클라이언트에게 응답 했던 패킷이 FIN 보다 늦게 도착할 수도 있습니다.

  - 그렇게 되면, 클라이언트가 서버의 일부 응답을 받지 못하게 됩니다.

    

    ![img](https://blog.kakaocdn.net/dn/QzWbF/btrEt2FlsdT/5rqucJ2u0vTDbFpzVkFhWk/img.png)

    

  - 따라서, 클라이언트는 서버로부터 FIN 패킷을 받고, ACK 패킷을 보낸 뒤에도

  - 일정 시간동안 혹시나 아직 도착하지 않은 잉여 패킷을 기다립니다.

  - 이렇게, 4 Way handshaking 이후에도 소켓을 닫지 않고 잉여패킷을 기다리는 상태를, TIME_WAIT 이라고 합니다.
