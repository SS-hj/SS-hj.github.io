---
title: "코딩 테스트를 위한 파이썬 문법 2"
category: 코딩 테스트
tag: 
- 코딩 테스트
- 파이썬
toc_label: "목차"
toc: true
toc_sticky: true
header:
 teaser: /assets/images/coding_test.png

---



<br/>

본 내용은 "이것이 취업을 위한 코딩 테스트다 with 파이썬" 책의 부록 A 부분과 순천향대학교 정엽섭 교수님의 "파이썬" 과목 수강시 정리했던 내용을 기반으로 포스팅하였습니다.

이 포스팅은 이전에 파이썬을 배운 경험이 있지만, 정확한 문법들을 잊어 주요 문법들을 다시 공부하고 싶으신 분들에게 적합한 내용입니다.

<br/>

<br/>

## ▷ 조건문



※ 해당 조건문에 속하는 문장은 들여쓰기(Tab or 스페이스바*4)하여 써야 함

```python
if 조건문 1:
	조건문 1이 True일 때 실행할 코드
elif 조건문 2:
	조건문 1이 아니면서, 조건문 2가 True일 때 실행할 코드
else:
	위의 조건들 1, 2가 모두 False일 때 실행할 코드
```



> **elif**  (else if; 그게 아니라면~ )
>
> if문이 나오면 elif는 여러개 나올 수 있음
>
> else는 if 하나당 한개만 가능



※ if False == if 0 (정수형에서는 0이 아니면, 전부 True이다.) == if " " == if [ ] == if ( ) == if None



**비교 연산자**

파이썬에서는 같은 값일 때 비교연사자는 "=="이며, 다를 때 비교 연산자는 "!="이다. 이외의 비교 연산자는 일반 수학에서의 부등호와 같으므로 생략하자.



**논리 연산자**

| 논리 연산자 | 설명                                               |
| ----------- | -------------------------------------------------- |
| X and Y     | X와 Y가 모두 참(True)일 때 X and Y가 참(True)이다. |
| X or Y      | X와 Y 중에 하나만 참(True)이어도 참이다.           |
| not X       | X가 거짓(False)일 때 참이다.                       |



**파이썬의 기타 연산자**

| in 연산자와 not in 연산자            | 설명                                              |
| ------------------------------------ | ------------------------------------------------- |
| X in 리스트/튜플/문자열/사전 ...     | 리스트 안에 X가 들어가 있을 때 참(True)이다.      |
| X not in 리스트/튜플/문자열/사전 ... | 문자열 안에 X가 들어가 있지 않을 때 참(True)이다. |



<br/>

## ▷ 반복문



**for문**

```python
for 변수 in 리스트/문자열/튜플 등 :
	실행문
```

 

> **range**
>
> range(시작 값, 끝 값+1)로 써야 한다.
>
> 만약 range(k)와 같이 하나의 값만 넣으면, 자동으로 range(0, k)로 시작값이 0이 된다.



```python
result=0

# 이 코드에서 i는 1부터 9까지의 모든 값을 돌아가면서 누적합을 구하게 된다.
for i in range(1,10):
    result+=i
print(result)  #45
```



**while문** 

```python
while 조건문:  #조건이 참일동안 실행문들을 반복
	실행문
```

※ 반복문은 얼마든지 중첩하여 사용할 수 있다

<br/>

※  for문과 while문에 사용 가능한 break 문과 continue문

**break; 중단하기**

이를 반복문 중간에 사용하면, 해당 조건이 True일 시, 해당 반복문을 빠져나간다.

```python
nums=[1,2,3]
for x in nums:
    if x > 1 :break
        print(x)  # 1만 출력하고 반복문을 빠져나가게 된다.
```

**continue; 스킵하기**

이를 반복문 중간에 사용하면, 해당 조건이 True일 시, 해당 반복문 코드를 skip하고, next로 넘어가게 된다.

```python
nums=[1,2,3]
for x in nums:
    if x % 2 == 0:continue
        print(x)  # 1을 print하고, 2는 skip한 뒤, 3을 print하게 된다.
```





