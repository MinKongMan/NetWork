# 1-1장 HTTP 리퀘스트 메시지를 작성한다.


### Url 해독 방법
  - 브라우저가 처음 하는 일은 웹 서버에 리퀘스트의 메시지를 작성하기 위해 URL을 해독하는 것<br/>
  > ex1) http://www.lab.cyber.co.kr/dir1/file1.html을 분해<br/>
  > > http:   //   www.lab.cyber.co.kr(웹 서버명)   dir1/file1.html(데이터 출처의 경로명)<br/>
  > > www.lab.cyber.co.kr이라는 웹 서버에 /dir1/file1.html 이라는 경로의 파일<br/>즉 /dir1/ 디렉토리 아래에 있는 file1.html 파일에 액세스한다는 의미

  <br/>
  
  > ex2) http://www.lab.cyber.co.kr/dir/ (파일명을 생략한 경우)<br/>
  > > 위와 같은 경우 미리 서버측에 액세스할 파일명을 설정해 둠.

  <br/>
  
  > ex3) http://www.lab.cyber.co.kr/whatisthis<br/>
  > > 이 경우 끝에 /가 없으므로 whatisthis를 파일명으로 보는 게 맞을 것 같다.<br/>
  > > 그래서 일반적으로 whatisthis라는 파일이 있으면 파일에 접근하고, whatisthis라는 디렉토리가 있으면 디렉토리에 접근한다.<br/>
  > > 이때 파일명과 디렉토리 이름이 같을 수 없음(같은 이름의 파일과 디렉토리를 만들 수 없음)

  <br/><br/>

