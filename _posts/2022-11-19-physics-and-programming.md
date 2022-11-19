---
layout: single
title: "about Physics and Programming"
toc: true
toc_sticky: true
toc_label: "study"
categories:
    - Study
---

<br>

<br>

# 물리와 프로그래밍 (3월 14일)

<br>

Anaconda &rarr; Jupyter notebook / Spyder

<br>


**High level language** &rarr; resource &uarr; , speed &darr; , difficulty &darr;

**Low level language** &rarr; speed &uarr; , difficulty &uarr; (거의 불가능 ..)

<br>

Compiler : ~ fast, 전체 프로그램을 작성 후 목적 파일을 작성하여 일괄적으로 실행하는 방법

Interpreter : ~ slow, line by line 으로 명령어를 실행시키는 방법


<br>

## 물리와 프로그래밍 (3월 16일)

<br>

### Python Expressions

<br>

컴퓨터 언어의 데이터 타입 : 데이터의 종류에 따라 차지하는 메모리 바이트가 다르기 때문이다.

<br>

### Literals - Numbers

<br>

- integer &rarr; 정수 자료형

- floating point number &rarr; 부동 소수점형

- **복소수의 i는 j로 쓴다.**

### Literals - Lists

- data = [1,4,9,16]

- C 언어의 배열에 해당되는 자료형. 리스트 형이라고 부름
- 

<br>

### Tuple

<br>

리스트와는 다르게 튜플은 원소 변경이 안 되는 자료형

<br>

### 파이썬의 기본 연산자

<br>

거듭제곱 &rarr; ** (^ 은 파이썬에서 인식 안 됨) 

**곱셈 기호를 생략할 수 없다.**

np,sqrt &rarr; name of function 

<br>

```py
import numpy as np

a,b,c = 1, -1, -1

(-b+np.sqrt(b**2-4*a*c))//(2*a)

```

`# Variables (변수) : 수학에서 쓰이는 변수와 의미가 비슷하지만, 컴퓨터의 메모리라는 점`

<br>

## 물리와 프로그래밍 (3월 21일)

<br>

함수 인수 개수 

- 0개 (ex_ np.random.random())
- 1개 (ex_ int(2.5))
- 콤마로 분리된 2개 이상의 인수 (ex_ pow(2.5, 3))
- 가변 개수의 인수 (ex_ max(2,3), max(2,3,4))

<br>

함수가 반환하는 결과 값의 개수

- 0개 (ex_ print('hello')는 IPython 콘솔에 텍스트 출력하는 동작 수행, ex_ plt.savefig 그림(plot)을 파일에 저장하는 동작)
- 1개 (ex_ numpy.sqrt(2))
- 여러 개의 반환된 값들 이용 가능 (5.3절 참고)
- Keyword arguments: 𝑓(𝑥,𝑦)=𝑥 𝑒^(−𝑦);𝑓(1, 2)  "or" 𝑓(𝑦=2, 𝑥=1) (5.1절 참고)

<br> 

### Ch.2 Structure and Control

<br>

- 2.1 객체(Objects)와 객체 메서드(Methods)
- 2.2 리스트(Lists), 튜플(Tuples), 배열(Arrays)
- 2.3 문자열(Strings)
- 2.4 루프(Loops): for loop, while loop
- 2.5 배열 연산(Array operations)
- 2.6 스크립트(Scripts)
- 2.7 조건적 동작: 분기(Contingent behavior: Branching): if
- 2.8 중첩(Nesting)

<br>

객체 (object) : (데이터, 함수)의 조합
- 파이썬에서 모든 것은 객체
- assignment statement (배정문) : 이름을 객체에 연계 &rarr; 변수 (variable) 

<br>

## 물리와 프로그래밍 (3월 23일)

<br>

### List 

<br>

```py
List, Tuple, Arrays

>>> a = [1,2,3,['a','b','c']]
>>> a
>>> a[0]
>>> a[1]
```

- 리스트에 요소 추가 (append)
- 위치 반환 (index)
- 리스트에 요소 삽입 (insert)

<br>

index &rarr; 위치 (첫 번째 위치 : 0)

컴퓨터에서 변수는 메모리다 !

<br>

```py
# 리스트에 요소 추가하자 append

a = [1,2,3]
a.append(4)
append(4) ==> X # append 라는 함수의 목적이 되는 변수 이름을 지정해줘야 함
a
a.append([5,6])
a # Out) [1,2,3,4,[5,6]]
a.append(5,6) # append 는 오직 한 개의 인수만을 갖는다 ..
```

```py
a = [1,4,3,2]
a
a.sort() # List 를 크기 순으로 정렬 해주는 함수 sort() 
a # Out) [1,2,3,4]
a = ['a', 'c', 'b']
a.sort()
a # Out) ['a', 'b', 'c']
```

