## 변수

---

### 일반적인 변수 선언 방법

```go
package main

import (
	"fmt"
)

func main() {
	//방법 1
	var test string
	test = "test"
	fmt.Println(test)

	// 방법 2
	var test2 string = "test2"
	fmt.Println(test2)

	// 방법 3
	var test3 = "test3"
	fmt.Println(test3)

	// **방법 4 (짧은 선언)**
	test4 := "test4"
	fmt.Println(test4)

	// 여러 변수 선언 방법
	test5, test6 := "test5", "test6"
	fmt.Println(test5)
	fmt.Println(test6)

	var (
		hello string
		world string
	)
	hello = "hi"
	world = "world"
	fmt.Println(hello, world)

}

/* 결과
test
test2
test3
test4
test5
test6
hi world
*/
```

**변수 선언 규칙**

- 변수의 이름은 숫자가 아닌 문자로 시작해야한다.
- 사용하지 않는 변수가 있을 경우 에러가 발생한다.
- 타입이 명시되지 않은 경우에는 컴파일시 자동으로 타입을 추론한다.
- 여러개의 변수 선언시 선언하는 변수와 초기화 하는 값의 개수가 같아야한다.

### 전역 변수 선언 방법

```go
package main

import (
	"fmt"
)

// 방법1 (비어있는 변수)
var test1 string

// 방법 2
var test2 string = "test2"
// 방법 3
var test3 = "test3"

// 에러
// test4 := "test4"

func main() {
	test1 = "test1"
}

```

- 단축 구문을 사용해서 전역 변수 선언시 에러가 발생한다.
