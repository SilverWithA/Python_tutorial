## < 파이썬 기초 문법 >

* #### list = [ ]
* #### tuple= ()
* #### set= {}
* #### dictionary = {"key":"value"} # - JSON에서 쓰임

### 1. 리스트: list


```python
list1 = [1,2,3,4]
type(list1)
```

    <class 'list'>
    


```python
list1.append(5) # 끝에 element 추가
print(list1)
```

    [1, 2, 3, 4, 5]
    


```python
list1.insert(0,1) # list1의 index 0 자리에 element 1 추가
print(list1)
```

    [1, 1, 2, 3, 4, 5]
    


```python
another_list= [8,55]
list1.extend(another_list) # 맨 끝에 리스트 병합하여 추가
print(list1)
```

    [1, 1, 2, 3, 4, 5, 8, 55]
    


```python
list1.remove(55) # element 55를 찾아 삭제 
print(list1)

list1.pop() #맨 마지막 항목 삭제
print(list1)
```

    [1, 1, 2, 3, 4, 5, 8]
    [1, 1, 2, 3, 4, 5]
    


```python
print(f"{list1.index(2)}) # 2에 해당하는 element의 위치 출력
print(list1.count(2)) # 2에 해당 element가 출현 빈도 출력

list1.reverse() # elements 역순으로 바꿔줌.
print(list1)
```

    2
    1
    [5, 4, 3, 2, 1, 1]
    


```python
# 오름차순 및 내림차순 정리
# 따로 다시 list1 = list.sort() 형태로 쓰지 않아도 됨.

list1 = [5,6,1,8,7,3,1,9]
list1.sort() # 오름차순
print(list1)
list1.sort(reverse=True) # 내림차순
print(list1)
```

    [1, 1, 3, 5, 6, 7, 8, 9]
    [9, 8, 7, 6, 5, 3, 1, 1]
    

* ### list slicing
#### list1[start : end : step] -> end는 포함하지 않는다


```python
# list의 elements로는 다양한 자료형이 올 수 있다.
list1 = [1,2,3,"a","b", [35,55],"a",True]

list1[5][1] # 55 인덱싱하기 # nesting list indexing

print(list1[:-2]) # 시작부터 끝에 2개 전까지

print(list1[3::-1]) # 인덱스 3번째부터 역순으로
```

    [1, 2, 3, 'a', 'b', [35, 55]]
    ['a', 3, 2, 1]
    


```python
# slicing
# 짝수만 출력하라
nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
nums[1::2] #2번째 element부터 2칸씩 띄워서 slicing
```




    [2, 4, 6, 8, 10]



* ### 리스트 내포(List comprehension)
#### 형식: [표현식 for 항목 in 반복가능객체 if 조건문]


```python
x = [1,2,3,4]
list1= [i ** 2 for i in x]

list1   # x의 elements의 각 제곱값
```




    [1, 4, 9, 16]



##### # a의 짝수 elements만 추출하는 내포식


```python
a = [1,2,3,4,5,6,7,8,9]

list2 = [x for x in a if x%2==0]
list2
```




    [2, 4, 6, 8]



##### 1000이하의 3의 배수와 5의 배수의 총합


```python
a = [x for x in range(20) if x%3==0 or x%5==0] # or 로 중복값 처리
sum(a)
```




    78



* ### list 원소 스캔
#### Do it 자료구조 파이썬 실습 2C-1 참고


```python
x = ['A','B','C','D','E']

for i in range(len(x)):
    print(x[i])
```

    A
    B
    C
    D
    E
    


```python
# enumerate()활용
# enmerate는 element와 그 index를 동시에 반환하는 함수
# 해당 for문에서 i에는 index, name에는 각 element가 할당된다

for i, name in enumerate(x):
    print(f"x[{i}]= {name}")
```

    x[0]= A
    x[1]= B
    x[2]= C
    x[3]= D
    x[4]= E
    

### 2. 문자열:str

* #### 공백 제거: strip()
* #### 출현 빈도: count()
* #### 위치: index()
* #### 단어 분리: split()
* #### 문자열 수정: replace()
#### ㄴ 문자열은 list형처럼 slicing 불가능
* #### 합치기: "구분자".join(문자열변수)


