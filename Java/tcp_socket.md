# TCP소켓 프로그래밍

### 소켓
프로세스간 통신에 사용되는 양쪽 끝단

<br/>

### Server - Client 통신과정
1. 서버 프로그램은 서버소켓을 사용해서 서버 컴퓨터의 특정 포트에서 클라이언트의 연결 요청을 처리할 준비를 한다.
2. 클라이언트 프로그램은 접속할 서버의 IP주소와 포트 정보를 가지고 소켓을 생성해서 서버에 연결을 요청한다.
3. 서버소켓은 클라이언트의 연결 요청을 받으면 서버에 새로운 소켓을 생성해서 클라이언트의 소켓과 연결되도록 한다.
4. 이제 클라이언트의 소켓과 새로 생성된 서버의 소켓을 서버소켓과 관계없이 일대일 통신을 한다.

<br/>

### 서버소켓의 역할
서버소켓은 포트를 통해 클라이언트의 연결 요청을 기다리다가 연결 요청이 올 때마다 새로운 소켓을 생성하여 클라이언트 소켓과 통신할 수 있도록 연결한다.

<br/>

### 소켓과 포트
여러 개의 소켓이 하나의 포트를 공유해서 사용할 수 있지만, 서버소켓은 포트를 독점한다. 왜냐하면 서버소켓이 여러개라면 클라이언트 프로그램은 어떤 서버소켓과 연결되어야하는지 알 수 없기 때문이다.

<br/>

### 소켓들이 데이터를 주고받는 연결통로 : 입출력스트림
소켓은 입력스트림과 출력스트림을 가지고 있으며, 한 소켓의 입력스트림은 상대편 소켓의 출력스트림과 연결되고, 출력스트림은 입력스트림과 연결된다.