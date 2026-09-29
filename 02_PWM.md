# PWM(Pulse Width Modulation) 정리

## PWM 사용 이유

마이크로프로세서는 기본적으로 디지털 방식으로 연산하고 출력

디지털 출력은 기본적으로

0(LOW) / 1(HIGH)

두 가지 상태만 가질 수 있음

그런데 LED의 밝기나 모터의 속도처럼 출력의 크기를 조절해야 하는 경우가 있다.

그렇다면 디지털 신호인 0과 1을 빠르게 반복하여 평균을 통해 전압을 조절 한다.

**=>PWM은 디지털 신호를 이용해서 아날로그적인 효과를 만들어내는 방법**


## PWM이란?

Pulse : 사각파

Width : 폭

Modulation : 변조

사각파의 폭을 제어한다는 의미

<img width="434" height="109" alt="image" src="https://github.com/user-attachments/assets/193393b6-379d-4f62-ae54-a6d3be656029" />

## Duty Cycle [%]

한 주기 안에서 신호가 on 되어 있는 비율

= (ON 시간 / 전체 주기) × 100


- 0% : 항상 OFF
- 50% : 절반 ON
- 100% : 항상 ON


<img width="398" height="484" alt="image" src="https://github.com/user-attachments/assets/9d93cda0-efb1-4987-b73d-e6e48630c6be" />


## PWM 활용

**LED 밝기 제어**


<img width="564" height="282" alt="image" src="https://github.com/user-attachments/assets/a385938c-4933-4307-a634-03a7ca82726b" />


Duty ↑ → LED가 켜져 있는 시간이 증가 → 더 밝게 보임 

Duty ↓ → LED가 켜져 있는 시간이 감소 → 더 어둡게 보임


PWM 주파수가 충분히 높으면 사람이 LED의 ON/OFF를 하나씩 구분하지 못하고 평균적인 밝기로 인식




**모터 속도 제어**

Duty ↑ → 모터에 전달되는 평균적인 에너지 ↑ → 속도 ↑


Duty ↓ → 전달되는 에너지 ↓ → 속도 ↓

## Duty Cycle과 주파수, 주기


**Duty Cycle**
→ 한 주기에서 신호가 ON(HIGH) 상태로 유지되는 비율


**Frequency(주파수)**
→ 신호의 주기가 1초에 몇 번 반복되는지를 나타내는 값


**Period(주기)**
→ 신호가 한 번 반복되는 데 걸리는 시간

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