```python
str1 = ' StRinG'
a =  str1.swapcase() # 대문자 to 소, 소 to 대
print(f"str1.swapcase() 실행 결과:{a}")
print()

str1 = str1.strip() # 공백제거 lstrip, rstlip도 존재


b = str1.count("i")  #str1안에 i라는 문자가 몇 개나 존재하는지 출력
print(f"문자 i는 {b}번 출현한다.")
print()

c = str1.find("i") # f가 존재하는 index 반환
print(f"i는 {c}번째 index에 존재한다")
print()
# str.rfind() 그냥 find는 왼쪽부터 찾지만 rfind()는 문자열의 오른쪽부터 찾음

str2 = "Hello World"
d= str2.split(' ')
print(f"스페이스를 기준으로 단어 분리: {d}")
print()

e = str2.replace("Hello","Hot dog")
print(f"수정 전: {str2} -> 수정 후: {e}")

"".join(str2) # - 변수 속에 있는 문자열을 구분자없이("") 합치는 code
"/".join(str2) # - 문자열을 /로 구분하여 합치기
```

    str1.swapcase() 실행 결과: sTrINg
    
    문자 i는 1번 출현한다.
    
    i는 3번째 index에 존재한다
    
    스페이스를 기준으로 단어 분리: ['Hello', 'World']
    
    수정 전: Hello World -> 수정 후: Hot dog World
    H e l l o   W o r l d
    




    'H/e/l/l/o/ /W/o/r/l/d'




```python
str = 'hello'
str.capitalize() # 맨 앞 문자만 대문자 변환
```




    'Hello'




```python
str.endswith("o")
# str 문자열이 ~로 끝나는지 T/F로 출력
# str.startswith("2020")
```




    False



### 3. print formatting

####  %d : 정수형 , %r : 문자열, %f : 실수형
#### %r: 객체 표현 (Object Representation)으로 출력해준다.
#### https://devday.tistory.com/entry/%ED%8C%8C%EC%9D%B4%EC%8D%AC-Python-s-vs-r


```python
name1 = "김민수"
age1 = 10
name2 = "이철희"
age2 = 13
print("이름:%s 나이:%d" %(name1, age1))
print("이름:%s 나이:%d" %(name2, age2))
```

    이름:김민수 나이:10
    이름:이철희 나이:13
    


```python
# 2. format() 매서드 이용

print("이름:{0} 나이:{1}".format(name1,age1))
print("이름:{0} 나이:{1}".format(name2,age2))


# print("첫번째 format{0}, 두번째 format{1}".format(변수1, 변수2))
```

    이름:김민수 나이:10
    이름:이철희 나이:13
    


```python
# 3. f-string 이용


print(f"이름:{name1} 나이:{age1}")
print(f"이름:{name2} 나이:{age2}")
```

    이름:김민수 나이:10
    이름:이철희 나이:13
    

### 3. 집합: set
* #### set = {} 이란? - 집합의 개념
#### 중복되는 elements를 한번만 출력
#### 순서가 없다.


```python
set1 = {1,2,3,4,4,4,4,4,5}
set2 = {1,2,5}

print(f"두 집합의 교집합은? :{set1 & set2}")
print(f"교집합 구하기: set1.intersection(set2): {set1.intersection(set2)}")
print()
print(f"두 집합의 합집합은? :{set1 | set2}")
print(f"합집합 구하기: set1.union(set2): {set1.union(set2)}")
```

    두 집합의 교집합은? :{1, 2, 5}
    교집합 구하기: set1.intersection(set2): {1, 2, 5}
    
    두 집합의 합집합은? :{1, 2, 3, 4, 5}
    합집합 구하기: set1.union(set2): {1, 2, 3, 4, 5}
    

### 4. bool 자료형 - True/False
* #### 빈 컨테이너는 Flase로 처리함


```python
a = [1,2,3,4]
while a:
    print(a.pop())
    
# 이처럼 a의 원소가 더이상 없다면 while문의 조건문이 False가 된다
# 이때 a는 빈 리스트이다. a = [] 상태
```

    4
    3
    2
    1
    

### 5. 딕셔너리: dictionary
* #### dict1 = {} 형태


```python
dict1 = {
    "이름":"Sliver A",
    "나이":"50"
}

# key와 value 따로 출력

for r,s in dict1.items():
    print(f"key:{r}, value:{s}") #key와 value 쌍으로 출력
    
```

    key:이름, value:Sliver A
    key:나이, value:50
    


```python
# 생성하는 방법

아이스크림1 = {"메로나": 500, "구구콘": 1000}
아이스크림2 = dict(메로나=500, 구구콘=1000)
아이스크림3 = dict([("메로나", 500), ("구구콘", 1000)])
```


```python
# 삭제하기

del dict1['나이'] # key2에 해당하는 value와 key값 삭제
dict1
```




    {'이름': 'Sliver A'}



* #### list를 dictionary로 만들기: zip(), dict() 사용


