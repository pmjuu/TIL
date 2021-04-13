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
