# Java 과제

## 문제 1

>다음 코드를 실행하면 결과로 5를 기대했는데 4가 출력되었습니다.
어디에서 잘못 작성된 것일까요?

``` Java
int var1=5;
int var2=2;
double var3 = var1 / var2;
int var4 = (int)(var3 * var2);
System.out.println(var4);
```

### 원인
```Java
double var3 = var1 / var2
```
위의 코드의 `var1`과 `var2`가 int형 변수이므로 `/` 연산 시 int형 결과값이 나오게 됩니다.\
그렇기 때문에 `var3`의 결과값은 2가 되고 `var4`의 값이 2 x 2로 계산되어 4가 나오게 되는 겁니다.  


### 해결법

#### 1. 피연산자 형 변환

```Java
double var3 = (double) var1 / var2           // var1을 double형으로 형 변환
double var3 = var1 / (double) var2           // var2를 double형으로 형 변환

double var3 = (double) var1 / (double) var2  // var1, var2를 double형으로 형 변환
```

위와같이 연산되는 피연산자 중 하나의 변수를 `double` 형으로 형 변환을 시켜주면\
나머지 하나의 변수도 동일 한 `double`형으로 변환 후 연산을 하게 됩니다.\
`double`형으로 연산을 하기 때문에 결과값은 `int`형이 아닌 실수 `double`형으로 나오게 됩니다.

#### 2. 변수 선언 시 `double`형으로 선언

```Java
double var1 = 5;
double var2 = 2;
```

4번째 줄에서 결과값을 저장할 때 형 변환을 진행하기 때문에 `var1, var2`를 처음부터 `double`형으로\
선언하여 해결이 가능합니다.

#### 최종 해결코드
```Java
public class test1 {
    public static void main(String[] args) {
        int var1=5;
        int var2=2;
        double var3 = (double) var1/var2;
//        int / int = int 의 값이 나오므로 Double로 형변환을 시켜주면 됩니다
        int var4 = (int)(var3*var2);
        System.out.println(var4);
    }
}

```

---

## 문제 2

> 다음 코드를 실행했을 때 출력 결과는 무엇입니까? (증감연산자에 대해 알아보세요!)

```Java
int x = 10;
int y = 20;
int z = (++x) + (y--);
System.out.println(z);
```

### 출력 결과
```
31
```

### 코드 해석
```Java
int z = (++x) + (y--);
```

위의 코드에서 `++` 와 `--`를 증감 연산자라고 부릅니다.

> 예)\
`++x` 와 `x++` 는 `x = x + 1`  
`--x` 와 `x--` 는 `x = x - 1`

`++` 와 `--`의 위치에 따른 역할이 달라지게 되는데 그 역할은 아래와 같습니다.

| 연산식  | 설명 |
| ------------- | ------------- |
| `++` or `--`피연산자  | 다른 연산을 하기 전에 값을 증가 또는 감소 시킴 |
| 피연산자`++` or `--`  | 다른 연산을 한 후에 값을 증가 또는 감소 시킴  |

그러므로 위의 코드는 아래와 같은 연산을 하게됩니다
```Java
int z = ( ++x ) + ( y-- )
//      ( 11  ) + ( 20  )
System.out.println(z);
// 31
```

---

## 문제 3

> while문과 Math.random() 메소드를 이용해서 2개의 주사위를 던졌을 때 나오는 눈을 (눈1, 눈2) 형태로 출력하고,\
눈의 합이 5가 아니면 계속 주사위를 던지고, 눈의 합이 5이면 실행을 멈추는 코드를 작성해보세요. \
눈의 합이 5가 되는 조합은 (1,4), (4,1), (2,3), (3,2)입니다.

### 출력 예시
```
시작!
(3,6)
(2,6)
(1,4)
끝!
```

### 해결 코드

```Java
public class test3 {
    public static void main(String[] args) {
        int sum = 0;
        System.out.println("시작!");
        while (sum != 5) {
//                                random() 범위지정 (최댓값-최소값+1) + 최소값
            int num1 = (int)(Math.random() * 6) + 1;
            int num2 = (int)(Math.random() * 6) + 1;
            System.out.println("("+ num1 +"," + num2 +")");
//          또 다른 출력방법
//          System.out.printf("(%d,%d)\n", num1, num2);
            sum = num1 + num2;
        }
        System.out.println("끝!");
    }
}
```

### 코드 해석

#### - `while()` 문
> 형식\
while(조건문)

위의 조건문이 참일 때 반복적으로 내부 코드를 실행합니다.
이 문제에서는 합이 5 가 되었을 때 멈취야 하므로 조건을 `sum != 5` 합이 5가 아닐때로 지정하였습니다.



#### - `Math.random()` 함수


> 함수의 역할\
0 ~ 1 사이의 랜덤한 소수를 반환 해줍니다.\
EX) 0.13212313

`rnadom()`함수의 범위를 지정하는 방법은 함수가 주는 값이  0과 1 사이의 랜덤한 소수이기 때문에  * `최대값과 최소값의 차이  + 1`으로 설정이 가능합니다.\
최소 값 역시 + `원하는 최소값`으로 지정이 가능합니다.