```python
name = ['merona', 'gugucon']
price = [500, 1000]

icecream = dict(zip(name, price))
print(icecream)
```

    {'merona': 500, 'gugucon': 1000}
    

* #### * Tuple unpacking and Asterisk


```python
a, b, *c = (0, 1, 2, 3, 4, 5)
print(a)
print(b)
print(c)
```

    0
    1
    [2, 3, 4, 5]
    

### (+) 알고리즘 복습
#### Do it 파이썬 자료구조 참고
#### (1)  소수나열하기 


```python
# 1 ~ 1000까지 소수 나열하기

counter = 0
prime = []
for i in range(2,1001):
    for j in range(2,i):
        counter += 1
        if i % j == 0:   # 나누어 떨어지면 소수가 아님
            break
    else:
        prime.append(i)
            
            
print(prime[:10])
print(counter)  # 78,022 횟수
# 소수가 중복으로 append되는 오류 발생 - else를 for문과 동일한 들여쓰기 위치로 이동하면 해결
# 나눗셈 연산이 불필요하게 많음
```

    [2, 3, 5, 7, 11, 13, 17, 19, 23, 29]
    78022
    


```python
# prime2:알고리즘 개선1  - 짝수 제외

counter = 0
ptr = 0
prime = [None] * 500

prime[ptr] = 2 # 첫번째 소수 2를 초깃값으로 지정
ptr += 1


for n in range(3,1001,2):
    for i in range(1,ptr):
        counter += 1
        if n % prime[i] == 0:
            break
    else:
        prime[ptr] = n
        ptr += 1
            
print(prime[:10])
print(f"나눗셈을 실행한 횟수:{counter}")
```

    [2, 3, 5, 7, 11, 13, 17, 19, 23, 29]
    나눗셈을 실행한 횟수:14622
    

* #### 위의 코드 for문에서 n=3일때 궁금증
#### Q. n=3일때 prime[1]은 None인데 왜 에러가 안날까? 
#### A. range(1,1)에서는 범위가 없음. for문이 실행되지 않음


```python
for i in range(1,1):
    print(i) # 어떤 숫자고 출력되지 않음
```


```python
#prime3: 약수의 대칭성 이용

# 약수의 대칭성: 모든 자연수의 약수는 중앙값을 기준으로 대칭을 이룬다.
# 중앙값 이전의 약수가 존재한다면 중앙값 이후에도 대칭을 이루는 자연수가 존재함
# 따라서 중앙값(제곱근)을 기준으로 그보다 작은 수들만 확인해주면 된다.


counter = 0
ptr = 0
prime = [None] * 8

prime[ptr] = 2
ptr += 1

prime[ptr]= 3
ptr += 1





for n in range(5,20,2):
    i= 1
    while prime[i]*prime[i] <= n:  # 
        counter += 2
        if n % prime[i]==0:  # 소수가 아님
            break       # while문 중단하고 for문으로 올라감
        i+=1            # if문 break에 걸리지 않았을 때 실행
    else:
        prime[ptr] = n    # while문에 해당 안되는 경우 - 소수로 판단
        ptr += 1
        counter+=1

     
prime[::]
```




    [2, 3, 5, 7, 11, 13, 17, 19]



* #### (2) 선형 검색 구현하기


```python
# 실습 3-15

from typing import Sequence, Any

def seq_search(a:Sequence, key:Any) -> int:
    """시퀀스 a에서 key값이 같은 원소를 선형검색 while문 """
    i = 0
    
    
    while True:
        if i == len(a):
            return -1
        if a[i] == key:
            return i 
        i += 1   # else 걸어주면 안됨
        

if __name__ =='__main__':
    num = int(input("원소의 개수를 입력해주세요: "))
    x = [None] * num
    
    for i in range(num):
        x[i] = int(input(f"x[{i}]:"))
        
    ky = int(input("검색할 값을 입력하세요."))
    
    idx = seq_search(x, ky)
    
    
    # seq_search()의 반환값은 i이거나 -1이므로
    # 조건을 걸때 -1을 기준으로 세우는 게 좋다
    if idx == - 1:
        print("검색값을 갖는 원소가 존재하지 않습니다.")
    else:
        print(f"검색값은 x[{idx}]에 있습니다.")
```

    원소의 개수를 입력해주세요: 1
    x[0]:2
    검색할 값을 입력하세요.3
    검색값을 갖는 원소가 존재하지 않습니다.
    


