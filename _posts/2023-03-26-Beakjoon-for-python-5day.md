---
layout: post
toc: true
title: 저작권(평균치 보정)
categories: study
tags: [Python]
author:
  - Kim Dowon
---


## 백준 2914번 저작권

```
A,I = map(int,input().split(" "))

print(A*(I-1)+1)

--> 38 24
--> 875
```

## 문제 해석
앨범에 수록된 곡의 개수: A, 평균값: I, 저작권이 있는 멜로디의 개수: B, `I = B/A` 일때, B를 구하는 문제이다.
그래서 단순히 `B = I*A` 인줄 알았으나, 실상은 그리 단순한 문제는 아니였다.

이 문제에 있어서 함정은 바로 평균값이 반올림 되었다는 사실이었다. 만약에 A가 38고 B가 894라면 I는 23.53이 되고 반올림해서 24가 된다는 것이다.   
그래서 평균값이 주어졌을때 반올림을 고려해서 문제를 풀어야 된다.

반올림된 평균값을 내리는 과정에서 우리는 두가지 경우를 생각해 볼 수 있다.   
1. 소수점이 있는경우 ex) 23.xxxx
2. 소수점이 없이 나누어 떨어지는경우 ex) 24   
두 경우의 수 다 반올림 했을때 24가 나온다.    
   
그렇다고 해서 이 문제에서 2가지 경우를 다 생각해야 되는 것은 아니다.    
문제에서 '적어도' 몇 곡이 저작권이 있는 멜로디인지 구하는것이 목적이기 때문에 멜로디의 수가 최소가 되는 경우를 고려 해야한다.   
따라서 1번 경우만 고려해도 된다.(추가적으로 2번 경우는 최대를 구할때 사용된다고 한다)   
그래서 B=A*(I-1) 이라는 식이 나오는 것이다.   

하지만 코드에서 B = A*(I-1) 의 식에 +1를 하는 모습을 볼 수 있었다. 결론부터 말하자면 이것은 값을 보정하기 위한 과정이다.   
우리는 위에서 반올림된 평균값 I를 내리기 위해서 I-1를 했었다. 또한 우리는 최소값을 구하기 위해서 1번 경우만 고려 한다고 가정했다.    
여기서 우리가 주목 했어야 하는 부분은 바로 `소수점`이다. 2번 경우는 상관 없지만 1번 경우에는 반올림된 수를 내렸을 경우에는 반드시 뒤에 `소수점`이 생긴다. 
하지만 우리는 반올림 하기 전의 소수점이 x.2...인지 x.6...인지 x.8...인지 알 수 없다.    
그렇기 때문에 뒤에 생기는 소수점을 고려해서 답의 정확도를 올리기 위해서 +1를 해준 것이다.(보편적으로 +1을 한다고 한다)