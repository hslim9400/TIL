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

###### 튜플, 레인지

###### 세트

###### 딕셔너리

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

###### 인자에 대해서

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