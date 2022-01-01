---
layout: single
title: "간단한 슈팅 게임 만들기 프로젝트"
toc: true
toc_sticky: true
toc_label: "On This Page"
categories:
    - Python
---

<br>

## 1. 슈팅 게임이란.

<br>

**ShooTingGame.**

적의 공격을 피하며 무기를 쏘는 게임의 총칭이다.

간단한 게임의 구조와 조작성 덕분에 게임 역사의 초창기부터 존재하였던 장르이다.

게임 제작 입문으로 자주 사용 되기 때문에, 나의 첫 번째 프로젝트로 정했다 !!

<br>

## 2. Pygame ?

<br> 

**pygame** 은 SDL 라이브러리 위에 구축되어 게임과 같은 멀티미디어 어플리케이션을 만들기 위한 

오픈 소스 파이썬 프로그래밍 라이브러리이다.

<br>

## 3. Python 에서 pygame 설치

<br>

**cmd prompt** 를 실행한 다음,

<br>

```js
pip install pygame 
```

<br>

이라는 명령어를 입력한다. 

<br>

설치가 완료 된 다음, **python idle** 을 실행하고

<br>

```js
import pygame
```

<br>

을 입력한다.

작성일 기준으로 pygame 2.1.2 (SDL 2.0.18, Python 3.9.9) 가 잘 설치 됐다는걸 확인했다.

**SuanLab** 님이 올려주신 리소스 파일을 다운 받았으며 

이제부터 게임 화면을 본격적으로 코딩 할 것이다.

<br>

## 4. 게임 화면 구성

<br>

본격적인 코딩에 앞서 idle 실행창에서 File-New File 을 클릭해 새로운 파일을 만들어주고,

Ctrl + S 를 누른 다음 파일을 Pyshooting 경로에 

Pyshooting.py 라는 이름으로 저장해주었다.

```py
import pygame
import sys
from time import sleep


BLACK = (0,0,0) # 게임 처음 화면을 블랙으로 설정
padWidth = 480 # 게임 화면 크기 
padHeight = 640 


def initGame(): # 게임 초기화를 위한 함수 'initGame'
    global gamePad, clock # global 변수로 gamePad 와 clock 을 가져온다
    pygame.init()
    gamePad = pygame.display.set_mode((padWidth, padHeight))
    pygame.display.set_caption('PyShooting') # 게임의 이름 !!
    clock = pygame.time.Clock()


def runGame(): # 실질적으로 게임이 실행될 수 있는 함수인 rungame
    global gamePad, clock

    onGame = False
    while not onGame:
        for event in pygame.event.get():
            if event.type in [pygame.QUIT]: # 창을 닫으면 ?
                pygame.quit() # 파이 게임을 닫고 
                sys.exit() # 시스템을 종료시킨다 !!

            gamePad.fill(BLACK) # 화면을 검은색으로 채워라

            pygame.display.update() # 게임 화면을 다시 그림

            clock.tick(60) # 초당 프레임 수를 60으로 설정하여 
            #게임 플레이가 초당 60으로 진행됨

        pygame.quit() # pygame 종료


initGame()
runGame()
```

<br>

```
pygame.error: video system not initialized
```

<br>

시작부터 에러가 뜬다. ㅎㅎ

<br>

`pygame.quit() --> pygame.init() 으로 바꾸니까 잘 실행되는 것을 확인했다.`

<br>

## 5. 배경 그림 넣기

<br>

```py
import pygame
import sys
from time import sleep


padWidth = 480 # 게임 화면 크기 
padHeight = 640 


def drawObject(obj, x, y): # 게임에 등장하는 객체를 드로잉
    global gamePad
    gamePad.blit(obj, (x,y)) # blit 이란, 비티 현상과 관련해서 해당하는 오브젝트를 x, y 좌표 위치로부터 그려라라는 의미 !!


def initGame(): # 게임 초기화를 위한 함수 'initGame'
    global gamePad, clock, background # global 변수로 gamePad 와 clock 을 가져온다
    pygame.init()
    gamePad = pygame.display.set_mode((padWidth, padHeight))
    pygame.display.set_caption('PyShooting') # 게임의 이름 !!
    background = pygame.image.load('background.png')
    clock = pygame.time.Clock()


def runGame(): # 실질적으로 게임이 실행될 수 있는 함수인 rungame
    global gamePad, clock, background # 정엽변수 불러와야 함 ....

    onGame = False
    while not onGame:
        for event in pygame.event.get():
            if event.type in [pygame.QUIT]: # 창을 닫으면 ?
                pygame.quit() # 파이 게임을 닫고 
                sys.exit() # 시스템을 종료시킨다 !!

            drawObject(background, 0, 0)

            pygame.display.update() # 게임 화면을 다시 그림

            clock.tick(60) # 초당 프레임 수를 60으로 설정하여 게임 플레이가 초당 60으로 진행됨

        pygame.init()


initGame()
runGame()
```

