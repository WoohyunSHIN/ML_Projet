// Reference Book : [점프 투 파이썬](https://wikidocs.net/book/1)

// Written by WoohyunSHIN. I reconstitute the reference book as my style for studying. If you have question or I commit an infrigement of copyright, send me a mail <swh159@gmail.com> please thank you.

# Python

***

###변수 표기법이란 ?

파이썬에서는 2가지 변수 표기법이 존재한다. 카멜표기법과 스네이크표기법 두가지가 존재한다.  

1. 카멜표기법은 대문자와 소문자로 구분을 한다.

   typeName

2. 스네이크표기법은 언더바 (_)로 구분을 한다

   type_name

***

## 2. 제어문

> 파이썬에서 if, while, for 등 제어문을 여기서 부터 다룰 것이다.

### 2.1. if문

> 조건문에서 테스트를하여 그 값이 참(True)이면 if문 바로 다음 문장을 수행하고, 조건문이 거짓(False)이면  else문 다음의 문장을 수행한다. 또한 **들여쓰기** 와 조건문 뒤에 **:** 가 무엇보다 중요하다. 아래의 예를 보자.

```python
# 실행가능
>>> if 조건문:
>>> 	수행할 문장 1
>>> 	수행할 문장 2
>>> 	수행할 문장 3
	
# 오류 1
>>> if 조건문:
>>> 	수행할 문장 1
>>> 수행할 문장 2
>>> 	수행할 문장 3

# 오류 2
>>> if 조건문:
>>> 	수행할 문장 1
>>> 		수행할 문장 2
>>> 	수행할 문장 3
```



> **조건문이란 ?**
>
> 참과 거짓을 판단하는 문장을 말한다.

