---
layout: post
toc: true
title: 사칙연산
categories: study
tags: [Python]
author:
  - Kim Dowon
---

백준을 통해 파이썬을 공부해 보려고 한다.

## 백준 1000번 A+B

```
a, b = map(int, input().split())

print(a+b)
```

'+' 연산자를 사용해서 정수 a, b를 더하는 코드 이다.

## 백준 1001번 A-B

```
a, b = map(int, input().split())

print(a-b)
```
'-' 연산자를 사용해서 정수 a, b를 빼는 코드 이다.

## 백준 10998번 AxB

```
a, b = map(int, input().split())

print(a*b)
```

'*' 연산자를 사용해서 정수 a, b를 곱하는 코드 이다.

## 백준 10869번 사칙연산

```
a, b = map(int, input().split())

print(a+b)
print(a-b)
print(a*b)
print(a//b)
print(a%b) 
```

앞서 썼던 연산자들을 이용해서 사칙연산을 하는 코드이다.
추가 적으로 '//' 와 '%' 각각 몫과 나머지를 계산하는 연산자 이다.

## 문제 해석

파이썬은 기본적으로 이런식으로 값을 받을 수 있다.
```
a = int(input())
```
input() 함수는 기본적으로 문자열(str)을 리턴한다. 그래서 우리가 원하는 값을 얻기 위해선 int 형으로 바꾸는 과정이 필요하다.
하지만 위에 문제 처럼 변수가 하나 거나 두개정도면 일일이 int 형으로 바꾸는 것은 문제가 안 된다. 진짜 문제가 되는 상황은 바꿔야 하는 변수가 여러개일 경우 일 것이다.

### map
이때 우리가 사용할 수 있는 함수는 map 함수이다. 예를 들어 4개의 실수로 구성된 리스트를 정수로 바꾸야 한다면 우리는 for 문을 이용해서 일일이 int 형으로 바꿔줘야 한다.

```
 a = [1.2, 2.5, 3.7, 4.6]
 for i in range(len(a)):
     a[i] = int(a[i])
```

하지만 map 함수를 이용하면 코드 한줄로도 충분히 수행이 가능하다.

```
a = list(map(int, a))
```

이처럼 map 함수를 이용하면 iterable 한 객체(예를 들어 리스트)를 코드 한 줄로 원하는 자료형으로 바꿀 수 있으며, 코드 수행 시간 또한 단축 시킬 수 있다.

### split()
문제를 풀기 위해선 a, b를 띄어쓰기를 기준으로 입력 받아야 한다. 또한 입력 받은 숫자를 a, b 변수에 각각 넣는 과정이 필요하다. 이 과정을 더욱 용이 하게 바꾸는 함수가 split() 이다.
split() 함수를 이용해 괄호 안에 있는 문자를 기준으로 문자열을 나눌 수 있다.
예를 들어

```
s = "a b c d e f g"
print(f's         : {s}')
 
r = s.split()
print(f's.split() : {r}')

--> s       : a b c d e f g
--> s.split : ['a', 'b', 'c', 'd', 'e', 'f', 'g']
```

