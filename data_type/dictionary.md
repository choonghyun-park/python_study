# Dictionary
키와 값의 쌍으로 구성된 자료 구조이다. 키는 유일해야 하며, 값은 중복을 허용한다. 
### Dictionary의 특징
* 순서가 존재하지 않는다.
* 키와 값의 쌍으로 구성된 자료 구조로 순서가 없다.
* 요소에 접근할 때는 키를 사용한다.
* 많은 양의 데이터를 효율적으로 저장하기에 적합하다.

## 생성
`{}` 괄호를 사용하여 생성할 수 있다.
```py
person = {'name':'Choonghyun','age':25,'city':'Seoul'}
number = {1:'one',2:'two',3:'three'}
```
또한, `dict()` 함수를 사용하여 생성할 수 있다.
```py
person = dict(name="Choonghyun",age=25,city='Seoul')
print(person) # {'name':'Choonghyun','age':25,'city':Seoul}
```
사소한 차이가 있다면, dict 변수 내에서 name='' 이런식으로 매개변수를 통해 값을 넘겨주었다. 즉, {}를 이용한 선언처럼 'name'='' 이런식으로 string으로 넘겨주지 않은 점을 기억하자. 별건 아니지만, 헷갈릴 수 있기 때문.

### zip
zip() 함수는 여러 개의 리스트를 같은 위치에 있는 요소끼리 묶어서 `튜플의 리스트`를 생성하는 함수이다. \
zip() 함수를 사용하여 리스트 -> 튜플((키,값)의 형태로 되어있는)로 변환하고, 이것을 dict() 함수를 사용해 딕셔너리로 바꿔줄 수 있다.
```py
keys = ['name','age','city']
values = ['Choonghyun',25,'Seoul']
person = dict(zip(keys,values))
print(person) # {'name':'Choonghyun','age':25,'city':'Seoul'}
``` 

## 요소 추가
요소를 추가할 때는 `딕셔너리이름[key]=value`의 문법을 사용한다.
```py
person = {'name':'Choonghyun','age':25,'city':Seoul}
person['gender']='Male'
print(person) # {'name':'Choonghyun','age':25,'city':'Seoul','gender':'Male'}
```

## 요소 변경
기존의 요소의 값을 변경할 때도 추가와 같이 `딕셔너리이름[key]=value`의 문법을 사용한다.
```py
person = {'name':'Choonghyun','age':25,'city':Seoul}
person['city']='Suwon'
print(person) # {'name':'Choonghyun','age':25,'city':'Suwon'}
```

## 요소 접근
### key를 사용하여 접근
딕셔너리는 key를 사용하여 값에 접근할 수 있다. \
```py
person = {'name':'Choonghyun','age':25,'city':'Seoul'}
print(person['name']) # 'Choonghyun'
```

### get()
get()을 사용하여 딕셔너리의 값에 접근할 수 있으며, 요소가 없을 경우 None을 반환한다. 해당 요소가 없을 경우, None을 반환한다.
```py
person = {'name':'Choonghyun','age':25,'city':'Seoul'}
print(person.get('name')) # 'Choonghyun'
```

## 요소 제거
### pop()
pop() 메서드를 사용하여 딕셔너리의 요소를 제거할 수 있으며, pop()을 사용하는 경우 제거된 요소의 값을 반환한다.
```py
person = {'name':'Choonghyun','age':25,'city':'Seoul'}
person.pop('name')
print(person) # {'age':25,'city':'Seoul'}
```

### del
del 구문을 사용하여 딕셔너리 요소를 제거할 수 있다. 문법은 `del 딕셔너리이름[key]` 이다.
```py
person = {'name':'Choonghyun','age':25,'city':'Seoul'}
del person['age'] # {'name':'Choonghyun','city':'Seoul'}
```

### clear
clear() 매서드로 딕셔너리 모든 요소를 제거할 수 있다.
```py
person = {'name':'Choonghyun','age':25,'city':'Seoul'}
person.clear()
print(person) # {}
```

## 기타 딕셔너리 매서드
### keys()
keys() 매서드를 사용하여 딕셔너리 키만을 가져올 수 있다.
```py
person = {'name':'Choonghyun','age':25,'city':'Seoul'}
print(person.keys()) # dict_keys(['name','age','city'])
```
### values()
values() 매서드를 사용하여 딕셔너리 값만을 가져올 수 있다.
```py
person = {'name':'Choonghyun','age':25,'city':'Seoul'}
print(person.values()) # dict_values(['Choonghyun','25','Seoul'])
```

### copy()
copy() 매서드를 사용하여 딕셔너리의 복사본을 생성할 수 있다. (확인해보지는 않았으나, 얕은 복사일 것이다.)
```py
person = {'name':'Choonghyun','age':25,'city':'Seoul'}
person_copy = person.copy()
print(person_copy) # {'name':'Choonghyun','age':25,'city':'Seoul'}
```

## 딕셔너리 응용 사용법
### 중첩 딕셔너리
딕셔너리 내에 딕셔너리를 다중으로 중첩할 수 있다.
```py
person = {'name':'Choonghyun','age':25,'address':{'street':'123 Main St','city':'Seoul'}}
print(person) # {'name':'Choonghyun','age':25,'address':{'street':'123 Main St','city':'Seoul'}}
```

### 반복문을 이용한 딕셔너리 키와 값 동시 처리
for문으로 딕셔너리의 키와 값을 동시에 처리할 수 있다.
```py
person = {'name':'Choonghyun','age':25,'city':'Seoul'}
for key,value in person.items():
    print(f"{key}:{value}")
```
출력
```
name: John Doe
age: 30
city: Seoul
```

### in
`in` 구문을 사용하여 딕셔너리에 특정 키가 존재하는지 확인할 수 있다. 키가 존재하는지를 확인할 때는 주로 if문과 함께 사용된다. 
```py
person = {'name':'Choonghyun','age':25,'city':'Seoul'}
if 'age' in person:
    print("Key 'age' exists in dict")
else:
    print("Key 'age' does not exist in dict")
```

## Tips
* 딕셔너리의 키는 `문자열, 숫자, 튜플` 등 다양한 타입의 값을 가질 수 있다.
* 딕셔너리의 키는 가변 타입의 값(리스트, 딕셔너리 등)을 가질 수 없다.
* 딕셔너리의 키와 값은 서로 다른 타입이어도 된다.