<br/>

## ▷ 함수



특정한 알고리즘을 수행한 결과를 반복적으로 출력하도록 요구하는 경우, 이 알고리즘을 함수화하여 사용하면, 보다 효율적인 코드로 문제를 풀 수 있다.



**함수**

```python
def 함수이름():
    실행할 소스코드
    return 반환값  # 반환하고자 하는 값이 있을 때 사용. 결과값을 저장하고 종료. return이 없을 수도 있음
함수이름()    # 생성한 함수를 호출 
```

 ※  return은 결과값을 출력하지 않으며, 저장만 한다. print는 결과값을 저장하지 않으며, 출력만 한다. 따라서 만약 함수를 정의할 때 return이 없이 print로 끝이 나면, 해당 함수 호출과 동시에 결과가 출력되며, 특정 변수에 함수 호출문을 대입하였어도 해당 변수는 함수의 결과값을 저장하지 못한다.

<br/>

 ※  인자를 지정하여 넣어줄 경우, 매개변수의 순서가 달라도 상관이 없게된다. 반대로 말하자면, <font style="color:#cc3333">인자를 지정하지 않고 매개변수 값을 넣어줄 경우엔 순서를 지켜서 값을 넣어주어야 한다는 것이다.</font>

※  함수 인자의 기본값을 설정할 수 있는데, 이때 기본값이 있는 것들은 가장 오른쪽(←) 부분에 있어야 한다. 반대로 매개변수는 왼쪽부터(→) 값을 지정해주어야 한다.

```python
def add(a,b):
    print('함수의 결과:',a+b)
add(b=3,a=7) # 10이 출력됨
```

```python
def summation(a,b=2): # 인자의 default값은 오른쪽부터 넣어야 한다.
    return a+b
print(summation(1)) # 3 출력됨 (매개변수의 값이 왼쪽부터 지정된다.)
```



※  함수 밖에서 변수 데이터를 변경해야 하는 경우에는, 함수에서 <font style="color:#6666ff">global 키워드</font>를 이용하여 변수를 생성하면 된다. 

```python
a=0
def func():
    global a
    a+=1
for i in range(10):
    func()
print(a) # 10이 출력됨
```



**lambda 함수**

람다 표현식을 사용하면, 함수를 매우 간단하게 작성하여 적용할 수 있다.

```python
# lambda [변수들]: [return할 코드문] 
print((lambda a,b: a+b)(3,7)) # 10이 출력됨
```



<br/>

## ▷ 입출력



**입력**

일반적으로 첫 번째 input으로는 데이터 개수가 주어지고, 실제 처리할 데이터가 그 다음 input으로 들어오는 경우가 많다.

이때 input 데이터를 파이썬에는 input() 함수를 이용하여 입력받는다.

input() 함수는 한 줄의 문자열을 입력받는 함수이다.

이를 이용하여 실제로 유용하게 자주 쓰이는 입력 코드를 살펴보자.



```python
# 데이터가 공백으로 구분되는 여러 개의 정수 데이터를 입력받는 경우
list(map(int,input().split()))
```

① input()으로 문자열을 입력받음

② split()으로 공백을 기준으로 문자열들을 나누어 리스트로 바꿈

③ map으로 해당 리스트의 모든 원소에 int()를 적용

④ 최종 결과를 하나의 list()로 다시 바꿈



```python
# 특정 개수의 정수 데이터를 입력받는 경우
n, m, k = map(int,input().split()) # 각각의 변수에 정수 데이터를 입력받게 됨
```



```python
# 많은 입력을 빠르게 받아야 하는 경우
import sys
# rstrip은 마지막 줄바꿈 기호로 들어오는 공백 문자를 제거해주는 역할을 함
Sys.stdin.readline().rstrip() 
```



**출력**

print()를 이용하여 출력한다. 

이때 주의할 점은 <font style="color:#cc3333">숫자와 문자열을 함께 출력할 경우, str()으로 숫자를 감싸 출력</font>해주어야 한다.

