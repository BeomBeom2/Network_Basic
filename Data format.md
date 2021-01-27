## XML(eXtensible Markup Language)
마크업 언어를 정의하기 위한 언어, 확장이 가능한 언어이다.

```마크업 언어는``` **태그 등을 이용해 문서나 데이터의 구조를 명기하는 언어의 한 가지**```이다.일반적으로 데이터를 기술하는 정도로만 사용되기에 프로그래밍 언어와는 구별된다. MXML이나 XAML처럼 특정 프로그래밍 언어와 강하게 연관되 가능하거나 제한적으로 프로그래밍 언어의 기능을 갖춘 것도 일부 있는데, 이런 경우엔 구별이 명확하지 않다.```

### HTML과의 비교

HTML과 흡사한 markup language이지만 Tag를 정의할 수 있고 데이터를 기술 할 수 있는 마크업 언어. 그렇기 때문에 XML은 데이터가 무엇인지에 초점을 맞춰 데이터를 기술하기 위해 고안되었고 HTML은 데이터가 어떻게 보일지에 초점을 맞춰 데이터를 표시하기 위해 고안되었다. 때문에 **XML은 데이터를 구조화시키는데 사용**되고 **HTML은 동일한 데이터를 표시하고 꾸미는데 사용**된다.

```xml
<?xml version="1.1" encoding="UTF-8"?>
<root>
	<apiVersion>v1</apiVersion>
	<kind>Pod</kind>
	<metadata>
	  <name>hello-pod</name>
	  <labels>
	    <app>hello</app>
	  </labels>
	</metadata>
	<spec>
	  <containers>
	    <name>hello-container</name>
	    <image>tmkube/hello</image>
	    <ports>
	      <containerPort>8000</containerPort>
	     </port>
	   </containers>
	 </spec>
</root>
```
이렇게 태그형식을 통해 Key와 Value를 구분하고, 태그안에 태그를 넣어 부모와 자식관계의 구조를 나타낸다. 

## YAML

XML, C, 파이썬 등에서 정의된 e-mail 양식에서 개념을 얻어 만들어진 '사람이 쉽게 읽을 수 있는' **데이터 직렬화 양식**이다. 
 오늘날 XML과 JSON "JSON")이 데이터 직렬화에 주로 쓰이기 시작하면서, 많은 사람들이 YAML을 '가벼운 마크업 언어'로 사용하려 하고 있다.
 
```초기에는 “또 다른 마크업 언어 (Yet Another Markup Language)”였으나, YAML의 핵심은 문서 마크업이 아닌 데이터 중심에 있다는 것을 보여주기 위해 YAML(YAML Ain’t Markup Language)이란 이름으로 바꾸었다.```

```Serialization(직렬화)은 데이터를 시스템 외부(파일로 쓰거나 네트워크로 전송하거나)에서 사용할 때 사용한다.(Byte Array, JSON, YAML)```

### YAML vs. JSON

**JSON의 최우선 설계 목표는 간편성과 보편성**이다. 따라서 JSON이 가독성이 떨어지나,생성 및 파싱이 용이하다.  
반면에 **YAML의 최우선 설계 목표는 가독성과 데이터 구조 Serialization**이다. 따라서 YAML은 사람이 읽기 쉬운 반면에 생성 및 파싱이 JSON 보다 복잡하다. 
 YAML을 JSON의 Superset으로 볼 수도 있다.  
모든 JSON 파일은 유효한 YAML 파일이다.  
따라서 JSON에서 YAML로 마이그레이션 하기가 용이하다.

