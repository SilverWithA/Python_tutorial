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