```python
a = 2
print("내가 좋아하는 숫자는 "+str(a)+"야.") # 내가 좋아하는 숫자는 2야.
```

이는 문자열은 문자열끼리만 더하기 연산이 가능하기 때문이다.

또한 콤마(,)를 print 함수 안에 써주면, 공백이 포함되어 출력된다.

따라서 공백을 넣고 싶지 않다면 콤마 대신 +를 이용하자.



Python 3.6이상의 버전부터는 f-string 문법을 사용할 수 있다.

```python
a = 2
print(f"내가 좋아하는 숫자는 {a}야.") # 내가 좋아하는 숫자는 2야.
```

문자열 앞에 "f"를 붙이고 숫자 변수는 중괄호({})에 넣어주면 된다.



<br/>

## ▷ 주요 라이브러리의 문법과 유의점



**표준 라이브러리**? 특정한 프로그래밍 언어에서 자주 사용되는 표준 소스코드를 미리 구현해 놓은 라이브러리



코딩 테스트를 위해 반드시 알아야 하는 라이브러리와 핵심 기능들을 알아보자.



- 내장 함수

import 없이 사용할 수 있는 파이썬 자체 내장 라이브러리 함수들이다.

앞에서 설명한 input(), print() 도 내장 함수 이다.

```python
n = sum([1,2,3,4,5]) # 리스트와 같은 iterable 객체가 들어왔을 때, 모든 원소의 합을 반환
print(n) #15
n = min(7,3,5,2)    # 2개 이상의 값 중 최소값 반환
print(n) #2
n = max(7,3,5,2)    # 2개 이상의 값 중 최대값 반환
print(n) #7
n = eval("(3+5)*7") # 문자열 형식으로 들어온 수학 수식의 계산 결과를 반환
print(n) #56
n = sorted([9,1,8,5,4]) # 오름차순으로 정렬
print(n) #[1,4,5,8,9]
n = sorted([9,1,8,5,4], reverse = True) # 내림차순으로 정렬
print(n) #[9,8,5,4,1]
```

*iterable 객체: 반복 가능한 객체  (e.g. 리스트, 사전 자료형, 튜플 자료형)



- itertools

이때 이 라이브러리에서 사용하는 것은 함수가 아니라 클래스이므로, list()를 이용하여 리스트 자료형으로 변환하여 사용함을 주의하자.

permutations는 iteratble 객체에서 r개의 데이터를 뽑아 일렬로 나열하는 모든 경우(순열)를 계산

```python
from itertools import permutations
d = ['A','B','C']
r = list(permuatations(d,2)) #d에서 2개를 뽑아 나열하는 모든 순열을 계산
print(r)
```



combinations는 iterable 객체에서 r개의 데이터를 뽑아 순서를 고려하지 않고 나열하는 모든 경우(조합)를 계산

```python
from itertools import combinations
d = ['A','B','C']
r = list(combinations(d,2)) #d에서 2개를 뽑아 나열하는 모든 조합을 계산
print(r)
```



product는 permutations과 비슷하나, 이미 뽑은 원소를 다시 뽑을 수 있다. 객체 초기화는 해당 데이터 수를 repeat속성에 넣어줌으로써 진행된다.

```python
from itertools import product
d = ['A','B','C']
r = list(product(d,2)) #d에서 2개를 뽑아 나열하는 모든 순열을 계산(중복 허용)
print(r)
```



combinations_with_replacement는 combinations과 비슷하나, 이미 뽑은 원소를 다시 뽑을 수 있다. 

```python
from itertools import combinations_with_replacement
d = ['A','B','C']
r = list(combinations_with_replacement(d,2)) #d에서 2개를 뽑아 나열하는 모든 조합을 계산(중복 허용)
print(r)
```



- heapq

힙(Heap) 기능을 제공.

파이썬의 힙은 최소 힙으로 구성되어 있으므로 단순히 원소들을 전부 힙에 넣었다가 빼는 것만으로 시간복잡도 O (*NlogN*)에 오름차순 정렬이 완료된다.

