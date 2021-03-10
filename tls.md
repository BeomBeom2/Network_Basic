## 📌 TLS(Transport Layer Security) 프로토콜

### 1. TLS 구조

![](https://media.vlpt.us/images/saseungmin/post/1ecb3aaa-16ad-4a59-a6bb-5f4384353122/500px-TLS_protocol_stack.PNG)

-   TLS는 단일 프로토콜이 아니고  **2계층에 걸친 프로토콜이다.**
-   **Record 프로토콜**은 운반자이며, 응용 계층으로부터 오는 데이터뿐만 아니라 TLS의 상위 프로토콜로부터 오는 메시지를 전송한다. Record 프로토콜에서 오는 메시지는 보통 TCP인 전송 계층의 페이로드이다.
-   **Handshake 프로토콜**은 Record 프로토콜에 대한 보안 매개변수를 제공한다.
 -   암호 집합을 설정하고 키와 보안 매개변수를 제공한다
-   또한, 필요하다면 클라이언트가 서버에 대해 그리고 서버가 클라이언트에 대해 인증된다.
-   **ChangeCipherSpec 프로토콜**은 암호학적 비밀을 신속하게 보내는 데 사용된다.
-   **Alert 프로토콜**은 비정상 조건을 알리는데 사용된다.
-   **Heartbeat 프로토콜**은 프로토콜 객체의 가용성을 모니터링 할 때 사용된다.


![](https://media.vlpt.us/images/saseungmin/post/1e475cb7-9f58-4c09-884f-accb3abe9c14/TLS-handshake-protocol.png)


### 1.Hello Request

- 서버가 아무 때나 보낼 수 있는 메시지, 클라이언트에게 Client Hello 메시지를 보내어 협상을 요구하는 메시지이다. 현재 협상이 진행 중이면 클리이언트는 이 메시지를 무시한다.
- 서버는 HelloRequest를 보내고 이에 대한 Hanshake가 끝나지 않은 상태에서 또 다시 HelloRequest를 보내면 안된다.

### 2. ClientHello

 - 클라이언트는 서버에 처음으로 연결을 시작하거나 HelloRequst 메시지에 대한 응답으로 ClientHello 메시지를 보낸다.
 - ClientHello 메시지는 세션 식별자, CipherSuite 리스트, 클라이언트가 지원하는 압축 알고리즘 리스트, SSL 버전, 난수를 서버에 전달한다.
	 - cipher_suites : CipherSuite 리스트는 키 교환 알고리즘, 암호 알고리즘, MAC 알고리즘을 포함한다.
	 - 형식은 SSL/TLS-(A)-WITH-(B) : A는 키 교환 및 인증 알고리즘, B는 cipher spec(암호 명세)는 대칭 암호 알고리즘, 암호키 길이, 블럭 암호 모드, HMAC용 해시 알고리즘 등으로 구성된다.
	 - ex) (B) = TLS-RSA-WITH-AES-256-CBC-SHA256 : AEC를 사용하며 암호키 길이는 256비트, 블록 암호 모드는 CBC이고, HMAC용 해시 알고리즘은 SHA-256을 사용하는 cipher suite

### 3.ServerHello

 - 서버는 ClientHello 메시지에 대한 응답으로 ServerHello 메시지를 보낸다. 실패 할 경우에는 HandsShake Failure Alert 메시지를 띄운다.
 - ServerHello 메시지는 세션 식별자, 선택한 CipherSUite, 선택한 압축방법, 서버 SSL 버전, 서버가 생성한 난수를 클라이언트에 전달한다.


## 🔶 1 단계 : 보안 기능 확립 후
 
  - SSL 버전
  - 키 교환, 메시지 인증과 암호화를 위한 알고리즘
  - 압축 방법
  - 키 생성을 위한 2개의 난수

### 4. Server Certificate 

 - 서버의 인증이 필요한 경우에 서버는 ServerHello 뒤에 서버의 인증서가 포함된 Certificate을 보내야 한다.
 - 이 때 서버의 인증서는 선택된 cipher suite의 키 교환 알고리즘에 맞는 타입이어야 한다.

### 5. Server Key Exchange

 - 서버의 인증서를 보내지 않았거나 보낸 인증서에 키 교환에 필요한 정보가 부족하면 전송되는 메시지.

### 6. Ceritificate Request 
 - 서버는 자신을 클라이언트에게 인증함과 동시에 클라이언트에게 클라이언트의 인증서를 통한 인증을 요구할 수 있다.
 - 이 메시지는 선택적으로 사용되고 사용할 시엔 서버와 클라이언트의 상호 인증이 이루어진다.

### 7. ServerHelloDone
 - 서버가 보낼 메시지를 다 보냈음을 알려주는 메시지.

## 🔶 2 단계 : 서버 인증과 키 교환 후에 서버는 클라이언트에 대해 인증되고 클라이언트는 필요하다면 서버의 공개키를 알 수 있다.

### 8. Client Certificate 
 - (6)에 대한 응답 : 서버가 클라이언트의 인증을 요구할 경우 클라리언트가 보내는 메시지 
 
### 9. Client Key Exchange
 - 클라이언트는 세션키를 생성하기 위해 임의의 비밀 정보인 48바이트 pre-master-secret을 생성한다.
 - 그 후 선택된 알고리즘(RSA, Fortezza, Diffi-Helllman 중 하나)을 이용하여 pre-master-secret을 서버와 공유

### 10. Ceritificate Verify
 - 클라이언트 인증서의 명백한 확인을 위해 클라이언트는 핸드 쉐이크 메시지를 전자 서명하여 전송한다.

## 🔶 3 단계 : 클라이언트 인증과 키 교환 후에 클라이언트는 서버에 대해 인증되고 클라이언트와 서버 양측은 사전 마스터 비밀을 알게 된다.

### 11. ChangeCipherSpec, Finished 
 
 - ChangeCiphterSpec 메시지는 핸드 쉐이크 프로토콜에 포함되는 것은 아니고, 이 메시지 이후에 전송되는 메시지는 새롭게 협상 된 알고리즘과 키를 이용할 것임을 나타낸다.
 - Finished 메시지는 ChangeCipherSpec 메시지 이후에 전송되며, 협상 된 알고리즘과 키가 처음으로 적용되고 상대편에서 이 메시지를 통해서 협상한 결과를 확인하게 된다.
 - 이후 애플리케이션 데이터가 전송된다.

## 🔶 4 단계 : 종료 단계 이후 클라이언트와 서버는 데이터를 교환할 준비가 된다.


### reference [SSL/TLS](https://velog.io/@saseungmin/SSLTLS-%EB%B3%B4%EC%95%88)