```py
a = [1, 2, 3]
# List의 위치 변환
a.index(1) # 1이라는 원소의 인덱스 (위치) 가 몇 번째인지 알려줌 Out) 0
a.index(2) # Out) 1
a.index(3) # Out) 2
```

```py
# List에 요소를 삽입. append와 구별해야 함
a.insert(0,4) # 0번째 위치에다가 4라는 요소를 넣으라는 의미
a # Oui) [4,1,2,3]
```

**insert 와 append 의 차이 알아둘 것**

```py
insert(i,j)
i 위치에 j를 삽입하라는 의미
```

```py
# 요소 끄집어 내기 -> pop() : 마지막 원소를 끄집어 내서 보여줌. 빼내는 원소만큼 리스트가 줄어들음
a = [1,2,3]
a.pop() # 마지막 원소를 끄집어 냄 (위치 지정 안 했을시)
a # Out) 3
a.pop(0) 
a # Out) 1
```

<br>

### Tuple

<br>

**List 와 Tuple 의 차이**

전자는 값을 수정할 수 있지만, 후자는 값을 변경할 수 없음 .. ([] vs ()의 차이 역시 있음)

근데 왜 Tuple을 쓰는가? &rarr; List에 비해 더 적은 메모리를 필요로 하고, 속도가 빠르다는 장점 때문에 .........

<br>

### Dictionary 

<br>

Key와 Value를 한 쌍으로 갖는 자료형

```py
dic = {'name':'pey', 'phone':'01012345678', 'birth':'0608'}
```

List, Tuple에서 indexing 하는 방법과 비교
- 순차적으로 내용을 찾는 것이 아니라 key 를 사용해서 바로 접근

<br>

<br>

## 물리와 프로그래밍 (3월 28일)

<br>

### 딕셔너리

<br>

&rarr; 사전 

연관 배열 또는 해시

Key & Value 룰 한 쌍으로 가짐

해시는 실제 데이터의 값이 아닌 index 를 뜻함

해시를 이용하면 더욱 빠른 속도로 처리할 수 있음 .. (검색과 저장이 아주 빠름)

<br>

```py
dic = {'name' : 'jungjun', 'birth' : '20020608'}
```

<br>

<br>

### NumPy (array 배열)

<br>

core python

```py
c = []
for i in range(n)
  c.append(a[i]*b[i])
```

<br>


using Numpy

```py
c = a * b 
```

<br>

Packages &rarr; Module 의 집합

<br>

Numpy module 은 반드시 import 하고 사용해야 함 ..

```py
import numpy as np
a = np.array( (10, 11, 12, 13, 14) )
a
```

<br>

괄호 안에 공간 있어요 ..

<br>

`np.zeros(4)`

<br>

```python
dic = {'name' : jungjun, 'birth' : 20020608}
```


```python
dic['name']
```




    'jungjun'




```python
dic['birth']
```




    '20020608'




```python
dic.keys()
```




    dict_keys(['name', 'birth'])




```python
dic.values()
```




    dict_values(['jungjun', '20020608'])




```python
dic.items()
```




    dict_items([('name', 'jungjun'), ('birth', '20020608')])




```python
dic.get('name')
```




    'jungjun'




```python
dic.get('birth')
```




    '20020608'




```python
import numpy as np
a = np.array( (10, 11, 12, 13, 14) )
a
```




    array([10, 11, 12, 13, 14])




```python
b = np.array([1,2,3,4])
b
```




    array([1, 2, 3, 4])




```python
type(b)
```




    numpy.ndarray




```python
c = np.zeros(5)
c
```




    array([0., 0., 0., 0., 0.])




```python
print(c)
```

    [0. 0. 0. 0. 0.]
    


```python
type(c)
```




    numpy.ndarray




```python
type(c[0])
```




    numpy.float64




```python
c = np.zeros((3,5))
```


```python
c
```




    array([[0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0.]])




```python
import numpy 
```

<br>

`np.eye(4)` &rarr; 대각행렬

<br>

```py
np.random.random(3) # 난수 발생
```

<br>

```py
a = np.zeros((3,5))
b = np.ones(3)
np.shape(a) # shape 는 차원을 뜻함
>>> (3, 5)
```

<br>

```py
np.size(a) # 배열의 크기 => 배열 안의 모든 원소 숫자
>>> 15
```

<br>

## 물리와 프로그래밍 (3월 30일)

<br>

### Numpy

<br>

**일정한 간격의 수 만들기** &rarr; 데이터 사이언스에서 예제되는 데이터를 만들어 사용할 때 자주 사용.

`np.arrange(M,N)` &rarr; M,M+1, ... , N-1 로 정해지는 1차원 배열 생성

`np.arrage(start, end, increment)`

increment 생략 &rarr; 1

start 생략 &rarr; 0

<br>

`np.linspace` &rarr; `np.arange` 와 달리 마지막 값 exact 하게 출력

- `np.arrange` 간격을 고정할 때 유리

- `np.linspace` 물리나 공학에서 많이 쓰임 (함수의 범위를 설정할 때)