### 리퀘스트, 응답 메시지 기본 개념
  - HTTP 프로토콜 : 클라이언트와 서버가 주고받는 메시지의 내용이나 순서를 정한 것
  > 1. 먼저 클라이언트에서 서버를 향해 리퀘스트를 보냄.<br/>
  > > 이때 리퀘스트 메시지 내부에 무엇을(URI) 어떻게 해서(METHOD) 하겠다는 내용이 있다.  <br/>
  > > 보통 페이지 데이터를 저장한 파일의 이름이나 CGI 프로그램의 파일명을 URI로 사용 <br/>
  > > ```
  > > CGI 프로그램이란?
  > > 웹 서버 소프트웨어에서 프로그램을 호출할 때의 규칙을 정한것이 CGI이고
  > > CGI의 규칙에 맞게 움직이는 프로그램을 CGI 프로그램이라고 한다.
  > > ```
     
  > 2. 리퀘스트 메시지 구조<br/>
  > > 리퀘스트 라인(첫 번째 행) 구조<br/>
  > > <메소드> / <'URI'> / <HTTP 버전><br/><br/>
  > > 메시지 헤더<br/>
  > > <필드명>:<필드값> --> 한 행에 한 개의 헤더 필드를 쓴다. 공백 행까지 메시지 헤더가 됨<br/><br/>
  > > 메시지 본문<br/>
  > > <메시지 본문> 클라이언트에서 서버에 송신하는 데이터.<br/>
  > > 폼 페이지에 입력한 데이터를 POST 메소드로 웹 서버에 보낼 때 등의 데이터가 들어감<br/><br/>

  > 3. 응답 메시지<br/>
  > > 리퀘스트 메시지를 보내면 서버에서 응답 메시지가 돌아온다.<br/>
  > > 응답의 경우 리퀘스트의 실행 결과를 나타내는 스테이터스 코드와 응답 문구를 첫 번째 행에 써야함.<br/>
  > > 1xx : 처리의 경과 상황 등을 통지 <br/>
  > > 2xx : 정상 종료 <br/>
  > > 3xx : 무언가 다른 조치가 필요함을 나타냄 <br/>
  > > 4xx : 클라이언트 측의 오류<br/>
  > > 5xx : 서버측의 오류<br/><br/><br/>
 
 # 1-2장 웹 서버의 IP 주소를 DNS 서버에 조회한다.
 - 라우터 : 패킷을 중계하는 장치의 일종.
 - 서브넷 : 허브에 몇 대의 PC가 접속된 것

 ### TCP/IP의 기본이 되는 개념 설명<br/>

 > ex) XX동 XX 번지라는 형태로 네트워크의 주소를 할당<br/>
 > XX동에 해당하는 번호를 서브넷에 할당(네트워크 번호)<br/>
 > XX번지에 해당하는 번호를 컴퓨터에 할당한 것이 네트워크의 주소(호스트 번호)<br/>
 > 위 둘을 합쳐(네트워크 번호 + 호스트 번호) IP주소라 칭함.<br/>

 ### 프로세스 설명<br/>
 > 1. 송신측이 메시지를 보내면 서브넷 안에 있는 허브가 운반하고 송신측에서 가장 가까운 라우터까지 도착<br/>
 > 2. 라우터가 메시지를 보낸 상대를 확인하여 다음 라우터를 판단하고 그 라우터로 보내도록 지시하여 송신 동작을 실행한 후, <br/>
 >    다시 서브넷의 허브가 라우터까지 메시지를 보낸다
 > 3. 이런 동작을 반복하여 최종적으로 상대의 데이터가 도착하는 원리 -> TCP/IP와 IP주소의 기본적인 개념
 
 - 넷마스크 : 네트워크 번호와 호스트 번호의 경계를 나눠주는 역할
 ### 주소 표기 방법 <br/>
 > 1) IP 주소 본체의 표기 방법<br/>
 > > 10.11.12.13<br/>
 > 2) IP 주소 본체와 같은 방법으로 네트워크를 표기하는 방법<br/>
 > > 10.11.12.13/255.255.255.0<br/>
 > > IP 주소본체 / 넷마스크<br/>
 > 3) 네트워크 번호의 비트 수로 넷마스크를 표기하는 방법
 > > 10.11.12.13/24
 > > IP 주소본체 / 넷마스크
 > 4) 서브넷을 나타내는 주소
 > > 10.11.12.0/24
 > > 0-> 호스트번호 부분의 비트가 모두 0인 것은 각 컴퓨터가 아니라 서브넷 자체를 나타냄
 > 5) 서브넷의 브로드캐스트를 나타내는 주소
 > > 10.11.12.255/24
 > > 255-> 호스트 번호 부분의 비트가 모두 1인 것은 전체에 대한 브로드캐스트를 나타냄
 
 - DNS : 웹사이트의 IP주소와 도메인 주소를 연결시켜 주는 시스템
 - 리졸버 : 웹 브라우저와 같은 DNS 클라이언트의 요청을 네임 서버로 전달하고 </br>
           네임 서버로부터 정보(도메인 이름과 IP 주소)를 받아 클라이언트에게 제공하는 기능을 수행한다. 
 ### 리졸버를 활용하여 DNS 서버에 있는 IP주소 획득
 > 1) 리졸버가 DNS 서버에 조회 메시지를 보내고, DNS 서버에서 응답메시지가 돌아옴</br>
 > 2) 이 응답 메시지 속에 IP 주소가 포함되어 있으므로 리졸버는 이것을 추출하여 브라우저에서 지정한 메모리 영역에 넣음</br>
 > <메모리 영역> = gethostbyname(조회하는 서버의 도메인 명); --> 이 행만 실행하면 IP 주소를 조회하는 동작은 끝</br>
 > 브라우저가 웹 서버에 메시지를 보낼 때는 이 메모리 영역에서 IP주소를 추출하여 HTTP 리퀘스트 메시지와 함께 OS에 건네주어 송신을 의뢰함</br>
 
 - 제어가 넘어감 : 별도의 프로그램을 호출하여 호출처의 프로그램이 쉬고있는 상태가 되며, 호출한 대상 프로그램이 실행되기 시작하는 것
 - 프로토콜 스택 : OS 내부에 내장된 네트워크 제어용 소프트웨어
 ### 리졸버 내부의 작동
 > 1) 네트워크 애플리케이션(브라우저)에서 리졸버를 호출하면 제어가 리졸버의 내부로 넘어감</br>
 > 2) 리졸버 내부에서 DNS 서버에 문의하기 위한 메시지를 만듦 (브라우저가 웹 서버에 보내는 HTTP 리퀘스트와 유사)</br>
 > 3) 이때 메시지 송신 동작은 리졸버가 아닌 OS 내부의 프로토콜 스택을 호출하여 실행</br>
 >    (리졸버도 브라우저와 같이 송,수신하는 기능이 없기 때문)</br>
 > 4) 액세스 대상의 웹 서버가 DNS 서버에 등록되어 있으면 응답 메시지에 써서 클라이언트측에 반송(프로토콜 스택을 경유하며 리졸버에게 건네줌).</br>
 > 5) 리졸버는 내용을 해독한 후 IP 주소를 추출하여 애플리케이션에 IP주소를 건네줌</br>
 > 6) 앞서 언급한 <메모리 영역>에 IP 주소 저장(메모리 영역 = 메모리 영역을 나타내는 이름)</br>
 > ※ DNS 서버에 메시지를 송신할 때도 DNS의 IP주소가 필요하지만 컴퓨터에 미리 설정되어 있다.</br></br>

