---
title: "코딩 테스트를 위한 파이썬 문법 1"
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

이 포스팅은 이전에 파이썬을 배운 경험이 있지만, 구체적인 문법사항들을 다시 공부하고 싶으신 분들에게 적합한 내용입니다.

<br/>

<br/>

## ▷ 자료형

### 1. 수자료형

- e나 E를 이용한 지수 표현 방식

  e 다음에 오는 수는 10의 지수부를 의미

  <font style="color:#6666ff">숫자 e <sup> 지수 </sup> == 숫자 x 10 <sup> 지수 </sup></font>

  e.g.) 1e9 == 10<sup>9</sup> == 1,000,000,000

- 정확한 소수점 값을 비교하는 작업이 필요할 때 round() 함수 사용

  <font style="color:#cc3333">round(실수형 데이터, 반올림하고자 하는 위치-1)</font>

  e.g.) round(123.456,2) == 123.46

- 숫자 사칙연산( +, -, *, /)

  (※ 나누기를 할 때에는 소수점까지 써야됨)

  > a**b: a의 b제곱
  >
  > a//b: a를 b로 나눈 몫
  >
  > a%b: a를 b로 나눈 나머지
  
- **<mark style='background-color: #ffffcc'>숫자 관련 유용한 함수 모음</mark>**

  ```python
  abs(숫자)  #숫자를  절댓값으로  반환
  int(a)     #a를 문자열 형태의 숫자나 소수점이 있는 숫자 등을 정수형으로 (소수점x)
  int(a,b)   #b진수로 표현된 a를 10진수로
  e.g.) int('11',2)  #2진수로 표현된 '11'을 10진수로
  hex(a)     #정수 십진수 a를 16진수로
  oct(a)     #정수 십진수 a를 8진수로
  pow(a,b)   #a**b a의 b제곱
  list(range(a))      #0부터 a앞까지 리스트로 
  list(range(a,b,c))  #a부터 b앞까지 c만큼 증가하면서 리스트로 
  divmod(a,b)         #(a//b,a%b) (몫,나머지)
  ```


<br/>

### 2. 리스트 자료형

- 표기법: [ ]

  좌우에 대괄호([])가 있으면 된다. 원소로는 아무거나 들어갈 수 있으며, 아무것도 없어도 된다. 순서가 있다. 쉼표(,)를 기준으로 원소를 구분한다. 인덱스는 0부터 시작한다.

- 비어있는 리스트 선언

  a=list()

  a=[]

- <font style="color:#6666ff">리스트 인덱싱</font>

  변수/리스트[n]: 인덱스 n에 있는 원소를 가져옴.  (이때 n은 정수 또는 변수이다.)

  ※ 이때 n에 음의 정수를 넣으면 원소를 거꾸로 탐색한다. 즉, 인덱스에서 -1은 마지막 원소를 의미한다.

- <font style="color:#6666ff">리스트 슬라이싱</font>

  대괄호 안에 콜로(:)을 넣어 연속적인 원소들을 한번에 가져올 수 있다.

  [a:b] 이면 a부터 b전 자리까지 있는 원소들을 리스트로 가져온다.

  e.g.)

  ```python
  a=[1,2,3,4,5,6,7,8,9]
  print(a[1:4]) # 결과는 [2,3,4]
  ```

- <font style="color:#cc3333">리스트 연산 (문자열과 같은 형식임)</font>

  > 1. 리스트+리스트  #리스트의 나열  
>
  >    ※ 리스트 끼리만 더하기 가능 ('리스트+문자열'은 오류) (문자열도 문자열끼리만)
>
  > 2. 리스트-리스트  #오류!!
>
  > 3. 리스트*n           #리스트를 n번 나열