<br>

- **Index &rarr; 0부터 시작**
- 딕셔너리가 개별 원소에 접급하기 가장 쉬움



<br>

<br>

## 물리와 프로그래밍 (4월 4일)

<br>

```py
# 04/04 
# arrays and assignment 

# '=' : 수학적으로 '같다'가 아니라, 왼쪽의 변수에 대입 또는 배정하는 것

# '==' 수학적으로 같다는 뜻

# Q : A가 튜플인 경우, A[0] = 1 가능한가?
# 불가능 ... (튜플은 리스트와는 다르게 수정 불가능)

C = (1,2,3)
C[0] = 5

TypeError : 'typle' object does not support item assignment
```

<br>

```py
# D[0] = 1 # 정의가 안 된 배열에 값을 먼저 배정하면 X

impot numpy as np

D = np.zeors(100)

D[0] = 1

d
```

<br>

### Slicing

```
a[star:end:strid]

stride가 생략될 경우 기본 값은 1이다.

Start or End 생략시 기본 값은 각기 첫 번째 항과 마지막 항
```

<br>

```
원래 배열의 형태를 바꾸는 함수들 : 
혼동의 여지 있으므로 사용을 자제한다
```
```
Lists and arrays as indices (이런게 있구나 ~)
리스트가 자동적으로 선택될 때 매우 유용
```

<br>

<br>


```py
import numpy as np
a = np.arange(10,21)

a

b = [2,4,5]
a[b] # a의 원소 중 2,4,5 번째 원소 출력
```

Output_
```
array([12,14,15])
```

<br>

### String literal

<br>

`"" or ''` &rarr; grave accent X

<br>

```py
s1 = 'Hello World'
s2 = "Hello World" >> good ㅋ
```

<br>

\ &rarr escape character

<br>

```py
s4 = 'I said "let's go"'
```

&uarr; Error

<br>



```py
s4 = 'I said "let\'s go"'
```

&uarr; escape character 

<br>

**문자열 결합, 내장 함수 str()** &rarr; important

<br>

## 물리와 프로그래밍 (4월 6일)

<br>

### format()

<br>

```py
# 4월 6일 수업 내용
# format() 함수 : 문자열 안에 원하는 숫자나 문자열을 넣는데 사용
```
```py
import numpy as np
s1 = "The values of pi is approximately " + str(np.pi)
s1

>> 'The values of pi is approximately 3.141592653589793'
```
```py
s2 = "The value of {} is approximately {: .5f}".format('pi', np.pi)
s2

>>> 'The value of pi is approximately  3.14159'
```
```py
s3 = "{1:d} plus {0:d} is {2:d}".format(2, 4, 2+4) # :d ==> deximal
s3

>>> '4 plus 2 is 6'
```
```py
s4 = "Every {2} has its {3}".format('dog', 'day', 'rose', 'thorn')
s4

>>> 'Every rose has its thorn'
```
```py
s5 = "The third element of the list is {0[2]:g}.".format(np.arange(10))
# 포맷 지시자 :g(general)는 가장 적은 개수의 문자를 사용하여 숫자를 표시
s5

>>> 'The third element of the list is 2.'
```

<br>

### %를 사용하는 문자열

<br>

```py
str2 = "The value of %s is approximately %.5f" % ('pi', np.pi)
# "%s" : 문자열을 여기에 넣으라는 의미
# "%.5f" : 소수점 아래 5자리인 부동소수점 숫자를 여기에 넣으라는 의미
str2

>>> 'The value of pi is approximately 3.14159'
```
```py
str3 = "%d plus %d is %d" % (2, 4, 2+4)
str3 

>>> '2 plus 4 is 6'
```

<br>

> % &rarr; modulo operation (나머지 연산)으로도 쓰인다 !!

<br>

### Loops

<br>

```py
b, c = 2, -1
for a in np.arange(-1, 2, 0.3):
    x = (-b + np.sqrt(b**2 - 4*a*c)) / (2*a)
    print("a = {:.4f}, x = {:.4f}".format(a,x))

>>> 
a = -1.0000, x = 1.0000
a = -0.7000, x = 0.6461
a = -0.4000, x = 0.5635
a = -0.1000, x = 0.5132
a = 0.2000, x = 0.4772
a = 0.5000, x = 0.4495
a = 0.8000, x = 0.4271
a = 1.1000, x = 0.4083
a = 1.4000, x = 0.3923
a = 1.7000, x = 0.3783
```

<br>

```py
a, b, c = 2, 2, -1
while (b**2 - 4*a*c >= 0):
      x = (-b + np.sqrt(b**2 - 4*a*c)) / (2*a) 
      print("a = {:.4f}, x = {:.4f}".format(a, x)) 
      a = a - 0.3 
print("done!")

>>> 
a = 2.0000, x = 0.3660
a = 1.7000, x = 0.3783
a = 1.4000, x = 0.3923
a = 1.1000, x = 0.4083
a = 0.8000, x = 0.4271
a = 0.5000, x = 0.4495
a = 0.2000, x = 0.4772
a = -0.1000, x = 0.5132
a = -0.4000, x = 0.5635
a = -0.7000, x = 0.6461
done!
```

