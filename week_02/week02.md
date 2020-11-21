## 2주차 - 자바 데이터 타입, 변수 그리고 배열
- - -
### 프리미티브 타입 종류와 값의 범위 그리고 기본 값
오라클 공식문서에 따르면 자바언어는 정적타입의 언어이기 때문에 변수를 사용하려면 먼저 선언해야한다고 명시되어 있습니다.

자바의 Primitive Data Type (기본데이터타입)은 8가지가 있으며, 예약된 키워드로 이름이 지정됩니다.

##### Java Primitive Data Type
1. byte
> byte 타입은 8비트의 정수를 표현합니다.
값의 범위 : -128 ~ 127
기본값 : 0
2. short
> short 타입은 16비트의 정수를 표현합니다.
값의 범위 : -32,768 ~ 32,767
기본값: 0
3. int
> int 타입은 32비트의 정수를 표현합니다.
값의 범위 : -2^31 ~ 2^31 - 1
기본값 : 0
4. long
> long 타입은 64비트의 정수를 표현합니다.
값의 범위 : -2^63 - 2^63 - 1
자바 SE 8 이상에서는 long 데이터 타입을 사용하여 최소값 0, 최대값 2^64 - 1 인 부호없는 값을 나타낼 수 있습니다.
기본값 : 0L
5. float
> float 타입은 32비트의 소수를 표현합니다.
값의 범위 : 1.4E-45 ~ 3.4028235E38
기본값 : 0.0f
6. double
> double 타입은 64비트의 소수를 표현합니다.
값의 범위 : 4.9E-324 ~ 1.7976931348623157E308
기본값 : 0.0d
7. boolean
> boolean 타입은 오직 2개의 값만 가능합니다.
값의 범위 : true / false
기본값 : false
8. char
> char 타입은 16비트의 유니코드 캐릭터를 표현합니다.
기본값 : '\u0000'

##### TIP
지역 변수의 경우는 컴파일때 초기화하지 않습니다. 때문에 지역 변수를 선언하고 사용하기 전에 값을 지정해야 합니다.
초기화되지 않은 지역 변수에 액세스 하면 컴파일 타임 오류가 발생합니다.

```java
public class Main {
    public static void main(String[] args) {
        // 초기화 되지 않은 지역 변수
        int gear;
        System.out.println(gear);
    }
}

Error : variable gear might not have been initialized
```
내용 출처 : <https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html>
- - -

### 프리미티브 타입과 레퍼런스 타입
기본형 데이터 타입 8가지를 제외한 모든 데이터 타입은 레퍼런스 데이터 타입니다.

기본형 데이터 타입은 값 그 자체를 저장하지만 레퍼런스 데이터 타입은 주소값을 저장하고 있습니다.
또한 레퍼런스 타입은 new 키워드를 사용합니다.

### 리터럴
리터럴은 변수에 값을 연산하지 않고 바로 대입하는 것을 말합니다.
```java
boolean result = true;
char capitalC = 'C';
bye b = 100;
short s = 10000;
int i = 100000;
```

### 변수 선언 및 초기화하는 방법
변수 선언 : [데이터 타입] [변수 이름];
ex ) int result;
```java
int result;
boolean isResult;
short index;
```
변수 초기화 하는 방법
```java
// 변수 선언 동시에 초기화
int result = 100;
boolean isResult = true;
short index = 10;

// 변수 선언 후에 초기화
int result;
result = 100;

boolean isResult;
isResult = true
```

### 변수의 스코프와 라이프타임
##### 변수의 스코프
1. 멤버변수
클래스 영역에서 선언한 변수를 말하며, 멤버 변수는 클래스 내 어디서든 사용이 가능하다.

2. 지역 변수
메서드 영역에서 선언한 변수를 말하며, 지역 변수는 메서드 스코프 안에서만 사용이 가능하다.

##### 라이프 타임
> Main 클래스가 생성되어 Heap영역에 올라가면, Main 클래스가 가지고 있는 멤버변수 sum, result가 Stack 영역에 생기게 된다.

> getSum 메서드를 호출하게 되면 지역 변수인 sumResult가 Stack 영역에 올라가며 getSum 메서드가 return을 하게되면 종료되면서 sumResult 도 Stack에서 사라지게 된다.

``` java
public class Main { // 클래스 스코프 Start
    // 멤버변수 (=클래스변수)
    int sum = 0;
    boolean result = false;

    public int getSum() { // 메서드 스코프 Start
        // 지역변수
        int sumResult = 100

        // 멤버변수 사용가능
        result = true;
        return sumResult;
    } // 메서드 스코프 End
} // 클래스 스코프 End
```

### 타입 변환, 캐스팅 그리고 타입 프로모션
##### 1. 명시적 형변환
어떤 타입으로 변환할지 지정해준다.
##### 2. 묵시적 형변환
두 개의 데이터 연산시 데이터의 범위가 더 큰쪽으로 자동 형변환이 일어난다.

``` java
// 1. 명시적 형변환
short num02 = 100;
int sum = (int) num02;

// 2. 암시적 형변환
short num02 = 100;
int sum = num02;
```

### 1차 및 2차 배열 선언하기
배열은 하나의 데이터 타입에 대한 고정된 크기의 컨테이너입니다.

데이터 타입은 같은데 변수는 여러개가 필요할 경우에 사용할 수 있습니다.

배열의 인덱스는 0부터 시작합니다.

단 !! 컨테이너의 크기가 정해져야 하므로 몇개의 변수가 필요한지 사전에 알고 있어야 합니다.

``` java
// 1차원 배열 선언하기
int[] anArray;

// 1차원 배열 초기화
// int 타입의 값을 10개 담을 수 있다.
anArray = new int[10];

// 1차원 배열 값 대입
anArray[0] = 100;
anArray[1] = 200;

// 1차원 배열 값 출력
System.out.println(anArray[0]);

// 출력
output : 100
```

``` java
// 2차원 배열 선언 & 초기화
String[][] names = {
    {"Mr. ", "Mrs. ", "Ms. "},
    {"Smith", "Jones"}
};

// 2차원 배열 출력
System.out.println(names[0][0] + names[1][0])

// 출력
output : Mr. Smith
```
##### TIP 배열의 크기 구하기
배열 컨테이너의 크기를 알고 싶다면 anArray.**length** 를 사용하면 알 수 있다.

> 내용 출처 : <https://docs.oracle.com/javase/tutorial/java/nutsandbolts/arrays.html>

### 타입 추론, var
Java 10 에서 새로운 기능으로 Laca-Variable Type Inference이 추가 되었습니다.

지역 변수 선언을 var 키워드를 이용하여 기존의 정적 데이터 타입 선언 방식에서 컴파일러가 타입을 추론할 수 있게 되었습니다.

개인적으로 느낀 장점으로는 클래스 이름이 길거나 비슷한 클래스 이름이 많아서 헷갈릴때 var를 쓰면 코드가 간결해져서 가독성이 좋아지는 측면이 있다고 생각이 듭니다.

```java
var name = "Seunghyun Lim";
// => String name = "Seunghyun Lim";

System.out.println(name);
```
