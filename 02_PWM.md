# PWM(Pulse Width Modulation) 정리

## PWM이란?

Pulse : 사각파

Width : 폭

Modulation : 변조

사각파의 폭을 제어한다는 의미

<img width="434" height="109" alt="image" src="https://github.com/user-attachments/assets/193393b6-379d-4f62-ae54-a6d3be656029" />

## PWM 사용 이유

마이크로프로세서는 기본적으로 디지털 방식으로 연산하고 출력

디지털 출력은 기본적으로

0(LOW) / 1(HIGH)

두 가지 상태만 가질 수 있음

그런데 LED의 밝기나 모터의 속도처럼 출력의 크기를 조절해야 하는 경우가 있다.

해결방법: 디지털 신호인 0과 1을 빠르게 반복하고, 듀티비에 따른 평균적인 전압 효과를 이용하여 출력의 크기를 조절한다.

**⇒PWM은 디지털 신호를 빠르게 ON/OFF하여 아날로그적인 효과를 만들어내는 방법**



## Duty Cycle (듀티비) [%]

한 주기 안에서 신호가 on 되어 있는 비율

$$\text{Duty Cycle} = \frac{\text{ON 시간}}{\text{전체 주기}} \times 100(\\%)$$

- 0% : 항상 OFF
- 50% : 절반 ON
- 100% : 항상 ON


<img width="398" height="484" alt="image" src="https://github.com/user-attachments/assets/9d93cda0-efb1-4987-b73d-e6e48630c6be" />


## FAST PWM


<img width="548" height="230" alt="image" src="https://github.com/user-attachments/assets/38b702e2-897b-4169-9f9a-6d56f5469e20" />



BOTTOM에서 TOP까지 카운트를 진행하는 상향 카운트만 존재: 단일 경사 모드 (Single Slope Mode)

  – 카운트 값이 BOTTOM일 때 파형 출력 핀으로 HIGH 출력 (비반전)

  – 비교 일치가 발생하면 파형 출력 핀으로 LOW 출력 (비반전)

  – 비교 일치 값 조정에 의해 듀티 사이클 조정


## Phase Correct PWM

<img width="592" height="263" alt="image" src="https://github.com/user-attachments/assets/926c9e5e-adc2-45cf-abf8-7419ab609052" />

BOTTOM에서 TOP까지 상향카운트 후 TOP에서 BOTTOM으로 하향 카운트: 이중 경사 모드 (Dual Slope Mode)
  
  – 상향 카운트에서 비교 일치가 발생하면 파형 출력 핀으로 LOW 출력(비반전)
  
  – 하향 카운트에서 비교 일치가 발생하면 파형 출력 핀으로 HIGH 출력(비반전)


## PWM 활용

**LED 밝기 제어**


<img width="495" height="287" alt="image" src="https://github.com/user-attachments/assets/195262df-8fe1-47ac-a7f3-2e7f21357b96" />



Duty ↑ → LED가 켜져 있는 시간이 증가 → 더 밝게 보임 

Duty ↓ → LED가 켜져 있는 시간이 감소 → 더 어둡게 보임


PWM 주파수가 충분히 높으면 사람이 LED의 ON/OFF를 하나씩 구분하지 못하고 평균적인 밝기로 인식




**모터 속도 제어**

<img width="598" height="199" alt="image" src="https://github.com/user-attachments/assets/de9fe3f4-f470-44d9-9b21-1062ba63f634" />

마이크로 프로세서(AVR)---증폭기(모터 드라이버, L298)---시스템(모터)

Duty ↑ → 모터에 전달되는 평균적인 에너지 ↑ → 속도 ↑


Duty ↓ → 전달되는 에너지 ↓ → 속도 ↓


## 주기와 주파수




**Period(주기)**

⇒ 신호가 한 번 반복되는 데 걸리는 시간

**Frequency(주파수)**

⇒ 신호의 주기가 1초에 몇 번 반복되는지를 나타내는 값



$$
f=\frac{1}{T}
$$

주기가 짧아질수록 → 주파수는 높아짐


주기가 길어질수록 → 주파수는 낮아짐



예를 들어 주기(T)가 1ms라면

$$
f=\frac{1}{0.001}=1000Hz=1kHz
$$

즉, 1초에 1,000번 반복되는 PWM 신호​가 됨




## 분주비(Prescaler)

**타이머에 들어가는 클럭의 속도를 나눠주는 비율**

**• 분주비를 사용하는 이유**

  타이머에 들어가는 클럭 주파수를 의도적으로 낮추기 위해
  
  ⇒ 타이머에 공급되는 클럭을 나누어 타이머의 동작 주파수를 낮춘다

