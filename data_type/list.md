# List

## 초기화와 접근
### 초기화
`[]` 안에 요소를 넣어서 초기화한다.
```py
intList = [1, 2, 3, 4, 5]
strList = ["reakwon", "tistory", "com"]
```

### 접근
index를 사용하여 접근하며, 가장 첫번째 원소의 index는 0번부터 시작한다. 이때, 마지막 원소는 -1, 마지막에서 두번째 원소는 -2 이렇게 뒤에서부터 n번째의 원소를 -n으로 접근할 수도 있다.
```py
intList = [1, 2, 3, 4, 5]
strList = ["reakwon", "tistory", "com"]
print (intList[0], intList[1], intList[-1], intList[-2])
print (strList[0], strList[-1])

#strList 마지막의 원소 값 변경
strList[2] = 'COM'
print (strList)
```
출력
```
1 2 5 4
reakwon com
['reakwon', 'tistory', 'COM']
```

## 슬라이싱
특정 index i부터 (j-1) 까지의 원소에 접근하고 싶은 경우, `:`을 사용할 수 있다. \
이때,
* `:`의 앞을 지정하지 않으면 0번부터 시작
* `:`의 뒤를 지정하지 않으면 리스트의 끝까지 \
를 의미한다.

```py
intList = [1, 2, 3, 4, 5]
strList = ["reakwon", "tistory", "com"]

print (intList[1:2])    #1번 원소부터 2번 원소 전까지
print (strList[1:])     #1번 원소부터 끝까지

# [1, 2, 3, 4, 5] 의 1번 인덱스부터 3-1=2번 index까지 값을 변경
intList[1:3] = [12, 13]
print(intList)
```
출력
```
[2]
['tistory', 'com']
[1, 12, 13, 4, 5]
```

## 삭제
특정 원소를 리스트에서 삭제하고 싶으면 `del`함수를 사용하면 된다. index를 사용하여 원소를 삭제하며, 해당 자리가 없어지므로 뒤에 원소들이 앞으로 당겨서 채워진다고 보면 된다. 이때, 슬라이싱으로 한꺼번에 리스트 원소를 삭제할 수도 있다.
```py
intList = [1, 2, 3, 4, 5]
strList = ["reakwon", "tistory", "com"]

del intList[:3]	# 3번 인덱스 이전까지 원소 모두 삭제
del strList[2]	# 2번 인덱스 원소 삭제

print(intList)
print(strList)
```
출력
```
[4, 5]
['reakwon', 'tistory']
```

## 다중 리스트
리스트 안에 리스트가 포함되는 `다중 리스트`에서는 `[i][j]` 의 형태와 같이 인덱스를 이용해 연속으로 접근하면 된다.
```py
intList = [1, 2, 3, 4, 5]
        # [0][1][2][3][4]
mergedList = ["reakwon", "tistory", "com",intList]
            #   [0]         [1]      [2]    [3]

print(mergedList[0], mergedList[1], mergedList[2], mergedList[3][0], mergedList[3][1], mergedList[-1][-1])
```
출력
```
reakwon tistory com 1 2 5
```
## 리스트의 반복
리스트를 반복하고 싶은 경우, * 연산자를 사용하면 된다.
### 예시 1
```py
ls = ['-','=']
repeat = ls * 5
print (repeat)
```
출력
```
['-', '=', '-', '=', '-', '=', '-', '=', '-', '=']
```
### 예시 2
```py
a = [0]*5
print(a)
```
출력
```
[0,0,0,0,0]
```
### 예시 3
번외이지만, 실질적으로 많이 쓰는 예시라서 함께 적어본다.
```py
a = [[0] for _ in range(5)]
b = [[1]*3 for _ in range(5)]
print(a)
print(b)
```
출력
```
[[0], [0], [0], [0], [0]]
[[1, 1, 1], [1, 1, 1], [1, 1, 1], [1, 1, 1], [1, 1, 1]]
```

## 리스트 내장함수
### len
리스트의 내장함수는 아니지만, 리스트 길이를 구하고 싶을 때는 `len`함수를 사용하면 된다.
```py
numbers = [5, 2, 3, 5, 6, 7, 1, 1, 1]   #9개 원소

print ("numbers 길이 : ", len(numbers))
```
출력
```
numbers 길이 :  9
```
### sort
list는 `sort`함수를 사용하여 원소를 정렬할 수 있다. 이때, list 내의 원소는 모두 같은 자료형이어야 한다.\
기본 정렬 순서
* 숫자 : 오름차순
* 문자열 : 사전순(대문자가 소문자보다 먼저이다.)
```py
numbers = [5, 2, 3, 5, 6, 7, 1, 1, 1]
strs = ['apple', 'computer', 'python', 'list', 'C++','Java', 'banana']

numbers.sort()  #정수 정렬
strs.sort()     #문자열 정렬

print(numbers)
print(strs)
```
출력
```
[1, 1, 1, 2, 3, 5, 5, 6, 7]
['C++', 'Java', 'apple', 'banana', 'computer', 'list', 'python']
```
### reverse
list의 순서를 거꾸로 저장하고 싶으면 `reverse`를 사용하면 된다. \
**Note** : 순서를 거꾸로 하는 것이므로, 내림차순 정렬하고 싶으면 `sort`를 먼저 사용한 후, `reverse`를 사용해야 한다.

