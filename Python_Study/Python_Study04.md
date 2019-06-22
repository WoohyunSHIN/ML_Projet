

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