- <font style="color:#6666ff">리스트 컴프리헨션(comprehension)</font>

  대괄호 안에 조건문과 반복문을 넣어 리스트를 초기화하는 것이다.

  ```python
  array=[i for i in range(20 if i%2==1)]
  ```

  위의 코드처럼 리스트 컴프리헨션을 이용했을 때와 아래 코드처럼 반복문과 조건문을 각자 사용했을 때의 array 리스트의 값은 같다.

  ```python
  array=[]
  for i in range(20):
      if i%2==1:
          array.append(i)
  ```

  따라서 짧고 간결한 리스트 컴프리핸션을 이용하는 것이 더 효율적인 코드임을 확인할 수 있다.

- **<mark style='background-color: #ffffcc'>리스트 관련 유용한 함수 모음</mark>** (이때 w는 리스트 변수를 의미)

  ```python
  w.append(~)    #리스트 맨 오른쪽에 ~를 추가
  w.sort()       #리스트 원소들을 사전순(오름차순)으로 정렬
  w.sort(reverse=True)   #리스트 원소들을 사전반대순(내림차순)으로 정렬
  w.reverse()    #리스트 원소의 순서를 반대로 정렬
  w.index(~)     #리스트에서 ~이 어느 자리에 있나( 없는 것을 찾으면 error나옴.)
  w.insert(a,b)  #인덱스 a 자리에 b를 넣음
  w.remove(a)    #리스트 내의 a를 지움(2개 이상 이면 맨 왼쪽 것만 지움)(없는 원소를 지우려고 하면 에러뜸)
  w.pop()        #리스트 내의 맨 마지막에 있었던 것이 출력되고, 리스트에서 삭제됨
  w.pop(a)       #리스트 내의 a번째 있었던 것이 출력되고, 리스트에서 삭제됨
  w.count(a)     #리스트에서 a 가 몇 개 있나
  w.extend([a])  #리스트 뒤에  a를 추가
  len(w)         #w 의 길이(w에 들어있는 아이템 갯수)
  ```

<br/>

### 3. 문자열 자료형

- 표기법: "a", 'a', """a""", '''a'''

  0개 이상의 문자 나열 가능 (공백도 따옴표가 붙어있으면 문자열임)

- 특수 문자들 출력하는 방법 (역슬래시 " \ "입력 후, 원하는 특수문자를 입력)

  ```python
  "\n"    #줄바꿈(개행)
  "\t"    #탭(가로)
  "\v"    #탭(세로)
  "\\"    #문자\
  "\'"    #문자'
  "\""    #문자"
  "\r"    #캐리지 리턴 (앞에 거 지우고 줄바꿈)
  "\b"    #백스페이스
  "\000"  #널문자
  ```

- <font style="color:#cc3333">문자열 연산</font> (리스트와 같은 형식임)

  > 1. 문자열+문자열  #문자열의 나열  ※문자열 끼리만 더하기 가능
  > 2. 문자열-문자열   #오류!!
  > 3. 문자열*n            #문자열을 n번 나열
  
  ```python
  a="Hello"
  b="World"
  print(a+" "+b)  #"Hello World"가 출력됨
  print(a*3)  #"HelloHelloHello"가 출력됨
  ```
  
- 문자열도 리스트와 마찬가지로 인덱싱과 슬라이싱을 이용할 수 있다.

<br/>

### 4. 튜플 자료형

튜플은 리스트와 거의 비슷하다. 따라서 리스트와의 차이점과 주의할 점을 알아보자.

- 리스트는 mutable, 튜플은 Immutable (튜플은 한번 선언된 값을 변경할 수 없다. 즉, 대입연산자 '='이 불가능하다.)

- 리스트는 대괄호[ ]를 이용하여 표현하지만, 튜플은 소괄호( )로 감싸서 표현한다.

- 튜플이 1개의 요소만을 가질 때는 요소 뒤에 콤마(,)를 반드시 붙여야 하고, 괄호()는 생략해도 무방하다.

- <font style="color:#cc3333">튜플도 순서가 있다. (인덱싱과 슬라이싱 가능)</font>

