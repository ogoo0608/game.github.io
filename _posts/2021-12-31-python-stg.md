---
layout: single
title: "간단한 슈팅 게임 만들기 프로젝트"
toc: true
toc_sticky: true
toc_label: "On This Page"
categories:
    - Project
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

<br>

<br>


일어나서 다시 보니까 멍청하게도 그냥 들여쓰기 문제였다.. ^^ .. 

앞으로는 파이썬이 indent 에 매우 민감한 언어라는걸 상기하자 !!!

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

## 6-1 미사일 발사하기

<br>

가장 먼저 missile image png 파일이 업로듣 되도록 코딩해주고

global 변수에 missile 을 추가한 뒤, 무기 좌표 리스트를 추가해준다..

```py
elif event.key == pygame.K_SPACE:
                    missileX = x + fighterWidth/2
                    missileY = y - fighterHeight
                    missileXY.append([missileX, missileY])
```

<br>

스페이스바를 눌렀을 때 미사일이 발사되도록 위와 같은 코드를 입력해주고,

<br>

```py
if len(missileXY) != 0:
            for i, bxy in enumerate(missileXY):
                bxy[1] -= 10
                missileXY[i][1] = bxy[1]

                if bxy[1] <= 0:
                    try:
                        missileXY.remove(bxy)
                    except:
                        pass

        if len(missileXY) != 0:
            for bx, by in missileXY:
                drawObject(missile, bx, by)
```

미사일이 발사되는 형태를 구현하기 위해 위와 같은 코드를 입력해준다 !!

<br>

## 6-2 랜덤한 운석 떨어지기

<br>

```py
import random
```

<br>

```py
rockImage = ['rock01.png','rock02.png','rock03.png','rock04.png','rock05.png',
             'rock06.png','rock07.png','rock08.png','rock09.png','rock10.png',
             'rock11.png','rock12.png','rock13.png','rock14.png','rock15.png',
             'rock16.png','rock17.png','rock18.png','rock19.png','rock20.png',
             'rock21.png','rock22.png','rock23.png','rock24.png','rock25.png',
             'rock26.png','rock27.png','rock28.png','rock29.png','rock30.png',]

```

<br>

사실 이미지 하나만 써도 되는데, 그러면 재미가 떨어지기 때문에 리소스 파일에 있는 

모든 이미지를 넣어주었다 .. ^^

<br>

```py
# 운석 랜덤 생성
    rock = pygame.image.load(random.choice(rockImage))
    rockSize = rock.get_rect(),size
    rockWidth = rockSize[0]
    rockHeight = rockSize[1]
```

<br>

```py
# 운석 초기 위치 설정
    rockX = random.randrange(0, padWidth - rockWidth)
    rockY = 0
    rockSpeed = 2
```

<br>

```py
rockY += rockSpeed # 운석이 아래로 향하게


        if rockY > padHeight :

            rock = pygame.image.load(random.choice(rockImage))
            rockSize = rock.get_rect().size
            rockWidth = rockSize[0]
            rockHeight = rockSize[1]
            rockX = random.randrange(0, padWidth - rockWidth)
            rockY = 0

        drawObject(rock, rockX, rockY) # 운석 그리기
```

<br>

## 7. 미사일로 운석 파괴하기

<br>

```py
explosion = pygame.image.load('exlosion.png')
```

<br>

```py
isShot = False
shotCount = 0
reockPassed = 0
```

<br>

global 변수에 explosion 추가는 필수 .. ^^

<br>

```py
if bxy[1] < rockY:
                    if bxy[0] > rockX and bxy[0] < rockX + rockWidth:
                        missileXY.remove(bxy)
                        isShot = True
                        shotCount += 1
```

<br>

```py
if isShot:
            drawObject(explosion, rockX, rockY)
            rock = pygame.image.load(random.choice(rockImage))
            rockSize = rock.get_rect().size
            rockWidth = rockSize[0]
            rockHeight = rockSize[1]
            rockX = random.randrange(0, padWidth - rockWidth)
            rockY = 0
            isShot = False
```

<br>

## 8. 파괴한 운석 수 & 놓친 운석 수 표시하기

<br>

```py
def writeScore(count):
    global gamePad
    font = pygame.font.Font('NanumGothic.ttf', 15)
    text = font.render('파괴한 운석 수 :' + str(count), True, (255, 255, 255))
    gamePad.blit(text,(10,0))

def writePassed(count):
    global gamePad
    font = pygame.font.Font('NanumGothic.ttf', 15)
    text = font.render('놓친 운석 수  :' + str(count), True, (255, 0, 0))
    gamePad.blit(text,(360,0))

```