```py
numbers = [5, 2, 3, 5, 6, 7, 1, 1, 1]

numbers.sort()  #정수 정렬
numbers.reverse()   #거꾸로 뒤집은 리스트

print(numbers)
```
출력
```
[7, 6, 5, 5, 3, 2, 1, 1, 1]
```

### count
list에 찾는 값이 몇개 있는지 `count`함수로 알 수 있다.
```py
numbers = [30, 19, 100, 34, 123, 51, 0, 0, -1]
strings = ['java', 'python', 'programming', 'algorithm', 'null', 'null']

print ('0은 몇개? :', numbers.count(0))
print ('null은 몇개? :', strings.count('null'))
```
Result
```
0은 몇개? : 2
null은 몇개? : 2
```
### append
list의 마지막에 요소를 추가한다.
```py
ls = ['hello','world']

ls.append('!!')
ls.append('This')
ls.append('is')
ls.append('python')
print (ls)
```
Result
```
['hello', 'world', '!!', 'This', 'is', 'python']
```

### extend
기존의 list에 다른 list 원소를 이어서 붙이고 싶으면 `extend`를 사용하면 된다. 이때, `+`를 사용하는 것과 같은 결과가 된다.
```py
animals = ['dog', 'cat', 'orca']
animals.extend(['monkey','elephant'])
print(animals)
animals+=['flower','hi']
print(animals)
```

Result
```
['dog', 'cat', 'orca', 'monkey', 'elephant']
['dog', 'cat', 'orca', 'monkey', 'elephant', 'flower', 'hi']
```

### insert
중간 어느 지점에 원소를 삽입하려면 insert 함수를 사용하면 된다.
```py
www = ['world','web']

www.insert(1,'wide')    # 1번째에 'wide' 원소 추가
print(www)
```
Result
```
['world', 'wide', 'web']
```

### remove
원소를 삭제하려면 `remove`를 사용할 수 있다. 이때, `del`은 index를 사용하지만, `remove`는 원소를 매개변수로 사용한다. 단, 특정 값의 여러개 존재하여도, 한 번의 remove는 하나의 값(가장 앞에 있는 값)만 삭제한다.
```py
countries = ['korea','japan','china','US','china','UK','france','vietnam']

countries.remove('japan')
countries.remove('china')

print(countries)
```
Result
```
['korea', 'US', 'china', 'UK', 'france', 'vietnam']
```

### clear
리스트의 내용을 전부 삭제하고 싶으면 clear함수를 사용하면 된다.
```py
www = ['world','web']

www.clear() #del www[:]와도 같은 동작

print (www)
```
Result
```
[]
```

### pop
pop은 원소를 가져와 반환한 후에 리스트에서 삭제한다. 인자를 넘겨주지 않으면 자동으로 마지막 원소를 가져오며, index를 인자로 넘겨주면 해당 index의 원소를 꺼낸다.
```py
countries = ['korea','japan','US','UK','france','vietnam', 'china']

countries.pop()     #마지막 원소 삭제
countries.pop(1)    #1번 원소 삭제

print(countries)
```
Result
```
['korea', 'US', 'UK', 'france', 'vietnam']
```
### index
특정 값(원소)이 어느 인덱스에 저장되어 있는지 확인하는 경우 `index`를 사용하면 된다. 가장 첫번째 값을 찾아주며, 이후에 다른 인자가 주어지지 않으면 전체 list 범위에서 찾는다. index 이후에 탐색을 하는 `시작 인덱스`,`끝 인덱스`를 주어지면 해당 범위에서만 찾는다. 또한, 찾으려는 원소가 범위 내에 없으면 에러를 낸다.
```py
languages = ['C++', 'Java', 'Python', 'C', 'C#', 'Kotlin']

print (languages.index('C++'))
print (languages.index('Kotlin',0,4))
```
Result
```
0
Traceback (most recent call last):
  File "c:/Users/chpark/Workspace/python_study/practice/list1.py", line 4, in <module>
    print (languages.index('Kotlin',0,4))
ValueError: 'Kotlin' is not in list
```




## Reference
* [List 자료형](https://reakwon.tistory.com/170)