# 1-3장 전 세계의 DNS서버가 연대한다.

### DNS 서버의 기본 동작 : 클라이언트에서 조회 메시지를 받고 조회의 내용에 응답하는 형태로 정보를 회답
##### 조회 메시지에 포함된 정보
> 1) 이름 : 서버나 메일 배송 목적지(메일 주소에서 @뒷부분)와 같은 이름</br>
> 2) 클래스 : 인터넷 이외의 네트워크는 소멸되었으므로 항상 'IN'</br>
> 3) 타입 : 이 타입에 따라 클라이언트에 회답하는 정보의 내용이 달라짐 </br>
> ex) www.lab.cyber.co.kr인 서버의 IP주소를 조사할 때 클라이언트는 </br>
> 1) 이름 : www.lab.cyber.co.kr</br>
> 클래스 = IN</br>
> 타입 = A(address)의 정보를 포함하여 DNS서버에 조회 메시지를 보낸다.</br>
> 2) DNS 서버는 등록된 정보를 찾아서 이름, 클래스, 타입의 세 가지가 일치하는 것을 찾는다.</br>

### 도메인의 계층
##### 정보를 분산시켜 다수의 DNS서버에 등록하고, 다수의 DNS 서버가 연대하여 어디에 정보가 등록되어 있는지 찾는 구조.
> DNS 서버에 등록된 정보에는 모든 도메인명이라는 계층적 구조를 가진 이름이 붙여져 있다.</br>
> ex) www.lab.cyber.co.kr처럼 점으로 구분되어 있다. -> </br>
> kr라는 도메인(대한민국에 할당된 도메인)아래에 </br>
> co라는 도메인(국내의 도메인을 분류하기 위해 설치된 도메인)아래에 </br>
> cyber라는 도메인(회사에 할당된 도메인)이며, </br>
> www가 서버의 이름.

### 담당 DNS 서버를 찾아 IP 주소를 가져옴
##### 하위의 도메인을 담당하는 DNS 서버의 IP주소를 상위의 DNS 서버에 등록하는 방식
> ex) lab.glasscom.com이라는 도메인을 담당하는 DNS 서버를 </br>
> glasscom.com DNS 서버에 등록하고 glasscom.com의 DNS 서버를</br>
> com 도메인의 DNS서버에 등록하는 방식</br>
##### 루트 도메인의 DNS 서버를 인터넷에 존재하는 모든 DNS 서버에 전부 등록하는 방식


### DNS 서버는 캐시 기능으로 빠르게 회답할 수 있다.
##### DNS 서버는 한 번 조사한 이름을 캐시에 기록할 수 있는데, 조회한 이름에 해당하는 정보가 캐시에 있으면 그 정보를 회답한다.
##### 조회한 이름이 도메인에 등록되어 있지 않은 경우에는 이름이 존재하지 않는 회답이 돌아오고 이것을 캐시에 저장할 수도 있다.
> 주의할 점 : 캐시에 정보를 저장한 후 정보가 변경되었을 때 올바르지 않은 정보가 돌아올 수 있음.</br>
> 따라서 DNS 서버에 등록하는 정보에는 유효기간을 설정하고, 캐시에 저장한 데이터의 유효기간이 지나면 캐시에서 삭제해야 한다.