def 를 이용하여 writeScore & writePassed 를 정의한다.

```py
writeScore(shotCount)
```

```py
isShot = False
    shotCount = 0
    rockPassed = 0
```

<br>

```py
rockPassed += 1


        writePassed(rockPassed)
```

<br>

## 8-1. 운석 맞추면 운석 속도 증가하기

<br>

```py
        if isShot:
```

<br>

위와 같은 if문에 아래와 같은 코드를 삽입하자.

<br>



```py
rockSpeed += 0.05
            if rockSpeed >= 10:
                rockSpeed = 10
```

<br>

운석이 미사일에 맞으면 속도가 0.05 씩 증가한다. !!

<br>

## 9. 전투기가 운석과 충돌하거나 놓치면 게임 오버

<br>

```py
def writeMessage(text):
    global gamePad,gameoverSound
    textfont = pygame.font.Font('NanumGothic.ttf', 70)
    text = textfont.render(text, True, (255,0,0))
    textpos = text.get_rect()
    textpos.center = (padWidth/2, padHeight/2)
    gamePad.blit(text, textpos)
    pygame.display.update()
    pygame.mixer.music.stop() # 배경 음악 정지 !
    gameoverSound.play() # 게임 오버 사운드 재생 ! 
    sleep(2)
    pygame.mixer.music.play(-1) # 배경 음악 재생 !!
    runGame()

def crash():
    global gamePad
    writeMessage('Fighter is Destroyed!')

def gameOver():
    global gamePad
    writeMessage('Game Over!')

```

<br>

## 10. 완성 코드

<br>