```python
def seq_search(a:Sequence,key:Any)-> int:
    """시퀀스 a에서 key값이 같은 요소를 선형검색 for문"""
    
    
    for i in range(len(a)):
        if a[i] == key:
            return i
    return -1


if __name__ == '__main__':
    num = int(input('원소 수를 입력하세요.: '))  # num 값을 입력
    x = [None] * num                           # 원소 수가 num인 배열을 생성

    for i in range(num):
        x[i] = int(input(f'x[{i}]: '))

    ky = int(input('검색할 값을 입력하세요.: '))  # 검색할 키 ky를 입력받음

    idx = seq_search(x, ky)                     # ky와 값이 같은 요소를 x에서 검색

    if idx == -1:
        print('검색 값을 갖는 요소가 존재하지 않습니다.')
    else:
        print(f'검색 값은 x[{idx}]에 있습니다.')
```

    원소 수를 입력하세요.: 1
    x[0]: 2
    검색할 값을 입력하세요.: 3
    검색 값을 갖는 요소가 존재하지 않습니다.
    

#### (2) 선형 검색과 보초법


```python
# 실습 3-1(while)을 보초법으로 수정


import copy
def seq_search(seq: Sequence, key:Any)-> int:
    """시퀀스 seq에서 key와 일치하는 원소을 선형검색"""    
    
    a = copy.deepcopy(seq) # deepcopy는 수정되어도 서로 영향을 미치지 않는 방법임
    a.append(key)   # 보초 추가

    i = 0
    while True:
        if a[i] == key:
            break
        i += 1
    return -1 if i == len(seq) else i
```

#### (3) 이진 알고리즘 bin_search 문제


```python
from typing import Any,Sequence

def bin_search(a:Sequence,key:Any)-> int:
    """시퀀스 a에서 key와 일치하는 원소를 이진 검색/인덱스 반환"""
    pl = 0
    pr = len(a) -1
    
    print('   |', end='')
    for i in range(len(a)):
        print(f'{i : 4}', end='')   # {i : 4}에서 4는 배치 간격
    print()
    print('---+' + (4 * len(a) + 2) * '-')
    
    
    while True:
        pc = (pl+pr)// 2
        
        print('   |', end='')
        if pl != pc:         # pl 원소 위에 <-를 출력
            print((pl * 4 + 1) * ' ' + '<-' + ((pc - pl) * 4) * ' ' + '+', end='')
        else: 
            print((pc * 4 + 1) * ' ' + '<+', end='')
        if pc != pr:         # pr 원소 위에 ->를 출력
            print(((pr - pc) * 4 - 2) * ' ' + '->')
        else:
            print('->')
        print(f'{pc:3}|', end='')
        
        for i in range(len(a)):
            print(f'{a[i]:4}', end='') 
        print('\n   |')
        
        
        if a[pc] == key:
            return pc
        elif a[pc] < key:
            pl = pc + 1
        else:
            pr = pc - 1 
        if pl > pr:   #검색범위 존재하지 않음
            break
    return -1




if __name__ == '__main__':
    num = int(input('원소 수를 입력하세요.: '))
    x = [None] * num  # 원소 수가 num인 배열을 생성

    print('배열 데이터를 오름차순으로 입력하세요.')

    x[0] = int(input('x[0]: '))

    for i in range(1, num):
        while True:
            x[i] = int(input(f'x[{i}]: '))
            if x[i] >= x[i - 1]:
                 break

    ky = int(input('검색할 값을 입력하세요.: '))  # 검색할 ky를 입력

    idx = bin_search(x, ky)                     # ky와 같은 값의 원소를 x에서 검색

    if idx == -1:
        print('검색값을 갖는 원소가 존재하지 않습니다.')
    else:
        print(f'검색값은 x[{idx}]에 있습니다.')
```

    원소 수를 입력하세요.: 10
    배열 데이터를 오름차순으로 입력하세요.
    x[0]: 1
    x[1]: 2
    x[2]: 3
    x[3]: 4
    x[4]: 5
    x[5]: 6
    x[6]: 7
    x[7]: 8
    x[8]: 9
    x[9]: 10
    검색할 값을 입력하세요.: 5
       |   0   1   2   3   4   5   6   7   8   9
    ---+------------------------------------------
       | <-                +                  ->
      4|   1   2   3   4   5   6   7   8   9  10
       |
    검색값은 x[4]에 있습니다.
    

#####  print() 출력 간격 사용법


```python
for i in range(5):
    print(f'{i : 4}', end='')
    
print()
for i in range(5):
    print(f'{i : 6}', end='')
print()    
for i in range(5):
    print(f'{i : 8}', end='')
```

       0   1   2   3   4
         0     1     2     3     4
           0       1       2       3       4