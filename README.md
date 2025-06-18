# 🚨 재난 상황 활용 로봇 🤖

## 프로젝트 진행 상황
🏷️ [1. 2025. 06. 11.](#1-2025-06-11)

## 1. 2025. 06. 11.
🏷️ [1. 프로젝트 계획 수립](#1-프로젝트-계획-수립)<br>
🏷️ [2. Arduino IDE에서 ESP32 보드 설정 및 테스트](#2-arduino-ide에서-esp32-보드-설정-및-테스트)

### 1. 프로젝트 계획 수립
![프로젝트 계획 수립](https://github.com/haeun0908/Project_Daejeon/blob/main/images/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EA%B3%84%ED%9A%8D%20%EC%88%98%EB%A6%BD.jpg)

### 2. Arduino IDE에서 ESP32 보드 설정 및 테스트
- 아두이노 개발 환경에 ESP32 보드를 설치<br>
(참고: https://m.blog.naver.com/mapes_khkim/222901956974)<br>
![ESP32 보드 설치](https://github.com/haeun0908/Project_Daejeon/blob/main/images/ESP32%20%EB%B3%B4%EB%93%9C%20%EC%84%A4%EC%B9%98.png)

- ESP32 모듈을 USB 케이블을 이용하여 PC와 연결<br>
![ESP32 모듈 연결](https://github.com/haeun0908/Project_Daejeon/blob/main/images/ESP32%20%EB%AA%A8%EB%93%88%20%EC%97%B0%EA%B2%B0.jpg)

- Arduino IDE → [Tools] 메뉴 → **보드 선택**<br>
(참고: 일반적으로 ESP32 Dev Module 사용)<br>
![보드 선택](https://github.com/haeun0908/Project_Daejeon/blob/main/images/%EB%B3%B4%EB%93%9C%20%EC%84%A0%ED%83%9D.png)

- Arduino IDE → [Tools] 메뉴 → **포트 설정**<br>
(참고: 장치 관리자 → 포트(COM & LPT) 항목에서 포트 번호를 확인)<br>
(예: COM5 / 포트 번호는 PC 환경에 따라 다른 번호로 표시)<br>
![포트 설정](https://github.com/haeun0908/Project_Daejeon/blob/main/images/%ED%8F%AC%ED%8A%B8%20%EC%84%A4%EC%A0%95.png)
![포트 설정(2)](https://github.com/haeun0908/Project_Daejeon/blob/main/images/%ED%8F%AC%ED%8A%B8%20%EC%84%A4%EC%A0%95(2).png)

- Adeept_Moter_For_ESP32.h 라이브러리를 사용하여 두 개의 모터(M1, M2)를 **앞/뒤 회전 → 정지**하는 동작 반복 테스트<br>
(참고: 해당 라이브러리는 별도로 파일 첨부)<br>
```
/**********************************************************************
  Description : Adjust the servo to the middle position.
  Auther      : www.adeept.com
  Modification: 2023/05/31
**********************************************************************/
#include "Adeept_Motor_For_ESP32.h"

void setup()  // Execute only once.
{
  PCA9685_Setup();       //Initializes the chip that controls the motor
  
  // Motor(MotorID, Direction, MotorSpeed)
  // MotorID: 1-4 (M1, M2, M3, M4)
  // Direction: 1 or -1 (1:forward, -1:backward)
  // MotorSpeed: 0-100 (0:stop)
  /*
  Motor(1, 1, 50); // The motor turns for 3 seconds.
  Motor(2, -1, 50); // The motor turns for 3 seconds.
  delay(1000);      // delay 3s.
  Motor(1, 1, 0);   //stop
  Motor(2, -1, 0);
  delay(1000);
  */
}

void loop()
{
  Motor(1, 1, 50); // The motor turns for 3 seconds.
  Motor(2, -1, 50); // The motor turns for 3 seconds.
  delay(1000);      // delay 3s.
  Motor(1, 1, 0);   //stop
  Motor(2, -1, 0);
  delay(1000);

  Motor(1, -1, 50); // The motor turns for 3 seconds.
  Motor(2, 1, 50); // The motor turns for 3 seconds.
  delay(1000);      // delay 3s.
  Motor(1, -1, 0);   //stop
  Motor(2, 1, 0);
  delay(1000);
}

```
![동작 반복 테스트](https://github.com/haeun0908/Project_Daejeon/blob/main/images/%EB%8F%99%EC%9E%91%20%EB%B0%98%EB%B3%B5%20%ED%85%8C%EC%8A%A4%ED%8A%B8.gif)