```python
target=1,  #튜플 자료형으로 (1,)과 동일
target=(1) #숫자 자료형으로 1과 동일
```

<br/>

### 5. 사전(DIctionary) 자료형

<font style="color:#6666ff">key와 value의 쌍을 데이터로 가지는 자료형.</font> 딕셔너리는 mutable로, 값을 변경할 수 있다.

- <font style="color:#6666ff">key</font>: 하나의 변수. 여러 자료형들이 한번에 들어올 수 있다. 동일한 key 값들이 있을 경우, 마지막의 key에 해당되는 value만 유의미하다. 

  ※ 여기에는 <font style="color:#6666ff">immutable한 자료형들만 들어 갈 수 있다.</font> 이때 immutable한 자료형이란, 수, 문자열, 튜플과 같은 자료형을 의미한다.

- <font style="color:#6666ff">value</font>: key에 대응되는 값. (또 다른 딕셔너리가 value로 들어올 수 있다.)

이러한 key-value 쌍으로 구성된 dictionary 자료형을 처리하는 것은 리스트 자료형보다 훨씬 빠르게 동작한다.

```python
dict={1:123,'2':'456'}
a=2
b=3
dict[a]=b  #a라는 key가 없었을 때, dict에 a-b 쌍이 추가로 생성됨. 
           #a라는 key가 있었을 때, 해당 value가 b로 수정됨.
del dict[a] #a key와 그에 대응되는 value를 삭제
dict.keys()   #key들을 모아서 리스트로 보여줌. 이 예시에서는 dict_keys([1,'2'])
dict.values() #key의 value들 값을 모아서 리스트로 보여줌. 이 예시에서는 dict_values([123,'456'])
dict.items()  #모든 key와 value값들을 보여줌. 이 예시에서는 dict_items([(1,123),('2','456')])
dict.get(a)   #a key에 대응되는 value값을 보여줌. 이 예시에서는 None이라는 결과가 나옴.
dict.clear()  #dict값들을 다 삭제. 즉, dict={}이 됨.
```

<br/>

### 6. 집합(Set) 자료형

- 표기법: set()

- <font style="color:#cc3333">중복×</font> (동일한 값 넣을 수 없음)

- <font style="color:#cc3333">순서x</font>  (인덱싱 사용하면 오류남)

```python
set([1,2,3]) #{1,2,3}과 동일
set("hello") #set(["h","e","l","l","o"])와 동일. {’o’,’l’,’e’,’h’}와도 동일
```

- **<font style="color:#6666ff">집합의 연산</font>**

  > 1. 합집합
  >
  >    AㅣB == A.nuion(B) == B.union(A)
  >
  > 2. 교집합
  >
  >    A&B == A.intersection(B) == B.intersection(A)
  >
  > 3. 차집합
  >
  >    A-B == A.difference(B)
  >
  >    B-A == B.difference(A)
  
  ```python
  a=set([1,2,3,4,5])
  b=set([3,4,5,6,7])
  print(a|b) #{1,2,3,4,5,6,7}
  print(a&b) #{3,4,5}
  print(a-b) #{1,2}
  ```
  
- 집합 관련 함수

  ```python
  s=set([1,2,3])
  s.add(4)        #새로운 원소 한 개를 추가하는 것 (여러 개를 추가하려하면 오류 남)
  s.update([5,6]) #새로운 원소 여러 개를 추가하는 것 (한 개도 가능)
  s.remove(3)     #특정한 원소 한 개를 삭제하는 것
  ```


<br/>

<br/>

++추가 내용)

<font style="color:#cc3333">언더바(_)</font>

파이썬에서 반복문 사용시, _는 어떤 <font style="color:#cc3333">특정값을 무시하기 위한 용도</font>로 사용되기도한다. 값이 필요하지 않거나 사용되지 않는 값을 _에 할당하기만 하면된다.

e.g.)

```python
for _ in range(5):
    print("Hello World")
```



<br/>

<br/>