[YAML | 오늘도 끄적끄적 (perfectacle.github.io)](https://perfectacle.github.io/2018/08/19/yaml/)
[JSON to YAML](https://www.json2yaml.com/)

```마이그레이션 : 데이터를 한 저장 장치에서 다른 저장 장치로 옮기는 과정```

youtube에 update server setup - wsus만 나옴(Window Server Update Server) X
google에 update server build - X
google에 update check flow X
google에 program version checking X
google에 version update server X 
google에 program update server X
google에 프로그램 업데이트 서버 O
google에 C++ mfc 프로그램 소스 분석

[게임에서 패치시스템을 보통 어떻게 구현하나요?](http://1st.gamecodi.com/board/zboard.php?id=GAMECODILAB_QnA_etc&page=4&sn1=&divpage=1&sn=off&ss=on&sc=on&select_arrange=hit&desc=asc&no=2659)
[자동 업데이트, 패치 프로그램 및 툴 (clebus.co.kr)](http://www.clebus.co.kr/clebus/zoom_print.php?id=store&no=3672)
[업데이트 서버요. - GpgStudy 포럼](https://www.gpgstudy.com/forum/viewtopic.php?t=21223)

## 프로토콜

**공통의 데이터 교환 방법 및 순서에 대해 정의한 의사소통** 약속, 규약 혹은 규칙 체계를 말한다. (언어 X, 대화방법 O)
프로토콜은 통신을 위한 물리적, 소프트웨어적 등 여러 조건을 취하여 결정한다. 예를 들어 통신 데이터의 포맷이나 전송 문자 등은 통신을 행하는 두 사람 사이에 사전에 결정해두지 않으면 안 된다. 동일한 통신망에 연결되어 있다고 하더라도 같은 프로토콜을 이용하는 커퓨터들 사이에만 통신할 수 있다. 
&nbsp;서로 프로토콜이 같으면 통신이 가능하지만 일반적으로 다른 컴퓨터 기종간에는 Protocol도 다르기 때문에, 다른 기종 간 정보통신을 하려면 표준 프로토콜을 설정하여 각각 이를채택하여 통신망을 구축해야 한다. 
#### 모든 프로토콜은 크게 세 가지 구성 요소인 구문, 의미, 타이밍으로 이루어져 있다.

 - **구문 = 송수신 데이터 포맷**
 - **의미 = 데이터의 각 항목이 가지는 의미**
 - **타이밍 = 데이터 송수신 동작방식의 정의**

약속인 프로토콜은 통신 기능의 확장과 새로운 통신기술, 방식 도입을 쉽게 하기 위해 적절한 기능 단위로 프로토콜 층이라 불리는 계층으로 분할되어 있다.
프로토콜의 계층 구성은 아키텍처에 따라 다소 다르지만 기본적으로 **데이터 전송제어에 관한 계층**```(물리적/전기적 인터페이스, 노드간 데이터 전송 등을 규정)```과 **통신처리에 관한 계층**```(메시지 전송, 파일 전송 가상 단말기능 등을 규정)```**으로 구분**하고 있다.
예전에는 프로토콜에 대해 각 메이커 마다 독자적인 체계를 만들었기 때문에 국제적으로 프로토콜의 표준화가 시도되었으며 ISO에서 개방형 시스템간 상호접속(OSI)에 관하여 7계층으로 나눈 프로토콜을 검토 했다.

프로토콜이 희미하고 추상적으로 느껴질 것 수 있다. 어떤 정보를 보내는데 IP주소만 알면되는 것 아닌가? 하는 생각이 들 수 있기 때문이다. 
원격지의 상대방에게 정보를 전송하기 위해서 데이터의 전기적인 신호로의 변환 및 통신망으로의 전달이 필요하고 전달된 전기적 신호는 다시 원래 정보로 돌아오도록 만드는 과정을 거친다. 이 과정에서 **통신망에서 정상적인 신호의 흐름을 방해하는 여러 현상이 존재하는데 만약 이 방해를 받아 보내고자 했던 신호가 바뀌었을 때 방해를 최소화함으로 정보를 원할하게 교환하거나 오고가는 정보를 최대한 보존할 수 있게끔 오류를 어떻게 찾아내고 대처하는지에 대한 기술도 프로토콜에 담겨 있다.** 덕분에 안전하게 손실 없이 정보를 전송할 수 있게 되는 것이다. 

[프로토콜 - Protocol 이란 무엇인가 : 네이버 블로그 (naver.com)](https://m.blog.naver.com/PostView.nhn?blogId=on21life&logNo=221509574568&proxyReferer=https:%2F%2Fwww.google.co.kr%2F)

## node.js
오픈 소스 JavaScript 엔진인 크롬 V8에 비동기 이벤트 처리 라이브러리인 libuv를 결합한 플랫폼이다. 다시 말해, **JavaScript로 브라우저 밖에서 서버를 구축하는 등의 코드를 실행할 수 있게 해주는 런타임 환경**이다. 처음엔 리눅스와 macOS만 지원되었으나 2011년 7월에 Windows 버전도 발표되었다.  
  
빈번한 I/O처리에 있어서의 우수한 성능, 서버 확장의 용이성, 무엇보다도 JavaScript라는 프론트엔드 필수 언어로 백엔드까지 작성할 수 있다는 엄청난 장점 때문에 출시 이후로 빠르게 점유율을 높여가고 있다. 특히 **트위터등 많은 양의 인/아웃풋 데이터를 처리해야 하는 서비스에 있어서 강점이 두드러진다.**
