

# 7. Java

**:book: Contents**

* [Java-Thread](#Java-Thread)

---

### Java-Thread

**Process**

- process란 OS로부터 실행에 필요한 자원(메모리)을 할당받아 process가 된다.
- process는 데이터,메모리등의 자원, thread로 구성



**Thread**

- process에게 할당된 자원을 이용해서 실제로 작업을 수행하는 것
- 모든 process에는 최소한 하나 이상의 thread가 존재하며, 둘 이상의 thread를 가진 process를 
   multi-threaded process라 한다.



**Multi-tasking과 Multi-threading**

- Multi-tasking이란, 여러 개의 process가 동시에 실행될 수 있는것을 의미한다.

  (대부분의 os에서 지원한다.)

- Multi-threading이란 하나의 process내에서 여러 thread가 동시에 작업을 하는것을 Multi-threading이라 한다.



**JAVA에서 Thread 구현방식**

- Thread를 구현하는 방법은 Thread클래스를 상속받거나 Runnable인터페이스를 사용하는 방법이 있다. Thread를 상속받으면 다른 클래스를 상속받을 수 없어서, Runnable인터페이스를 구현하는 방식을 주로 사용한다.

  ```java
  class ThreadEx1 {
  	
  	public static void main(String[] args) {
  		ThreadEx1_1 t1 = new ThreadEx1_1();
  		Runnable r = new ThreadEx1_2();
  		Thread t2 = new Thread(r);
  		
  		t1.start();
          //t1.start(); 같은 thread를 또 star하면 IllegalThreadStateException이 발생
  		t2.start();
  	}
  	
  	
  
  }
  
  class ThreadEx1_1 extends Thread{
  	public void run(){
  		for(int i=0; i<5; i++) {
  			System.out.println(getName());
  		}
  	}
  }
  
  class ThreadEx1_2 implements Runnable{
  	public void run() {
  		for(int i=0; i<5; i++) {
  			//Thread.currentThread() 현재 실행중인 thread를 반환
  			System.out.println(Thread.currentThread().getName());
  		}
  	}
  }start()와 run()
  ```

  

**start()와 run**

  - start메서드는 새로운 thread를 생성하는 역할을 담당하고 run은 생성된 thread가 할 작업에 대한 정의이다.

  - 아래의 그림에서 실행절차는 다음과 같다.

    - 1.main thread에서 start메소드를 호출한다.

    - 2.start 메소드는 새로운 스레드를 생성한다.(메모리 측면에서)

    - 3.생성된 thread에서 run함수 실행

        ![thread](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRPeqaGVxISRvIoItsE6ykwxOHiU_OnjH-jyZyOsWIu9a8Y_SlKWA)

      

- 호출스택이 모두 비워진 thread는 종료하게 된다.



**Thread Priority**

- thread는 우선순위(Priority)라는 속성(멤버변수)를 가지고 있고 이를 통해 thread의 실행시간을 달리할 수 있다.(숫자가 높을 수록 우선순위가 높다.,우선순위 범위는 1~10)
- main메소드는 default 우선순위 5이다. main메소드를 통해 만들어지는 thread역시 우선순위는 5
- 멀티코어 환경에서는, 우선순위에 따른 실행시간과 실행기회를 갖게 될 것이라고 기대할 수 없다. 따라서 이는 OS스케쥴링 정책과 JVM의 구현을 확인해봐야 한다. 따라서, 스레드의 우선순위를 부여하는 대신 작업에 우선순위를 두어 PriorityQueue에 저장해 놓고, 우선순위가 높은 작업이 먼저 처리되도록 하는 것이 효율적일 수 있다.



**Thread Group**

- thread group이 등장한 이유는 보안상의 이유로 도입되었다.

- 여러개의 thread를 하나의 그룹으로 묶을 수 있고 또한, thread그룹과 thread 그룹을 묶어서 새로운 group으로 만들 수 있다.(파일 생성이랑 비슷한 개념)
- 자신이 속한 thread 그룹이나 하위 thread 그룹은 변경할 수 있지만 다른 thread 그룹의 thread를 변경할 수는 없다.
- 모든 thread는 반드시 thread 그룹에 포함되어 있어야 하기 때문에, 이를 지정하지 않는 경우 기본적으로 자신을 생성한 thread와 같은 thread 그룹에 속한다.



**Damon Thread**

- Damon Thread는 일반 스레드(데몬 스레드가 아닌 스레드)의 작업을 돕는 thread 이다. 따라서 일반 thread가 종료되면 자동으로 Damon Thread는 종료된다. Damon Thread의 예는 가비지 컬렉터, 워드프로세서의 자동저장, 화면자동갱신 등이 있다.
- Damon thread는 무한루프와 조건을 이용해서 실행 후 대기하고 있다가 특정 조건이 만족되면 작업을 수행하고 다시 대기상태로 돌아간다. 또한, Damon thread가 생성한 thread는 자동적으로 Damon thread가 된다.



**Thread Execution control**

- 

> :arrow_double_up:[Top](#7-java)    :leftwards_arrow_with_hook:[Back](https://github.com/HanHoJung/Java) 

---

## Reference























































