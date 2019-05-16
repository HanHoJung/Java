# 7. Java
**:book: Contents**

* [Java I/O Stream](#Java-I/O-Stream)

---

### Java I/O Stream
* **I/O Stream**이란 장치로부터 데이터를 입력하거나 출력하기 위해서 사용된다.

  - 서버 또는 클라이언트가 데이터를 주고 받는 경우, 키보드와 모니터, 파일

  - 입/출력 대상마다 입출력 방식이  달라진다. 그러나 자바에서는 장치에 종속되지 않고 같은 인터페이스를 제공한다. 이를 I/O Stream모델 또는 I/O모델이라 한다.

  - stream은 기본적으로 byte단위로 입/출력을 수행한다.

    

    ![img](http://hepunx.rl.ac.uk/~adye/javatutorial/java/io/images/inputstreams.trans.gif)

    ![img](http://hepunx.rl.ac.uk/~adye/javatutorial/java/io/images/outputstreams.trans.gif)

* **Filter Stream이란** stream을 보조하는 성격의 스트림이다.

  - Filter Stream도 FilterInputStream, FilterOutputStream으로 나누어진다.
  - 우리가 원하는 형태로 데이터를 읽을 수 있도록 입력 스트림 앞에 필터를 다는것이다.

  ![img](https://mblogthumb-phinf.pstatic.net/20160106_100/das135_1452066007156WK1IS_PNG/11.PNG?type=w2)

  - FilterStream 중 가장 많이 사용되는 것은 BufferedInputStream, BufferedOutsputStream 이다.

  - InputStream과OutStream에서 버퍼 필터 스트림을 사용하면 성능향상을 거둘 수 있다. 버터 입력스트림안에 내부적으로 버퍼(메모리 공간)을 갖는다. 그리고 입력 스트림으로 부터 많은 양의 데이터를 가져와 버퍼를 채운다. 때문에, read 메소드 호출시 파일에 저장된 데이터를 가져오는것이 아니라 버퍼에 저장된 데이터를 가져온다. 따라서, I/O 접근을 최소화하고 메모리에서 데이터를 가져오는 방식이므로 성능 향상에도움이 된다.

    ![img](https://mblogthumb-phinf.pstatic.net/20160106_53/das135_1452065777527mKuyi_PNG/9.PNG?type=w2)

    ![img](https://mblogthumb-phinf.pstatic.net/20160106_57/das135_1452065785393WKECT_PNG/10.PNG?type=w2)

  - Filter 스트림을 아래 그림과 같이 연결할 수 도 있다.

    

    ![img](https://mblogthumb-phinf.pstatic.net/20160106_162/das135_1452066692558RhCcF_PNG/12.PNG?type=w2)

* **character Stream** 운영체제와 java 간의 문자 인코딩 방식을 프로그래머가 손쉽게 사용하기 위해서 등장하였습니다. 

  - 자바는 기본적으로 모든 문자를 유니코드를 기준으로 표현합니다. 윈도우의 경우 CP949 인코딩 방식을 사용하기 때문에 프로그래머가 의도한 문자를 다르게 해석하게 됩니다. 따라서 프로그래머가 일일이 운영체제에 맞게 변환해주는 작업이 필요합니다. 이를 해결해주는 것이 문자 스트림 입니다.

  - 문자 스트림에도 BufferedReader,BufferedWriter 같은 필터 스트림을 적용할 수 있습니다.

    ![img](https://t1.daumcdn.net/cfile/tistory/267532415324E44E05)

* **IO스트림 기반의 인스턴스 저장**

  - ObjectInputStream, ObjectOutputStream 클래스 사용

  - 직렬화(Serialization)는 오브젝트(Object)를 Binary 형태의 파일로 만드는 기술이다.

    역직렬화(Deserialization)는 Binary를 오프젝트(Object)로 만드는 기술이다.

  - 직렬화를 시켜줄 클래스에 Serializable 인터페이스를 붙여야 한다.

  - transient 키워드가 붙은 것은 직렬화대상에서 제외된다. 저장이 안된다는 의미이다.


> :arrow_double_up:[Top](#7-java)    :leftwards_arrow_with_hook:[Back](https://github.com/HanHoJung/Java) 

---

## Reference

<http://hepunx.rl.ac.uk/~adye/javatutorial/java/io/overview.html>

<https://m.blog.naver.com/PostView.nhn?blogId=das135&logNo=220589478513&proxyReferer=https%3A%2F%2Fwww.google.com%2F>

<https://www.youtube.com/watch?v=variM5qJsQM>























