```py
import pygame
import sys
import random
from time import sleep


padWidth = 480 # 게임 화면 크기 
padHeight = 640
rockImage = ['rock01.png','rock02.png','rock03.png','rock04.png','rock05.png', 
             'rock06.png','rock07.png','rock08.png','rock09.png','rock10.png', 
             'rock11.png','rock12.png','rock13.png','rock14.png','rock15.png', 
             'rock16.png','rock17.png','rock18.png','rock19.png','rock20.png', 
             'rock21.png','rock22.png','rock23.png','rock24.png','rock25.png', 
             'rock26.png','rock27.png','rock28.png','rock29.png','rock30.png']
explosionSound = ['explosion01.wav','explosion02.wav','explosion03.wav','explosion04.wav']

def writeScore(count):
    global gamePad
    font = pygame.font.Font('NanumGothic.ttf', 15)
    text = font.render('Destroyed meteorite : ' + str(count), True, (255, 255, 255))
    gamePad.blit(text,(10,0))

def writePassed(count):
    global gamePad
    font = pygame.font.Font('NanumGothic.ttf', 15)
    text = font.render('Missed meteorite  : ' + str(count), True, (255, 0, 0))
    gamePad.blit(text,(360,0))


def writeMessage(text):
    global gamePad,gameoverSound
    textfont = pygame.font.Font('NanumGothic.ttf', 40)
    text = textfont.render(text, True, (255,0,0))
    textpos = text.get_rect()
    textpos.center = (padWidth/2, padHeight/2)
    gamePad.blit(text, textpos)
    pygame.display.update()
    pygame.mixer.music.stop()
    gameoverSound.play()
    sleep(2)
    pygame.mixer.music.play(-1)
    runGame()

def crash():
    global gamePad
    writeMessage('Fighter is Destroyed!')

def gameOver():
    global gamePad
    writeMessage('Game Over!')



def drawObject(obj, x, y): # 게임에 등장하는 객체를 드로잉
    global gamePad
    gamePad.blit(obj, (x,y)) # blit 이란, 비티 현상과 관련해서 해당하는 오브젝트를 x, y 좌표 위치로부터 그려라라는 의미 !!


def initGame(): # 게임 초기화를 위한 함수 'initGame'
    global gamePad, clock, background, fighter, missile, explosion, missileSound, gameOverSound # global 변수
    pygame.init()
    gamePad = pygame.display.set_mode((padWidth, padHeight))
    pygame.display.set_caption('PyShooting') # 게임의 이름 !!
    background = pygame.image.load('background.png')
    fighter = pygame.image.load('fighter.png')
    missile = pygame.image.load('missile.png')
    explosion = pygame.image.load('explosion.png')
    pygame.mixer.music.load('music.wav')
    pygame.mixer.music.play(-1)
    missileSound = pygame.mixer.Sound('missile.wav')
    gameOverSound = pygame.mixer.Sound('gameover.wav')
    clock = pygame.time.Clock()


def runGame(): # 실질적으로 게임이 실행될 수 있는 함수인 rungame
    global gamepad, clock, background, fighter, missile, explosion, missileSound # 정엽변수 불러와야 함 ....

    fighterSize = fighter.get_rect().size
    fighterWidth = fighterSize[0]
    fighterHeight = fighterSize[1]

    x = padWidth * 0.45 # 폭에서 0.45 위치
    y = padHeight * 0.9 # 높이에서 0.9 위치
    fighterX = 0

    missileXY = [] # 무기 좌표 리스트

# 운석 랜덤 생성
    rock = pygame.image.load(random.choice(rockImage))
    rockSize = rock.get_rect().size
    rockWidth = rockSize[0]
    rockHeight = rockSize[1]
    destroySound = pygame.mixer.Sound(random.choice(explosionSound))

# 운석 초기 위치 설정
    rockX = random.randrange(0, padWidth - rockWidth)
    rockY = 0
    rockSpeed = 2

    isShot = False
    shotCount = 0
    rockPassed = 0


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

                elif event.key == pygame.K_SPACE:
                    missileSound.play()
                    missileX = x + fighterWidth/2
                    missileY = y - fighterHeight
                    missileXY.append([missileX, missileY])
                

            if event.type in [pygame.KEYUP]: # 방향키를 떼면 전투기가 멈춤
                if event.key == pygame.K_LEFT or event.key == pygame.K_RIGHT:
                    fighterX = 0



        drawObject(background, 0, 0)

        x += fighterX
        if x < 0: # x 가 0보다 작을 경우 : 게임 왼쪽 끝까지 가는 경우를 의미..
            x = 0 # 멈춰 !
        elif x > padWidth - fighterWidth: # 오른쪽 끝까지  갔을 때
            x = padWidth - fighterWidth # 멈춰 !!


        if y < rockY + rockHeight:
            if(rockX > x and rockX < x + fighterWidth) or \
                (rockX + rockWidth > x and rockX + rockWidth):
                crash()

        drawObject(fighter, x, y)

        if rockPassed == 3:
            gameOver()

        if len(missileXY) != 0:
            for i, bxy in enumerate(missileXY):
                bxy[1] -= 10
                missileXY[i][1] = bxy[1]

                if bxy[1] < rockY:
                    if bxy[0] > rockX and bxy[0] < rockX + rockWidth:
                        missileXY.remove(bxy)
                        isShot = True
                        shotCount += 1

                if bxy[1] <= 0:
                    try:
                        missileXY.remove(bxy)
                    except:
                        pass

        if len(missileXY) != 0:
            for bx, by in missileXY:
                drawObject(missile, bx, by)

        writeScore(shotCount)

        rockY += rockSpeed # 운석이 아래로 향하게


        if rockY > padHeight :

            rock = pygame.image.load(random.choice(rockImage))
            rockSize = rock.get_rect().size
            rockWidth = rockSize[0]
            rockHeight = rockSize[1]
            rockX = random.randrange(0, padWidth - rockWidth)
            rockY = 0
            rockPassed += 1


        writePassed(rockPassed)


        if isShot:
            drawObject(explosion, rockX, rockY)
            destroySound.play()
            rock = pygame.image.load(random.choice(rockImage))
            rockSize = rock.get_rect().size
            rockWidth = rockSize[0]
            rockHeight = rockSize[1]
            rockX = random.randrange(0, padWidth - rockWidth)
            rockY = 0
            destroySound = pygame.mixer.Sound(random.choice(explosionSound))
            isShot = False

            rockSpeed += 0.05
            if rockSpeed >= 10:
                rockSpeed = 10

        drawObject(rock, rockX, rockY) # 운석 그리기
                     

        pygame.display.update() # 게임 화면을 다시 그림

        clock.tick(60) # 초당 프레임 수를 60으로 설정하여 게임 플레이가 초당 60으로 진행됨

    pygame.init()


initGame()
runGame()
```

<br>

>간단한 갤러그 같은 게임임에도 꽤나 긴 코드를 작성해야 한다는 점에서 놀라웠다. !!
>>타인이 올린 자료를 보고 그저 코드를 따라서 적었을 뿐인데도 많은 공부가 되었다.
>>>아주 재밌었다 ... 이 코드를 이용해서 나만의 게임도 만들면서 공부할 것이다.
>>>>일단 계절학기가 우선이지만 방학동안 많은 분야를 경험하고 싶다.