<br>

![image](https://user-images.githubusercontent.com/96330958/147814545-fcddb6de-eef6-4157-9532-fba45b8f4677.png)

<br>

보시다시피 이미지 로드가 아주 잘 됐다 ^^ .. b

<br>

## 5-1 전투기 넣기

<br>

drawObject 를 통해 전투기의 위치를 설정해줄 것이다 .. 

정엽변수 fighter 추가는 덤 . . .

<br>

```py
import pygame
import sys
from time import sleep


padWidth = 480 # 게임 화면 크기 
padHeight = 640 


def drawObject(obj, x, y): # 게임에 등장하는 객체를 드로잉
    global gamePad
    gamePad.blit(obj, (x,y)) # blit 이란, 비티 현상과 관련해서 해당하는 오브젝트를 x, y 좌표 위치로부터 그려라라는 의미 !!


def initGame(): # 게임 초기화를 위한 함수 'initGame'
    global gamePad, clock, background, fighter # global 변수로 gamePad 와 clock 을 가져온다
    pygame.init()
    gamePad = pygame.display.set_mode((padWidth, padHeight))
    pygame.display.set_caption('PyShooting') # 게임의 이름 !!
    background = pygame.image.load('background.png')
    fighter = pygame.image.load('fighter.png')
    clock = pygame.time.Clock()


def runGame(): # 실질적으로 게임이 실행될 수 있는 함수인 rungame
    global gamePad, clock, background, fighter # 정엽변수 불러와야 함 ....

    fighterSize = fighter.get_rect().size
    fighterWidth = fighterSize[0]
    fighterHeight = fighterSize[1]

    x = padWidth * 0.45 # 폭에서 0.45 위치
    y = padHeight * 0.9 # 높이에서 0.9 위치
    fighterX = 0


    onGame = False
    while not onGame:
        for event in pygame.event.get():
            if event.type in [pygame.QUIT]: # 창을 닫으면 ?
                pygame.quit() # 파이 게임을 닫고 
                sys.exit() # 시스템을 종료시킨다 !!

            drawObject(background, 0, 0)

            pygame.display.update() # 게임 화면을 다시 그림

            clock.tick(60) # 초당 프레임 수를 60으로 설정하여 게임 플레이가 초당 60으로 진행됨

        pygame.init()


initGame()
runGame()
```

<br>

이제 F5 를 눌러 전투기가 보이는지 확인해보자 ^^ !!

<br>

![image](https://user-images.githubusercontent.com/96330958/147814862-21962709-9cfc-4286-baa4-135d9ffc5b53.png)

<br>

?

<br>

`drawObject(fighter, x, y)` 를 빼먹었다 .. ^^ 

코드를 넣어주니 정상적으로 전투기가 나온다 .. ^^

<br>

```py
import pygame
import sys
from time import sleep


padWidth = 480 # 게임 화면 크기 
padHeight = 640 


def drawObject(obj, x, y): # 게임에 등장하는 객체를 드로잉
    global gamePad
    gamePad.blit(obj, (x,y)) # blit 이란, 비티 현상과 관련해서 해당하는 오브젝트를 x, y 좌표 위치로부터 그려라라는 의미 !!


def initGame(): # 게임 초기화를 위한 함수 'initGame'
    global gamePad, clock, background, fighter # global 변수로 gamePad 와 clock 을 가져온다
    pygame.init()
    gamePad = pygame.display.set_mode((padWidth, padHeight))
    pygame.display.set_caption('PyShooting') # 게임의 이름 !!
    background = pygame.image.load('background.png')
    fighter = pygame.image.load('fighter.png')
    clock = pygame.time.Clock()


def runGame(): # 실질적으로 게임이 실행될 수 있는 함수인 rungame
    global gamepad, clock, background, fighter # 정엽변수 불러와야 함 ....

    fighterSize = fighter.get_rect().size
    fighterWidth = fighterSize[0]
    fighterHeight = fighterSize[1]

    x = padWidth * 0.45 # 폭에서 0.45 위치
    y = padHeight * 0.9 # 높이에서 0.9 위치
    fighterX = 0


    onGame = False
    while not onGame:
        for event in pygame.event.get():
            if event.type in [pygame.QUIT]: # 창을 닫으면 ?
                pygame.quit() # 파이 게임을 닫고 
                sys.exit() # 시스템을 종료시킨다 !!

            drawObject(background, 0, 0)

            drawObject(fighter, x, y)

            pygame.display.update() # 게임 화면을 다시 그림

            clock.tick(60) # 초당 프레임 수를 60으로 설정하여 게임 플레이가 초당 60으로 진행됨

        pygame.init()


initGame()
runGame()
```

<br>

## 6. 전투기 움직이기

<br>

```py
 if event.type in [pygame.KEYDOWN]
                    if event.key == pygame.K_LEFT: # 전투기 왼쪽으로 이동
                        fighterX -= 5

                    elif event.key == pygame.K_RIGHT: # 전투기 오른쪽으로 이동
                        fighterX += 5

                if event.type in [pygame.KEYUP]: # 방향키를 떼면 전투기가 멈춤
                    if event.key == pygame.K_LEFT or event.key == pygame.K_RIGHT:
                        fighterX = 0

```

<br>

```py
x += fighterX
            if x < 0: # x 가 0보다 작을 경우 : 게임 왼쪽 끝까지 가는 경우를 의미..
                x = 0 # 멈춰 !
            elif x > padWidth - fighterWidth: # 오른쪽 끝까지  갔을 때
                x = padWidth - fighterWidth # 멈춰 !!
```

<br>

안 된다 ........................

아무리 방향키를 눌러도 되지 않는다 ......................

일단 지금까지 해놓은 코드를 올려놓고 내일 다시 살펴봐야겠다 . . .

<br>

```py
import pygame
import sys
from time import sleep


padWidth = 480 # 게임 화면 크기 
padHeight = 640 


def drawObject(obj, x, y): # 게임에 등장하는 객체를 드로잉
    global gamePad
    gamePad.blit(obj, (x,y)) # blit 이란, 비티 현상과 관련해서 해당하는 오브젝트를 x, y 좌표 위치로부터 그려라라는 의미 !!


def initGame(): # 게임 초기화를 위한 함수 'initGame'
    global gamePad, clock, background, fighter # global 변수로 gamePad 와 clock 을 가져온다
    pygame.init()
    gamePad = pygame.display.set_mode((padWidth, padHeight))
    pygame.display.set_caption('PyShooting') # 게임의 이름 !!
    background = pygame.image.load('background.png')
    fighter = pygame.image.load('fighter.png')
    clock = pygame.time.Clock()


def runGame(): # 실질적으로 게임이 실행될 수 있는 함수인 rungame
    global gamepad, clock, background, fighter # 정엽변수 불러와야 함 ....

    fighterSize = fighter.get_rect().size
    fighterWidth = fighterSize[0]
    fighterHeight = fighterSize[1]

    x = padWidth * 0.45 # 폭에서 0.45 위치
    y = padHeight * 0.9 # 높이에서 0.9 위치
    fighterX = 0


    onGame = False
    while not onGame:
        for event in pygame.event.get():
            if event.type in [pygame.QUIT]: # 창을 닫으면 ?
                pygame.quit() # 파이 게임을 닫고 
                sys.exit() # 시스템을 종료시킨다 !!

                if event.type in [pygame.KEYDOWN]:
                    if event.key == pygame.K_LEFT: # 전투기 왼쪽으로 이동
                        fighterX -= 5

                    elif event.key == pygame.K_RIGHT: # 전투기 오른쪽으로 이동
                        fighterX += 5

                if event.type in [pygame.KEYUP]: # 방향키를 떼면 전투기가 멈춤
                    if event.key == pygame.K_LEFT or event.key == pygame.K_RIGHT:
                        fighterX = 0

            drawObject(background, 0, 0)

            x += fighterX
            if x < 0: # x 가 0보다 작을 경우 : 게임 왼쪽 끝까지 가는 경우를 의미..
                x = 0 # 멈춰 !
            elif x > padWidth - fighterWidth: # 오른쪽 끝까지  갔을 때
                x = padWidth - fighterWidth # 멈춰 !!

            drawObject(fighter, x, y)

            pygame.display.update() # 게임 화면을 다시 그림

            clock.tick(60) # 초당 프레임 수를 60으로 설정하여 게임 플레이가 초당 60으로 진행됨

        pygame.init()


initGame()
runGame()

```

<br>

뭐가 문제지 ??