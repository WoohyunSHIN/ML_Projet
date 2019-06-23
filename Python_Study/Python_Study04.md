

// Reference Book : [점프 투 파이썬](https://wikidocs.net/book/1)

// Written by WoohyunSHIN. I reconstitute the reference book as my style for studying. If you have question or I commit an infrigement of copyright, send me a mail <swh159@gmail.com> please thank you.

# Python

***

#4. 함수

> 프로그래밍을 하다 보면 똑같은 내용을 반복해서 작성하고 있는 자신을 발견할 때가 종종있다. 특히 파이썬 같은 경우 들여쓰기의 가독성이 좋지 않기 때문에 많은 기능을 함수화 시켜 놓는게 필수 적이다. 

## 4.1. 파이썬의 함수 구조

> return 은 종료를 뜻하기도 하고 또는 다시 반환할 값을 지정할 수 있다. 예를 들어 **return a+b** 처럼 함수를 끝낼 수 있다. 다양한 함수들이 존재하는데
>
> - 일반적인 함수
>
> ```python
> >>> def add(a,b):
> ... 	result = a + b
> ... 	return result
> ```
>
> - 입력값이 없는 함수
>
> ```python
> >>> def say():
> ... 	return "Hi"
> ```
>
> - 결과값이 없는 함수
>
> ```python
> >>> def add(a,b):
> ... 	print("%d, %d의 합은 %d 입니다."%(a,b,a+b))
> ```
>
> - 입력값도 결과값도 없는 함수
>
> ```python
> >>> def say()
> ...	print('Hi')
> ```

```python
>>> def 함수명(매개변수):
... 	<수행할 문장1>
... 	<수행할 문장2>
... 	<수행할 문장3>
... 	return 
```

**IMPORTANT** :

#### 매개변수(parameter) vs 인수(argument) ?

```python
# a,b 는 parameter
>>> def add(a,b):
... 	return a+b

# 3,4 는 인수
>>> print(add(3,4))
```

***

## 4.2. 입력값이 몇개가 될지 모를때는 어떻게 해야할까 ?

> C 언어 같은 경우 malloc 을 사용하여 메모리 heap 에 공간을 잡아 놓고 사용해야하는데 파이썬은 이 부분해결을 아래와 같이 편하게 해결하도록 해놓았다. 모양은 **( )** 튜플 자료형으로 여러개의 매개 변수를 집어 넣을 수 있게 설정되어있다.

```python
>>> def add_many(*args):
... 	result = 0
... 	for i in args:
... 		result += i
... 		return result

# 변수의 갯수를 정해놓은 것과 달리 마음대로 집어 넣을 수 있다.
>>> print(add_many(1,2,3,4,5,6,912))
933
```

### 4.2.1. 키워드 파라미터 (kwargs)

keyword arguments 는 일반 arguments 와 달리 별표시(*) 를 **2개** 사용한다. 아래의 코드에서 확인해 보자. **kwargs 처럼 매개변수 명 앞에 

```python
>>> def print_kwargs(**kwargs)
... 	print(kwargs)
...
>>>
>>> print_kwargs(a=1)
{'a':1}

>>> print_kwargs(name='foo', age=3)
{'age':3,'name':'foo'}
```





### (수정해야한다) 3.5.2. 고객관리 프로그램(DB_function)

> 콘솔형 고객 정보 관리 시스템 구축

1. 기능 : 고객 정보 입력(I), 현재/이전/다음 고객 정보 조회(C/P/N), 고객 정보 수정(U), 고객 정보 삭제(D), 고객 정보 종료(Q)

- 괄호 안 영문자를 입력하면 각 기능이 구현되게 만든다  
- 종료(Q)를 입력하기 전까지 기능 선택 메시지가 계속 뜨도록 만든다  
- 각 기능은 함수로 관리한다  
- 입력된 각 정보는 인덱스 값에 따라 페이지를 가진다  
  -> 첫 정보 입력시 인덱스는 0이므로, 입력 전 기본 page 값은 -1로 설정한다

2. 입력(I)

- dictionary로 각 키의 값을 받고 빈 리스트에 채워나간다
- 성별(sex) : M, m, F, f로만 입력 가능  
      -> 소문자로 입력하는 경우 대문자로 자동 변환  
      -> sex 값이 M 또는 F가 아닐 경우 다시 입력  
- 이메일(email) : 입력값 내 '@'가 반드시 있어야 함  
      -> 정규표현식 사용  
      -> re를 import 하여 이메일 입력값 내 '@' 존재 여부 파악  
      -> 없는 경우 '@'를 포함하라는 문구와 함께 재입력 하도록 함
- 출생년도(birthyear) : 4자리로 입력 해야  
      -> len 값으로 입력 값의 길이를 구함  
      -> 4자리가 아닐 경우 재입력 하도록 함
- 출생년도까지 입력이 완료되었을 경우  
  -> 키 값 입력이 완료된 customer 딕셔너리를 custlist 리스트에 추가(append)한다  
  -> 고객 정보가 새로 입력 되었으므로 page 값에 1을 더한다

3. 조회(C, P, N)

- 인덱스는 0부터 시작하나 페이지는 통상 1부터 시작하므로 페이지 출력시 page+1 값을 반환한다
- 이전 페이지 조회(P)의 경우, 첫 번 째 페이지인 상태에서 이전 페이지로 이동이 불가하므로 현재 페이지인 첫 번 째 페이지를 반환
- 다음 페이지 조회(N)의 경우, 마지막 페이지인 상태에서 다음 페이지로 이동이 불가하므로 현재 페이지인 마지막 페잊이를 반환
                

4. 삭제(D)

- unique한 키를 기준으로 삭제정보를 선택한다 -> 여기서는 이메일로 가정
- 삭제 성공 여부 변수(delok)  
  -> 입력한 이메일이 등록된 정보 내에 있을 경우 삭제  
  -> 삭제가 성공하면 delok=1 (default 값 0)  
  -> 등록된 정보 내에 없는 이메일일 경우(delok=0) 등록되지 않았다고 출력 

5. 수정(U)

- unique한 키를 기준으로 수정정보를 선택한다 -> 여기서는 이메일로 가정
- 입력한 이메일과 일치하는 고객 정보의 인덱스를 idx에 입력  
  -> idx의 default 값은 -1  
  -> 일치 여부 확인 후에도 idx가 -1일 경우 등록되지 않았다고 출력
- 이메일 외에 이름, 성별, 출생년도 중 수정할 정보 선택
- 수정할 정보 선택 후 수정할 내용 입력
- 수정하고픈 변수가 없는 경우 exit 입력 시 수정창 종료

6. 종료(Q)

- 맨처음 while 반복문을 나간다 -> break

```

```