이러한 힙정렬을 구현하는 코드를 예제를 통해 살펴보자.

```python
import heapq

def heapsort(iter):
    h = []
    res = []
    # 모든 원소를 차례대로 힙에 삽입
    for value in iter:
        heapq.heappush(h, value)
    # 힙에 삽입된 모든 원소를 차례대로 꺼내어 담기
    for i in range(len(h)):
        res.append(heapq.heappop(h))
    return res
res = heapsort([1,3,5,7,9,2,4,6,8,0])
print(res)  #[0,1,2,3,4,5,6,7,8,9]
```



파이썬은 최대 힙을 제공하지 않으므로, 내림차순 정렬을 하고자 할 때에는 원소들의 부호를 임시로 변경하여 사용한다.

```python
import heapq

def heapsort(iter):
    h = []
    res = []
    # 모든 원소를 차례대로 힙에 삽입
    for value in iter:
        heapq.heappush(h, -value)
    # 힙에 삽입된 모든 원소를 차례대로 꺼내어 담기
    for i in range(len(h)):
        res.append(-heapq.heappop(h))
    return res
res = heapsort([1,3,5,7,9,2,4,6,8,0])
print(res)  #[9,8,7,6,5,4,3,2,1,0]
```



- bisect

이진 탐색을 쉽게 구현하게 도와주는 라이브러리

bisect_left(a, x): 리스트 a의 정렬된 순서 상에서 데이터 x를 삽입할 가장 왼쪽 인덱스를 찾는 함수

bisect_right(a, x): 리스트 a의 정렬된 순서 상에서 데이터 x를 삽입할 가장 오른쪽 인덱스를 찾는 함수

```python
from bisect import bisect_left, bisect_right
a = [1,2,4,4,8]
x = 4

print(bisect_left(a,x))  # 2 반환
print(bisect_right(a,x)) # 8 반환
```



위 함수들을 이용하여 정렬된 리스트에서 특정 범위안에 속하는 원소들의 개수를 빠르게 구할 수 있다.

```python
from bisect import bisect_left, bisect_right

# [left_index, right_index]에 속하는 원소 개수를 반환하는 함수
def count_by_range(a, left_value, right_value):
    right_index = bisect_right(a, right_value)
    left_index = bisect_left(a, left_value)
    return right_index - left_index

a = [1,2,3,3,3,3,4,4,8,9]
print(count_by_range(a,4,4)) # 2 반환
print(count_by_range(a,1,3)) # 6 반환
```



- collections

유용한 자료구조를 제공하는 라이브러리

기본 리스트 연산은 맨 뒤 원소를 기준으로 적용되므로, 맨 앞 쪽을 기준으로 적용하고자 할 때는 시간 복잡도가 O(N)이다. 이때 deque를 이용하면 O(1)로  같은 작업을 수행할 수 있다.

deque는 스택이나 큐의 기능을 모두 포함한다고 할 수 있다.

```python
from collections import deque

popleft() # 첫 번째 원소를 제거
pop()     # 마지막 원소를 제거
appendleft(x) # 첫 번째 인덱스에 x를 삽입
append(x)     # 마지막 인덱스에 x를 삽입
```



Counter는 iterable 객체가 주어졌을 때, 해당 객체 내부에서 특정 원소가 몇 번씩 등장했는지 알려준다.

```python
from collections import Counter

counter = Counter(['red','blue','red','green','blue','blue'])

print(counter['blue']) # 'blue'가 등장한 횟수 출력
```



- math

자주 사용되는 수학적인 기능을 포함하는 라이브러리이다.

팩토리얼, 제곱근, 최대공약수 등을 계산해주는 기능이 포함되어 있다.

```python
import math

math.factorial(n) # n!을 반환
math.sqrt(n)      # n의 제곱근을 반환
math.gcd(a,b)     # a와 b의 최대 공약수를 반환
math.pi           # 파이(pi) 반환
math.e            # 자연상수 e 반환
```



<br/>

<br/>