<br>

```py
for ii in range(10**6): 
     if ii % 10**5 == 0: print("{:f} percent complete …".format( (100*ii)/10**6))
     
>>> 
0.000000 percent complete …
10.000000 percent complete …
20.000000 percent complete …
30.000000 percent complete …
40.000000 percent complete …
50.000000 percent complete …
60.000000 percent complete …
70.000000 percent complete …
80.000000 percent complete …
90.000000 percent complete …
```

<br>

### infinite loops

<br>

```py
while True: print("infinite loop…")
```
```py
---------------------------------------------------------------------------
KeyboardInterrupt                         Traceback (most recent call last)
<ipython-input-64-3538fbd439b2> in <module>
----> 1 while True: print("infinite loop…")

~\anaconda3\lib\site-packages\ipykernel\iostream.py in write(self, string)
    400             is_child = (not self._is_master_process())
    401             # only touch the buffer in the IO thread to avoid races
--> 402             self.pub_thread.schedule(lambda : self._buffer.write(string))
    403             if is_child:
    404                 # newlines imply flush in subprocesses

~\anaconda3\lib\site-packages\ipykernel\iostream.py in schedule(self, f)
    203             self._events.append(f)
    204             # wake event thread (message content is ignored)
--> 205             self._event_pipe.send(b'')
    206         else:
    207             f()

~\anaconda3\lib\site-packages\zmq\sugar\socket.py in send(self, data, flags, copy, track, routing_id, group)
    398                                  copy_threshold=self.copy_threshold)
    399             data.group = group
--> 400         return super(Socket, self).send(data, flags=flags, copy=copy, track=track)
    401 
    402     def send_multipart(self, msg_parts, flags=0, copy=True, track=False, **kwargs):

zmq/backend/cython/socket.pyx in zmq.backend.cython.socket.Socket.send()

zmq/backend/cython/socket.pyx in zmq.backend.cython.socket.Socket.send()

zmq/backend/cython/socket.pyx in zmq.backend.cython.socket._send_copy()

~\anaconda3\lib\site-packages\zmq\backend\cython\checkrc.pxd in zmq.backend.cython.checkrc._check_rc()

KeyboardInterrupt: 
```

<br>

### Vectorization

<br>

## 물리와프로그래밍 (4월 11일)

<br>

### Broadcast (흩뿌리다) &larr; 확장의 의미를 가짐

<br>

**브로드캐스팅 조건**

- 두 넘파이 배열 중 최소한 하나의 배열의 어떤 축이라도 관계없이 차원이 1이라면 가능하다
- 두 넘파이 배열의 차원에 대해서 축의 길이가 동일하면 가능하다

<br>

Ex_
```py
import numpy as np
a = np.array([1,2,3])
b = np.array([1,2,3,4])
print(a+b)

>>>
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-4-85111a3ab660> in <module>
----> 1 print(a+b)

ValueError: operands could not be broadcast together with shapes (3,) (4,) 
```

&uarr; 축의 길이가 동일하지 않음

<br>

```py
a = np.array([[1,2,3],[4,5,6]])
b = 2
c = a*b
c
>>>
array([[ 2,  4,  6],
       [ 8, 10, 12]])
```
```
a는 벡터, b는 스칼라인데 c로 새로운 벡터(배열)로 확장(broadcast) 가능하다
```

<br>

```py
np.sum(a,0) # a라는 배열에서 0번째 축의 원소들을 다 더하라는 의미
```

<br>

```py
a = np.vstack((np.arange(20), np.arange(100,120)))
a
>>>
array([[  0,   1,   2,   3,   4,   5,   6,   7,   8,   9,  10,  11,  12,
         13,  14,  15,  16,  17,  18,  19],
       [100, 101, 102, 103, 104, 105, 106, 107, 108, 109, 110, 111, 112,
        113, 114, 115, 116, 117, 118, 119]])
```
```py
b = np.sum(a,0) # 위의 행과 아래행의 원소들을 더해서 1행의 새로운 배열을 생성
b
>>> 
array([100, 102, 104, 106, 108, 110, 112, 114, 116, 118, 120, 122, 124,
       126, 128, 130, 132, 134, 136, 138])
```
```py
c = np.sum(a,1)
c
>>>
array([ 190, 2190])
```

<br>

```py
a = np.array([[3,0,-1,1],[2,-1,-2,4],[1,7,0,4]])
a.min()
>>> -2
```

<br>

### Scripts &rarr; text file (series of commands)

<br>

**Jupyter &rarr; Interpreter**

**Spyder &rarr; Scripts** (Compiler)

<br>

### Debugging &rarr; 에러 or 경고 메시지 잘 읽기

