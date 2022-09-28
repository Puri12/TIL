---
Tag : 코드
---

# [깔끔한 코드를 원하면 "Rule of Six"만 기억하세요](https://news.hada.io/topic?id=7493)

## 각 줄은 한가지 일만 수행합니다.

> 한줄에는 한 작업만.\
> 그러나 그것에 집착하지 마십시오.

#### - 이유
1. 짧은 코드 한줄은 긴 코드한줄보다 두뇌력을 덜 소비합니다.
2. 읽기 쉬운 코드는 추론하기 쉽습니다. 
3. 더 짧은 줄이 있는 프로그램은 이론적으로 유지보수가 쉽습니다.

* 그러나 간결한 코드는 암호처럼 보일 수 있습니다.\
그리고 코드를 나눌 수 있다고 무조건 나눠야 하는 것은 아닙니다.

## 줄 길이가 전부는 아닙니다.

Hermans의 책 "Programmer's Brain" 에서는 두뇌의 세 가지 기억 기능이 함께 작동하는 방법을 설명합니다.

* __장기 기억__(LTM): 키워드, 구문과 같은 장기 검색을 위한 정보를 저장합니다.
* __단기 기억__(STM): 변수 이름, 특수 값과 같은 단기(30초 미만!)을 위한 새로운 정보를 저장합니다.
* __작업 기억__(WM): 결론을 도출하고 새로운 지식을 도출하기위해 LTM / STM의 정보를 **처리**합니다.

STM과 WM은 한번에 4~6개 정도만 기억할 수 있습니다.\
그렇기 때문에 **6개 이상의 정보가 포함된 코드 줄은 단순화 해야합니다.**\
그것을 "Rule of Six"라고합니다.

## 예시

##### 원본 코드
```Python
maplambda x: x.split('=')[1], s.split('?')[1].split('&')[-3:])
```

##### 1차 분활
```Python
query_params = s.split('?')[1].split('&')[-3:]
map(lambda x: x.split('=')[1], query_params)
```

##### 2차 분활
```Python
url_query_string = s.split('?')[1]
query_params = url_query_string.split('&')[-3:]
map(lambda x: x.split('=')[1], query_params)
```

##### MORF 적용
> MORF는 Move Out and Rewrite as a Function의 약자로 다른 접근 방식을 취하고 함수로 그룹화 하는 것입니다.

```Python
def query_params(url):
    return url.split('?')[1].split('&')[-3:]

map(lambda x: x.split('=')[1], query_params(s))
```
---

## 코멘트

최근 알고리즘 문제를 풀면서 한 줄에 여러가지 작업하여 원하는 데이터 값으로 바꾸는 코드들을 많이 작성하였는데 기록해두고 며칠 지나서 보게되면 이해하기 힘들었던 적이 있었다.\
그럴 때마다 단순히 정리를 해두지 않고 풀기만 하는 것 때문인줄 알았지만 위와같이 뇌가 저장할 수 있는 정보는 한계가 있고 코드 한 줄에 여러 기능이 있으면 이해하기 더 어려워 진다는 부분 때문인 것 같다.\
코드가 짧아지는 것은 좋지만 "Rule of Six"를 기억해서 이해하기 쉽도록 작성하는 노력을 해봐야겠다.

---
출처: [The Rule of Six](https://davidamos.dev/the-rule-of-six/)
