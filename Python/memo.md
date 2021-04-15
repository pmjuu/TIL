연산 수행 시 자료형 주의하기
```py
print(4/2, type(4/2))     -> 2.0 float
print(4//2, type(4//2))   -> 2 int
```   
### .sort() sorted() 차이점
```py
a = [1,4,3,2]

#a를 바꾼다.
a.sort(reverse=True) #내림차순 정렬
print(a) -> 4,3,2,1 

#a를 바꾸지 않는다.
print(sorted(a)) -> 1,2,3,4 
print(a) -> 4,3,2,1
```
정렬 -> 자료값을 안 바꾼다...
```py
s = '가나다라'

print(s.center(14)) # 가운데 정렬됨
s.rjust(n)          # 우측 정렬
print(s)            # 정렬 안 되어있음
```
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
print(divmod(a, b))    -> (1, 2)
print(*divmod(a, b))   -> 1 2

>>> divmod(3,11)       #몫을 일의자리까지만 출력
(0, 3)
>>> divmod(3.0,11.0)   #float 형식으로 출력해도 마찬가지
(0.0, 3.0)
```
divmod는 작은 숫자를 다룰 때는 a//b, a%b 보다 느리다. 대신, 큰 숫자를 다룰 때는 전자가 후자보다 더 빠르다.   
*packing 참고 [https://wikidocs.net/22801]   
(Q. 패킹은 인자로 받은 여러개의 값을 하나의 객체로 합쳐서 받는건데, 여기서 말하는 '하나의 객체'는 무조건 튜플인가?)   

### 이차원 리스트 뒤집기
`zip()` : Returns an iterator of tuples, where the i-th tuple contains the i-th element from each of the argument sequences or iterables   
*zip 함수에 서로 길이가 다른 리스트가 인자로 들어오는 경우에는 길이가 짧은 쪽 까지만 이터레이션이 이루어진다.
```py
mylist = [1, 2, 3]
new_list = [40, 50, 60]
for i in zip(mylist, new_list):
    print (i)

(1, 40)
(2, 50)
(3, 60)

mylist = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
print(list(zip(*mylist)))
print(list(map(list, zip(*mylist))))

[(1, 4, 7), (2, 5, 8), (3, 6, 9)]    #map() 안 쓰면 tuple원소로 들어간다~
[[1, 4, 7], [2, 5, 8], [3, 6, 9]]
```
### 2차원 리스트를 1차원 리스트로 만들기
```py
my_list = [[1, 2], [3, 4], [5, 6]]

# 방법 1 - sum 함수
answer = sum(my_list, [])

# 방법 2 - itertools.chain
import itertools
list(itertools.chain.from_iterable(my_list))

# 방법 3 - itertools와 unpacking
import itertools
list(itertools.chain(*my_list))

# 방법 4 - list comprehension 이용
[element for array in my_list for element in array]

# 방법 5 - reduce 함수 이용 1
from functools import reduce
list(reduce(lambda x, y: x+y, my_list))

# 방법 6 - reduce 함수 이용 2
from functools import reduce
import operator
list(reduce(operator.add, my_list))
```
[itertools.chain](https://docs.python.org/3/library/itertools.html#itertools.chain)

### itertools.permutations() 순열
```py
import itertools
mylist = [1, 2, 3]
data1 = itertools.permutations(mylist)

print(data1) #값 출력 안 됨
print(type(data1), end='\n\n')

print(sorted(data1)) #list로 자동 형변환 되고? 값 출력 잘 됨
print(type(sorted(data1)), end='\n\n')

print(sorted(map(list, itertools.permutations(mylist)))) #원래 tuple이었던 원소를 list로 바꿔서 2차원 list 만들기

# 결과
# <itertools.permutations object at 0x7f8fa02fc4f0>
# <class 'itertools.permutations'>

# [(1, 2, 3), (1, 3, 2), (2, 1, 3), (2, 3, 1), (3, 1, 2), (3, 2, 1)]
# <class 'list'>

# [[1, 2, 3], [1, 3, 2], [2, 1, 3], [2, 3, 1], [3, 1, 2], [3, 2, 1]]
```