<br>

- 코드를 주의해서 읽어본다
- 코드를 천천히 개발한다. 간단한 작업을 수행하는 각각의 단계가 정확히 의도된 작업을 수행하는지 확인한다.
- 간단한 데이터를 사용하여 코드를 확인한다
- 변수들을 조사하라 &rarr; a라는 변수를 사용 중, 중간중간에 a에 어떤 값이 있는지 출력해본다. (이런 기능이 있는 개발환경이 있다)
- 진단을 위한 명령들을 삽입한다. 오류 발생이 의심되는 곳 앞에 그 시점에서 특정 변수들이 갖고 있는 값들을 출력해본다.
- 코드를 작성하면서 사전 대책을 세운다
- 주변 친구들에게 도움을 받는다 Ex_ **Stackoverflow.com**
- **break points**를 이용한다 (어떤 지점에서 멈추는 것)

<br>

## 물리와프로그래밍 (4월 13일)

<br>

### Scripts - Comment

<br>

Comment &rarr; Good comments save time in the long run

<br>

```py
# projectile.py

'''
# Calculate how long an object is in the air when thrown from a specified height

# with a range of initial speeds assuming constant acceleration due to gravity:

#     0.5 * g * t**2 - v0 * t - y0 = 0
'''

import numpy as np

 

#%% Initialization of variables.

initial_speed = 0.0        # v0 = initial vertical speed of ball in [m/s]

impact_time = 0.0        # t = time of impact in [s] (computed in loop)

 

#%% Initialization of parameters.

g = 9.8066            # gravitational acceleration in [m/s^2]

initial_height = 2.0        # y0 = height ball is thrown from in [m]

speed_increment = 5.0    # how much to increase speed in [m/s] for each iteration

cutoff_time = 10.0        # stop computing after impact time exceeds cutoff

 

#%% Calculate and display impact time.  Increment initial speed each step.

# Repeat until impact time exceeds cutoff.

while impact_time < cutoff_time:

     # Use quadratic equation to solve kinematic equation for impact time:

     impact_time = (np.sqrt(initial_speed**2 + 2 * g * initial_height) + initial_speed) / g

     print("speed= {} m/s; time= {:.1f} s".format(initial_speed, impact_time))

     initial_speed += speed_increment

print("Calculation complete.")
```
```
!runfile('C:/Users/Gachon/untitled0.py', wdir='C:/Users/Gachon')
speed= 0.0 m/s; time= 0.6 s
speed= 5.0 m/s; time= 1.3 s
speed= 10.0 m/s; time= 2.2 s
speed= 15.0 m/s; time= 3.2 s
speed= 20.0 m/s; time= 4.2 s
speed= 25.0 m/s; time= 5.2 s
speed= 30.0 m/s; time= 6.2 s
speed= 35.0 m/s; time= 7.2 s
speed= 40.0 m/s; time= 8.2 s
speed= 45.0 m/s; time= 9.2 s
speed= 50.0 m/s; time= 10.2 s
Calculation complete.
```

<br>

<br>

## 물리와 프로그래밍 (5월 2일)

<br>

### Ploting

<br>

module Ex_ &rarr; **numpy**

pylab &darr;

pyplot &uarr;

plt.subplots() &rarr; 보조 플랏을 그릴 때 사용

<br>

```py
import matplotlib as mpl
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D
import numpy as np
import matplotlib.pyplot as plt
num_points = 5
x_min, x_max = 0, 4
x_values = np.linspace(x_min,x_max,num_points) 
y_values = x_values**2 
plt.plot(x_values, y_values)
```
```py
fig, (ax1, ax2, ax3) = plt.subplots(1,3, figsize = (12,4))

x = np.arange(1,11)

y1 = np.random.random(10)
y2 = np.random.random(10)
y3 = np.random.random(10)

ax1.plot(x, y1)
ax1.set_title('Plain Line plot')

ax2.plot(x, y2, marker = 'o')
ax2.set_title('Line plot with markers')

ax3.plot(x, y3, marker = 'o', linestyle = ':')
ax3.set_title('Line plot with markers & linestyle') 
```

<br>

plt.legend() &rarr; create legend

<br>

<br>

## 물리와 프로그래밍 (5월 16일)

<br>

### 실전 예제 2 _ SPACING between planes (원자 면간의 거리)

<br>

```py
#importing modules
import math
from __future__ import division

#Variable declaration

a = 5.64;      #lattice constant (angstrom)
h1 = 1;
k1 = 0;
l1 = 0;

h2 = 1;
k2 = 1;
l2 = 0;

h3 = 1;
k3 = 1;
l3 = 1;

#Calculation
d100=a/math.sqrt(h1**2 + k1**2 + l1**2);     #spacing between (100) plane
d110=a/math.sqrt(h2**2 + k2**2 + l2**2);     #spacing between (110) plane
d111=a/math.sqrt(h3**2 + k3**2 + l3**2);     #spacing between (111) plane

#Result
print ("spacing between (100) plane is",d100,"angstrom")
print ("spacing between (110) plane is",round(d110,2),"angstrom")
print ("answer for spacing between (110) plane given in the book is wrong")
print ("spacing between (111) plane is",round(d111,2),"angstrom")
```

