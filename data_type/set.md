# set
python 집합은 `고유한 요소의 모음`으로, 단일 변수에 여러 항목을 저장할 수 있다.\
집합은 다음 특징을 가진다.
* 순서가 없다. (인덱스로 접근할 수 없다.)
* 중복은 허용되지 않는다.
* 요소는 변경 불가능한 자료형만 사용할 수 있다.

## 선언
```py
set_1 = {1,2,3} # 직접 값 할당
set_2 = set([1,2,3,4]) # set()함수를 사용
```
`set()`함수를 사용하는 경우, `list, dictionary, string`의 등의 변경 가능한 자료형으로부터 집합으로 변환할 수 있다.

## 접근
### 인덱스로 접근
집합에는 순서가 존재하지 않으며, 인덱스로 접근하는 경우 오류가 발생한다. \
예시
```py
s = {1,2,3}
for v in s:
    print(v)
```
결과 : TypeError 발생

### in
집합 내부에 특정 요소가 존재하면 True를 반환, 존재하지 않으면 False를 반환한다.
```py
fruits = {"apple", "banana", "cherry"}
print("apple" in fruits) # True
print("grape" in fruits) # False
```

## 요소 추가
### add()
집합에 단일 요소를 추가하는 경우 사용한다.
```py
s = {1,2,3}
s.add(4)
print(s) # {1,2,3,4}
```

### update()
집합에 여러 요소를 추가하는 경우 사용한다.
```py
s = {1,2,3}
s.update([4,5,6])
print(s) # {1,2,3,4,5,6}
```

## 요소 제거
### remove()
집합에서 특정 요소를 제거하는 데 사용한다. 집합 안에 요소가 존재하지 않으면 `KeyError`가 발생한다.
```py
s = {1,2,3}
s.remove(2)
print(s) # {1,3}
```
KeyError가 발생하는 경우
```py
s = {1,2,3}
s.remove(5)
```
### discard()
집합에서 특정 요소를 제거하는 데 사용한다. remove() 와 다른 점은, discard()는 요소가 집합 내에 존재하지 않아도 KeyError를 발생시키지 않는다.
```py
s = {1,2,3,4}
s.discard(5) # KeyError가 발생하지 않으며, 그냥 지나감.
print(s) # {1,2,3,4}
```

### pop()
pop()은 집합에서 임의의 요소를 제거하는 데 사용한다. 다만, 실제로 pop()을 사용해보면 set의 앞에서부터 차례로 제거되는 것을 확인할 수 있는데, 집합은 순서가 없기 때문에 임의의 요소가 제거되는 것이라고 본다.
```py
s = {1,2,3,4}
s.pop()
print(s)
{2,3,4}
```
## 합집합, 교집합, 차집합, 대칭차집합
### 합집합
두 집합의 모든 요소를 포함하는 집합이다. \ 
`union()` 매서드 또는 `|` 연산자를 사용하여 만들 수 있다.
```py
a = {1,2,3,4,5}
b = {4,5,6,7,8}
c = a.union(b)
d = a | b
print(c) # {1,2,3,4,5,6,7,8}
print(d) # {1,2,3,4,5,6,7,8}
```

### 교집합
두 집합의 공통인 요소만을 포함하는 집합이다.\
intersection() 메서드 또는 `&` 연산자를 사용하여 얻을 수 있다.
```py
a = {1,2,3,4,5}
b = {4,5,6,7,8}
c = a.intersection(b)   # intersection()
d = a & b               # & 연산자
print(c) # {4,5}
print(d) # {4,5}
```

### 차집합
한 집합에는 있지만, 다른 집합에는 없는 요소를 포함하는 집합이다. \
difference() 메소드 또는 `-` 연산자를 사용하여 얻을 수 있다.
```py
a = {1,2,3,4,5}
b = {4,5,6,7,8}
c = a.difference(b)
d = a - b
print(c) # {1,2,3}
print(d) # {1,2,3}
```

### 대칭 차집합
공통된 요소만 제외하고 모든 요소를 포함하는 집합이다. \
symmetric_difference() 메서드 또는 `^` 연산자를 사용하여 얻을 수 있다.
```py
a = {1,2,3,4,5}
b = {4,5,6,7,8}
c = a.symmetric_difference(b)
d = a^b
print(c) # {1,2,3,6,7,8}
print(d) # {1,2,3,6,7,8}
```

## 집합의 기타 매서드
### len()
집합의 요소의 수를 len() 매서드를 사용하여 알 수 있다.
```py
s = {1,2,3,4,5}
print(len(s)) # 5
```

### clear()
집합의 모든 요소를 제거하기 위해 clear() 함수를 사용할 수 있다.
```py
s = {1,2,3,4,5}
s.claer()
print(s) # set()
```

### copy()
집합의 얕은 복사본을 만드는 데 copy() 함수를 사용할 수 있다. \
**Note** : 깊은 복사가 아니라 얕은 복사이다.
```py
s = {1,2,3,4,5}
s_copy = s.copy()
print(s_copy) # {1,2,3,4,5}
```

### frozenset()
set() 함수는 `가변 집합`을 생성하며, frozenset() 함수는 `불변 집합`을 생성한다. frozenset()은 불변집합이기 때문에, add() 매서드로 요소를 추가하는 등의 동작을 수행할 시 에러가 발생한다. \
set
```py
s = set([1,2,3,4,5])
s.add(6)
print(s) # {1,2,3,4,5,6}
```
frozenset
```py
frozen_s = frozenset([1,2,3,4,5])
frozen_s.add(6) # AttributeError
```







## Reference
* [파이썬 집합 정리 및 사용](https://ctkim.tistory.com/entry/Python-%EC%9E%85%EB%AC%B8-%EA%B0%95%EC%A2%8C-12-%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EC%A7%91%ED%95%A9Set-%EC%A0%95%EB%A6%AC-%EB%B0%8F-%EC%82%AC%EC%9A%A9%EB%B2%95)
* [파이썬 집합(set) 정리 및 사용법](https://ctkim.tistory.com/entry/Python-%EC%9E%85%EB%AC%B8-%EA%B0%95%EC%A2%8C-12-%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EC%A7%91%ED%95%A9Set-%EC%A0%95%EB%A6%AC-%EB%B0%8F-%EC%82%AC%EC%9A%A9%EB%B2%95)