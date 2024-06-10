---
# 프로젝트 주제
---

![header](https://capsule-render.vercel.app/api?type=venom&color=0:5DEBD7,100:b678c4&height=200&section=header&text=AVR_WashingMachine&fontSize=40)

---
## 작품 기간 : 24.01.15 ~ 24.01.22
---
## 주제 선정
CodeVisionAVR과 ATmega128a를 사용해 가정용 세탁 기능을 추가한 세탁기 구현

## 기술 구현 목표
- 표준 세탁, 탈수, 쾌속 세탁 기능을 PWM으로 속도 차이를 주고, 속도를 LED를 통해 게이지 표현
- LCD에는 실행 동작 메시지 출력

📌 기능 구현
1. dc모터 > 동작 PORTB
2. led > DC Motor 세기 조절 PORTA
3. lcd > PORTC에 연결
4. 버튼 1, 2, 3, 4, 5 각각 PORTD.4, PORT.5, PORTD.6, PORTD.7 설정
5. 버튼1. On / Off
6. 버튼2. 표준 세탁 - 지정 된 시간 동안 표준 속도로 정 방향 역 방향 세탁
7. 버튼3. 탈수 - 지정 된 시간 동안 한 방향으로 회전
8. 버튼 2 & 3. 쾌속 세탁 - 지정 된 시간 동안 빠른  속도로 정 방향 역 방향 세탁
9. 버튼4. 시작 - Start(세탁 중 누르면 Pause)

함수
- 표준 세탁 2분에 세기 5
- 쾌속 세탁 1분에 세기 10
- 탈수 2분에 세기 8

## 기대 효과
- AVR을 통해 다양한 기능 구현
- 버튼 입력을 통해 LCD 출력
- DC Motor 세기에 따른 LED 변화
- 함수 동작의 끝을 알리는 스피커
- 다중 입력을 통한 버튼 제어
---
## 구성도
![image](https://github.com/BChanGod/AVR_WashingMachine/assets/159971128/9710092e-9dc1-4723-a2bc-00c9628062ec)

## 주요 특징 및 핵심 기술 / 회로도 절차
![image](https://github.com/BChanGod/AVR_WashingMachine/assets/159971128/931d30e6-0035-4bf8-b546-d476c240ae34)
![image](https://github.com/BChanGod/AVR_WashingMachine/assets/159971128/2e8d465e-5c99-4c67-afc8-6f3e5e69a477)


## 하드웨어
- 사진은 순서대로 하드웨어 초기 구현, 하드웨어 설계 후 내부, 최종 모형 외부 사진
---
![image](https://github.com/BChanGod/AVR_WashingMachine/assets/159971128/a5c40686-a685-429c-8597-c65edcd94e48)
![image](https://github.com/BChanGod/AVR_WashingMachine/assets/159971128/4607279e-d5bc-47fe-bce4-17f08302ceb7)
![모형_외부](https://github.com/BChanGod/AVR_WashingMachine/assets/159971128/52c0b695-102d-47b8-8e6c-d7a1a06d3b9f)

---
## 개발 환경
| Board | ATmega128a |
| --- | --- |
| Language |C|
| Device | DC Motor, LCD, 10-segment LED, PushButton, 4.7KΩ, AVR 가변저항, Buzzer |
| System | CodeVisionAVR |

## 프로젝트 팀원
|  | 이  름 | 역할 분담 |
| --- | --- | --- |
| 팀장 | 김용기 | LCD, DC Motr, Button 제어, main 코드 작성 |
| 팀원 | 김예빈 | DC Motor 세기에 따라 LED 나타내는 코드 작성 |
| 팀원 | 이민규 | Motor가 멈추면 Buzzer로 알림, 회로도 구성 |
| 팀원 | 이병찬 | DC Motor, 각 구동 시스템 코드 통합, 기능 보완, 하드웨어 설계 연결 및 동작 검증 |

# 개발 일정
![image](https://github.com/BChanGod/AVR_WashingMachine/assets/159971128/cce3174d-1015-4240-b327-266007fe3f66)

## 문제점
< 하드웨어 >
- 하드웨어 모형과 빵판에 LED와 LCD를 연장선으로 연결하기 때문에 접촉 불량이 생겨 밝기가 약해진다.

< 소프트웨어 >
- 여러 개의 버튼을 동작하다 보니 다중 입력 시 인식이 잘 안 된다.

## 해결 방안
< 하드웨어 >
- LED와 LCD 핀에 맞는 사이즈의 암, 수를 연결하면 됐으나, 사이즈가 맞는 선이 없어 테이프와 글루건으로 고정하였다.

< 소프트웨어 >
- 버튼 입력에 대한 인터럽트를 사용하여 버튼의 우선순위를 두어 신속하게 신호를 감지, 인터럽트를 사용하여 다중 입력을 놓치지 않고 정확한 신호 처리가 가능하도록 보완하였다.

## 향후 목표
- 인터럽트를 사용해 버튼 하나로 1~개의 기능이 아닌 Mode 선택으로 기능 안에 진입하여 여러 기능을 선택할 수 있는 기능 추가