<br>

**V(r) = A(1/C)^12 - B(1/C)^6**

**Lennard jones &rarr; molecular dynamics**

**가장 에너지가 적은 지점 r0에서 고체 상태로 존재할 확률이 가장 높음 ..**

<br>

원자 사이의 거리가 반발력으로 인해 멀어짐 .. 절대 들러붙지 X 

굉장히 많은 원자들의 포텐셜을 계산했으며

힘 &rarr; 가속도 &rarr; 속도

<br>

### 밀러 지수 (miller index)

<br>

결정학에서 결정격자의 면 (plane) & 방향 (direction) 을 나타내기 위한 표기법 !!

원자를 다루는 학문 &rarr; 고체물리 (Solid State Physics)

<br>

- Crystal line (규칙적으로 배열이 되어있음) (양자역학 이후 결정질에 대한 특성 파악)
- Polycrystal line

<br>

Miller Index 는 결정질의 원자들이 **이루는 면을 수학적으로 표시한 것**

Cubic &rarr; 3차원에서 원자들이 이루는 모형

원자로 이루어진 면을 설명하는 밀러 지수는 면과 좌표축이 만나는 점을 (1/h, 1/k, 1/l) &rarr; 면 (h, k, l)

면은 실재하지 않으며 가정하는 것임.

<br>

## 물리와 프로그래밍 (5월 18일)

<br>

### LJ 포텐셜 분자 동역학 (Molecular Dynamics)

<br>

중성 원자들에 작용하는 인력 (Ar, Ne 등) 

포텐셜이 + &rarr; 반발력 &uarr; 

<br>

멀어지다가 인력이 작용하면 다시 가까워짐

LJ 포텐셜을 이용해서 중성 원자들이 시간에 따라 어떻게 운동하는지를 시각화해서 볼 수 있다.

기본적인 아이디어는 &darr;

LJ 포텐셜 (에너지) &rarr; 어떤 범위의 거리 안에 있는 원자들이 느끼는 힘을 계산한다. (F = -du/dx) &rarr; 힘에서 가속도를 구한다. (F = ma) &rarr; 가속도를 알면 원자들의 속도를 구할 수 있다

<br>

결정에서는 원자 혹은 분자들이 규칙적으로 배열되어 있다. 

이렇게 규칙적으로 배열된 원자들이 만들어내는 면과 그 면의 방향을 표기하는 방법을 밀러 지수 (miller index) 라고 한다 

아래 그림에서 세 개의 축 x, y, z 과 원자들에 의해서 그려지는 면을 수학적으로 표시하는 방법이고 물리학, 수학, 재료공학에서 보편적으로 사용된다.

밀러지수가 표시하는 면은 실제로 원자 안에 그러한 평면의 물질이 **따로 존재하는 것이 아니라** 원자들이 이루는 **가상의 면**이다.

따라서 한 결정 구조 안에서 표현되는 면은 무한히 많다.

<br>

### 밀러지수를 결정하는 방법 

가장 간단한 구조인 큐빅 (입방체) 에서 밀러지수를 결정하는 방법을 알아보자

<br>

