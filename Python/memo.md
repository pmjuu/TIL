``` py
data = [1, 9, 2, 3]
print(data)
print(data[::-1]) #반대순서로 출력
```
[1, 9, 2, 3]   
[3, 2, 9, 1]

## 프로그래머스 강의 '파이썬을 파이썬 답게'
정수를 담은 이차원 리스트, mylist 가 solution 함수의 파라미터로 주어집니다.   
mylist에 들은 각 원소의 길이를 담은 리스트를 리턴하도록 solution 함수를 작성해주세요.

제한 조건> mylist의 길이는 100 이하인 자연수입니다. mylist 각 원소의 길이는 100 이하인 자연수입니다.

예시   
input	                   output   
[[1], [2]]	          -> [1,1]   
[[1, 2], [3, 4], [5]]	-> [2,2,1]   

``` py
def solution(mylist):
    answer = []
    for data in mylist:
        answer.append(len(data))
    return answer

def solution(mylist):
    return list(map(len, mylist))  #map()을 list()로 묶어줘야 list로 출력됨.
```

### divmod(x,y)
두 숫자를 인자로 전달 받아 첫번째 인자를 두번째 인자로 나눈 몫과 나머지를 tuple 형식으로 반환한다.   

출처: https://technote.kr/259 [TechNote.kr]
``` py
a = 7
b = 5
print(a//b, a%b)       -> 1 2
print(*divmod(a, b))   -> (1, 2)

>>> divmod(3,11)       #몫을 일의자리까지만 출력
(0, 3)
>>> divmod(3.0,11.0)   #float 형식으로 출력을해도 마찬가지
(0.0, 3.0)
```
divmod는 작은 숫자를 다룰 때는 a//b, a%b 보다 느리다. 대신, 큰 숫자를 다룰 때는 전자가 후자보다 더 빠르다.   
*packing 참고 [https://wikidocs.net/22801]
