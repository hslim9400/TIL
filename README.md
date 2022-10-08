# TIL

## 규칙

## 분류

### Git

#### Git ?

프로젝트를 진행하다 보면 프로젝트를 수정할때마다 그것을 저장하게 되고 
과거의 기록을 통해 어떤 부분이 어떻게 수정되었는지 알고 싶어진다.

Git은 프로그래밍을 하며 프로그램의 수정사항에 대한 버전을 
기록하고 관리할 수 있도록 하는 프로그램이다. 
git init을 통해 디렉토리 내에 git 폴더를 생성하고 git add를 통해 
변경내용을 스테이징하고 git commit으로 그것을 기록한다.
git status로 git이 추적하고 있는 파일이 어떤 상태에 있는지 확인한다.
git commit을 통해 git add로 스테이징 한 변경내용을 기록한다.
이것으로 로컬영역에서 git으로 할 수 있는 일은 했다고 할 수 있다.

* 상위폴더에서 git init을 선언하면 그 아래에서 일어나는 모든 변경사항들을 추적하므로 주의해야 하며 git ignore명령으로 추적하지 않을 파일들을 선택할 수 있다.

#### Git과 Hub

여러 사람과 협업을 할 경우 프로젝트의 진행사항과 수정 내역들을 공유하게 된다. 이 때 git의 commit내역을 온라인에 저장할 수 있도록 하는 서비스가 GitHub이다. GitHub의 repository에서 클론을 생성하여 파일을 수정할 수 있다.
로컬에서 Git remote를 통해 리모트를 설정하고 git pull을 통해 Hub->로컬로 commit내역을 동기화하고 git push를 통해 로컬->Hub로 commit내역을 동기화 한다. 

* 이 때 양쪽의 commit기록이 서로 달라진 채로 동기화를 시도 할경우 collision이 발생한다. 

---

### Python

##### 코드 스타일

코드를 보기 좋고, 통일되도록 작성하도록 하는 가이드 라인

파이썬에서 제안하는 스타일 가이드

PEP8 (https://www.python.org/dev/peps/pep-0008/ )

회사/ 프로젝트마다 따로 스타일 가이드를 설정하기도 함

#### 자료형

##### 불리언

참, 거짓을 표현하는 자료형

and, or등의 논리 연산자 사용

and는 사칙연산에서 곱셈과 유사, or는 덧셈과 유사 -

```python
3 is True
>False
```

##### 숫자형

##### 문자열

#### 컨테이너

###### 리스트

l.pop(i) : 인덱스 원소 반환 후 삭제, 인덱스 미지정 시 마지막 원소 반환 후 삭제

l.append(x) : 리스트 마지막에 x 추가 x가 컨테이너일 경우 컨테이너 째로 추가

l.extend(m) : 순회형 m의 모든 항목을 리스트 끝에 추가

###### 튜플, 레인지

###### 세트

s.add(x) : s에 x가 없을 시 x 추가

s.pop() : 임의의 원소 반환

s.issubset(t) : s가 t의 하위 셋 일 경우(t 가 s를 포함) True

s.remove(x) :  x 삭제, 없을시 KeyError   s.discard(x) : x 삭제, 없어도 오류 나지 않음

###### 딕셔너리

d.keys(), d.values(), d.items() : 딕셔너리 들이 각각 keys, values, items(key, item)를 반환 반환하는 자료형은 바꾸어줘야 하는 듯

리스트에 인덱스를 붙여 딕셔너리로 만들고 싶다

```python
test_dict = {}
for idx, num in enumerate(winners):
    test_dict[idx + 1] += num
```

이건 오류(키에러로)

```python
test_dict = {}
for idx, num in enumerate(winners):
    test_dict[idx+1] = 0
    test_dict[idx+1] += num
```

이렇게 초기화 해줘야 생성할 수 있다.

또는

```python
from collections import defaultdict
int_dict = defaultdict(int)
```

초기 값을 int로 설정할 수 있다.

```python
for idx, num in enumerate(winners):
    int_dict[idx+1] += num
```

이건 된다.

#### 반복문

##### for

###### for .. else

for와 같은 레벨에  else를 둬서 break없이 for문을 빠져나온 후 실행한다. 있는지도 몰랐던 구문이라 익숙하지 않은데 적절한 상황에서 사용한다면 상당히 유용할 것 같다.

#### 함수

##### 인자에 대해서

함수를 선언하면 함수에 들어갈 인자를 선택하게 되는데

```python
def func(me)
```

me(나)라고 써있는 녀석이 인자이다. 함수를 선언할 때 기본값을 설정할 수 있는데 만약 여러 인자를 선언 할 경우, 기본값을 설정한 인자 뒤에는 기본값이 없는 인자를 사용하지 못한다.

```python
def func(name = '임씨', age)
```

이렇게는 안된다는 뜻

또한 함수를 불러올 때에 키워드인자를 활용한 다음에는 위치인자를 활용하지 못한다.

```python
func(age = 100, '임)
```

이렇게는 못부른다.

##### 내장함수

###### zip(*iterables)

```python
a = [[1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
list(zip(*a))  
```

를 찍으면

```python
[(1, 4, 7), (2, 5, 8), (3, 6, 9)]
```

가 나온다.

각각의 iterable 객체나 순서 객체의 i번째에 해당하는 원소들을 튜플의 i번쨰 원소로 포함하는 튜플을 반환한다.

고 써있다.

가변인자를 받을 수 있기 때문에 *a로 입력 시 자동으로 a[0], a[1], a[2], ..로 입력받는다. 원소의 개수가 같은 여러개의 리스트를 인자로 입력하면 이들을 묶어 튜플로 생성하여 반환한다.  

전치행렬 구할때 쓰면 유용할만도..

##### LEGB에 대해서

함수내에서 매개변수로 받지 않은 값을 사용하려 할 경우 값을 참조해야 한다. 그럴 경우 뒤져보는 통의 순위가 LEGB라 할 수 있다. Local, Enclosed,  Global, Built-in순서이다. 

```python
def a():
    print(1)

    def b():
        print(2)

        def c():
            print(3)

        c()
    b()
a()
```

이런걸 할 수 있는데 출력 해보면

```
1
2
3
```

이런 식으로 출력된다.

#### 객체지향 프로그래밍

##### 추상화

##### 상속

부모클래스가 가진 모든 속성, 행동, 관계 및 제약조건을 상속받음

애스터리스크(*)를 통해 init메서드도 가져올 수 있음

```python
class 자식(부모):

    def __init__(self, arg1, arg2, *args):
        super().init(*args)
        self.args1 = args1
        self.args2 = args2
```

이런식. 물론 말고도 다 상속받을 수 있다. 더 고민해보자.

##### 다형성

##### 캡슐화

### 웹 (추가예정)

#### 

#### CSS

HTML에서 <style>태그를 붙여서 작성

##### flexbox

##### 

##### Bootstrap

<<<<<<< HEAD

###### grid

Bootstrap Grid System은 flexbox로 제작됨

column은 12칸을 차지함

gird breakpoint는 6가지(xs, sm, md, lg, xl, xxl)

breakpoint를 사용해 화면의 전체 크기에 따라 다른 화면을 표시할수 있다.

즉, 디스플레이의 종류에 따라 화면을 바꿀 수 있다.(반응형 웹)

12칸이 넘어가면 넘어간 박스는 다음 줄부터 시작한다. 빈 칸은 채우지 않음



### Django

CRUD

modelform

authentication

login & logout

### DB