![image](https://user-images.githubusercontent.com/96330958/168938043-ebe03a8c-1a5a-433f-84cb-9f01a13b1798.png)

<br>


밀러지수는 다음과 같은 순서에 의해 결정할 수 있다. 

- 좌표축의 표시 : 물리학적으로 의미있는 좌표축은 임의로 설정 가능하다.
- 좌표와 만나는 평면 (plane) 을 확인한다.
  - 원자 (분자) 들에 의해 생기는 면이 어떤 점과 만나는지 계산한다.

<br>

![image](https://user-images.githubusercontent.com/96330958/168938646-efb90efa-ab91-470e-b2fe-6b48741884ad.png)

<br>

Ex_ 위의 그림에서, 녹색의 면은 z = 1 이라는 점과 교차한다. 그 만나는 좌표를 (무한대, 무한대, 1) 로 표시한다.

<br>

- 교차하는 좌표의 역수를 취한다 :
  - (무한대, 무한대, 1) 의 역수를 취하면 [0,0,1] 

<br>

- 이렇게 구한 좌표의 역수를 정수 형태로 만들어준다.

<br>

이렇게 구한 위의 면의 밀러 지수를 [0,0,1] 이 된다.

그리고 면의 밀러 지수 &rarr; 소괄호 () 로 표시하므로 (0,0,1) 이 최종 밀러 지수로 사용된다.

<br>

이 (0,0,1) 면과 (0,0,2) 는 어떤 관계에 있을까 ?? &rarr; (0,0,2) 면이 결정 안에서 어떤 모양을 하는지 이해하려면, 밀러 지수를 구하는 방법의 역순을 따라가면 쉽게 할 수 있다.

- (0,0,2) &rarr; 역수를 취하면 평면과 좌표측이 교차하는 점을 구할 수 있다.
- (0,0,2) 의 역수 &rarr; (무한대, 무한대, 1/2) 즉 (0,0,1) 보다 아래에 존재한다 .. ^^

<br>

이 사실을 이해하면 (0,0,1), (0,0,2), (0,0,3), ... 의 상관 관계를 알 수 있다. 즉 3번째 밀러 지수의 값이 커질수록 평면은 (0,0,1) 의 아래에 위치하는데,

중요한 것은 (0,0,1) 과 평행하다는 것을 알 수 있다.

밀러 지수는 이러한 성지를 이용해서 한 면만을 말하는 것이 아니고, 그 면과 평행인 모든 면을 표현할 수 있다.

<br>

면의 밀러 지수와 법선의 밀러 지수

소괄호는 면 자체, 중괄호는 그 평면에 법선인 벡터를 나타낸다.

(0,0,1) : 평면

[0,0,1] : (0,0,1) 면에 수직인 벡터

<br>

&darr; 큐빅 구조에서 가능한 면들의 밀러 지수를 표시 

![image](https://user-images.githubusercontent.com/96330958/168939220-babcc510-8184-47ed-a055-049f5687dac2.png)

&uarr; 서로 다른 밀러 지수를 갖는 입방 결정들 !

<br>

<br>

## 물리와 프로그래밍 (5월 23일)

<br>

격자 상수가 a인 입방 결정에서 밀러 지수가 (l,m,n) 인 면들 사이의 거리

밀러 지수 (l,m,n) 은 같은 방향으로 서로 평행인 무한히 많은 면을 포함하게 된다.

이 무한한 면들 중에서 서로 이웃하는 두 면의 거리 d를 계산하면 다음과 같다.

d = a/sqrt (l^2 + m^2 + n^2)

<br>

```py
#importing modules 
import math # 수학 전문 모듈 math를 불러온다

#Variable declaration

a = 5.64;      # 격자 상수 (그 분자의 크기를 나타낸다)
l1 = 1;        # 면들의 밀러 지수 (lmn)
m1 = 0; 
n1 = 0;        # 밀러 지수 (100)인 면

l2 = 1;
m2 = 1;
n2 = 0;        # 밀러 지수 (110)인 면

l3 = 1;        # 밀러 지수 (111)인 면
m3 = 1;
n3 = 1;


# 면들 사이의 거리 계산
d100=a/math.sqrt(l1**2 + m1**2 + n1**2);     #spacing between (100) plane # (100) 면 사이의 간격
d110=a/math.sqrt(l2**2 + m2**2 + n2**2);     #spacing between (110) plane # (110) 면 사이의 간격
d111=a/math.sqrt(l3**2 + m3**2 + n3**2);     #spacing between (111) plane # (111) 면 사이의 간격

# Result
print ("spacing between (100) plane is",d100,"angstrom")
print ("spacing between (110) plane is",round(d110,2),"angstrom")
print ("answer for spacing between (110) plane given in the book is wrong")
print ("spacing between (111) plane is",round(d111,2),"angstrom")
```

<br>

3개의 면 (100), (110), (111) 면 사이의 간격을 파이썬을 이용해서 구해보자. 그 코드는 위와 같다.. ^^ &uarr;

<br>

### 실전 예제 3 : 상자 안에 갇힌 전자의 에너지 준위

<br> 

가장 간단한 양자 시스템으로서 전자가 오직 한 개만 있는 원자를 생각해보자. 

이러한 시스템과 가장 유사한 원자는 자연에 수소가 있다. 

원자 한 개가 원자핵에 의해 갇혀있으므로, 1차원 상에서 다음과 같이 모델링하면 가장 이해하기 쉬울 것이다.

<br>

이 전자가 포텐셜 우물에 빠져있어서, 이 우물 밖으로는 나오지 못하는 상황을 가정해보자. 

아래 그림과 같이 이 우물의 폭은 L이고, 좌표는 1차원만 존재하므로 x라고 해보자.

좌표축을 설정해서 x = 0 ~ x = L 이 우물의 경계이고 이 0<=x=<L 사이에만 전자가 존재한다.

이 전자가 갇혀있다는 것은 우물의 양 끝점 (x = 0 and x = L) 에서 전자가 존재하지 않는다는 뜻이다.

(측정이라는 관점에서 보면 이 두 점에서 이 전자가 발견될 확률은 0 이 된다는 것이다.

<br>

우물 안에서는 (0 < x < L) 포텐셜이 0이어서 전자는 아무런 힘도 느끼지 않고 자유롭게 운동할 수 있다.

다만, 경계면에서 포텐셜이 무한대이므로 이 우물을 뚫고 밖으로 나가진 못한다.

<br>

양자역학에 의해서 이 전자의 물리적인 모든 정보는 파동함수 (wavefunction) (psi) 안에 다 담겨져 있다.

또한 양자역학은 이 파동함수가 다음의 슈뢰딩거 방정식을 따른다고 알려준다.

<br>

H (psi) = E (psi)

H : 해말토니안이고 전자가 갖고 있는 모든 에너지의 합을 의미한다. 입자의 모든 에너지 H = 운동 에너지 + 포텐셜 에너지 = T + V 로 표시된다.

그런데, 이 전자가 우물 안에서 포텐셜 = 0 이므로 이 전자가 가질 수 있는 에너지는 운동에너지 뿐이다.

따라서 H = T (운동에너지) = -h_bar^2/(2 m)*2^2/dx2 가 된다

<br>

<br>

## 물리와 프로그래밍 (5월 25일)

<br> 

### 실전 예제 3 : 상자 안에 갇힌 전자의 에너지 준위

<br>
Particle in a box + 터널링

포텐셜 = 0 &rarr; 운동에너지 *Kinetic Energy

<br>

<br>



1번

```py
import numpy as np
import matplotlib.pyplot as plt

plt.rcParams.update({'font.size': 18}) 

def lj_pot(x, epsilon, sigma, r_cut, c_shift=0.0):
    pot = 4.0 * epsilon * ((sigma / x)**12 - (sigma / x)**6) + c_shift
    pot[x > r_cut] = 0
    return pot

epsilon = 1.0 
sigma = 1.0    

xs = np.linspace(0.5, 10, 100) 
ys_lj = lj_pot(xs, epsilon, sigma, r_cut=xs[-1])

fig = plt.figure(figsize=(10, 6))
plt.plot(xs, ys_lj, label='LJ') 
plt.axhline(y=0, color='grey')
plt.xlabel("$r/\sigma$") 
plt.ylabel("$V(r)/(k_{\mathrm{B}}T)$") 
plt.legend() 
plt.ylim(-1.5, 2.5) 
plt.show() 
```

<br>

2번

```py
import numpy as np
import matplotlib.pyplot as plt

plt.rcParams.update({'font.size': 18}) 

def lj_pot(x, epsilon, sigma, r_cut, c_shift=0.0):
    pot = 4.0 * epsilon * ((sigma / x)**12 - (sigma / x)**6) + c_shift
    pot[x > r_cut] = 0
    return pot

epsilon = 1.0 
sigma = 1.0    

xs = np.linspace(0.5, 1.5, 100) 
ys_lj = lj_pot(xs, epsilon, sigma, r_cut=xs[-1])

fig = plt.figure(figsize=(10, 6))
plt.plot(xs, ys_lj, label='LJ') 
plt.axhline(y=0, color='grey')
plt.xlabel("$r/\sigma$") 
plt.ylabel("$V(r)/(k_{\mathrm{B}}T)$") 
plt.legend() 
plt.ylim(-1.5, 2.5) 
plt.show() 
```

<br>

3번 

```
최소 점의 물리적인 의미 == 가장 에너지가 적은 지점 r0에서 고체 상태로 존재할 확률이 가장 높음
```

<br>

5번

```py
#importing modules 
import math # 수학 전문 모듈 math를 불러온다

#Variable declaration

a = 5.64;      # 격자 상수 (그 분자의 크기를 나타낸다)
l1 = 1;        # 면들의 밀러 지수 (lmn)
m1 = 0; 
n1 = 0;        # 밀러 지수 (100)인 면

l2 = 1;
m2 = 1;
n2 = 0;        # 밀러 지수 (110)인 면

l3 = 1;        # 밀러 지수 (111)인 면
m3 = 1;
n3 = 1;


# 면들 사이의 거리 계산
d100=a/math.sqrt(l1**2 + m1**2 + n1**2);     #spacing between (100) plane # (100) 면 사이의 간격
d110=a/math.sqrt(l2**2 + m2**2 + n2**2);     #spacing between (110) plane # (110) 면 사이의 간격
d111=a/math.sqrt(l3**2 + m3**2 + n3**2);     #spacing between (111) plane # (111) 면 사이의 간격

# Result
print ("spacing between (100) plane is",d100,"angstrom")
print ("spacing between (110) plane is",round(d110,2),"angstrom")
print ("answer for spacing between (110) plane given in the book is wrong")
print ("spacing between (111) plane is",round(d111,2),"angstrom")
```

<br>

## 물리와 프로그래밍 (6월 1일)

<br>

```py
#importing modules
import math
from __future__ import division
#Variable declaration
d=1.181;       #lattice spacing(angstrom)
theta=90*math.pi/180;     #glancing angle(radian)
lamda=1.540;    #wavelength of X-rays(angstrom)
#Calculation
n=2*d*math.sin(theta)/lamda;       #maximum order of diffraction 
#Result
print "maximum order of diffraction is",round(n,2)
```
