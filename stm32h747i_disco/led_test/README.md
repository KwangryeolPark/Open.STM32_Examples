# led_test
* 보드 전면부 좌측에 부착된 LED1~4를 제어하는 예시입니다.

<br>

# 기본 용어
| 용어 | 의미 | Full name |
| --- | --- | --- |
| GPIO | 다목적 입출력 포트. 즉, LED를 제어할 때 사용하는 포트들을 의미. A, B, D 등의 channels이 존재. | **G**erneral **P**urpose **I**nput and **O**utput |
| GPIOI | GPIO 중, I channel | GPIO I channel |
| PIN | GPIO의 특정 핀을 의미. GPIO_PIN_13은 코드 상에서 13번째 핀을 의미. |  |
| Port | PIN와 동일시 여겨짐 |  |
| PI13 | GPIO I channel의 13번째 핀의 실제 명칭. |  |

<br>

# 프로젝트 불러오기
* "STMCubeIDE 실행 -> File -> Open Projects From File System... -> Directory..."를 눌러 led_test 폴더 선택.

<br>

# 실행 방법
1. Run -> Run Configurations... -> STM32 C/C++ Application -> led_test_CM4 Debug -> Main 탭 누르기 -> 중앙 Build Cnofiguration을 Debug로 수정 -> Debugger 탭 누르기 -> Interface에 ST-LINK S/N check -> Scan 버튼 누르고 잠시 기다리기 (어떤 코드가 나올 때까지).
2. Apply
3. Run
4. 같은 창에서 led_test_CM7 Debug -> Main 탭 누르기 -> 중앙 Build Cnofiguration을 Debug로 수정 -> Debugger 탭 누르기 -> Interface에 ST-LINK S/N check -> Scan 버튼 누르고 잠시 기다리기 (어떤 코드가 나올 때까지).
5. Apply
6. Run

<br>

# 코드 설명
led_test_CM7/Core/Src/main.c line 120 ~ 144
```C++
  MX_GPIO_Init();   //  GPIO 관련된 설정들을 초기화 합니다.
  /* USER CODE BEGIN 2 */
  HAL_GPIO_WritePin(GPIOI, GPIO_PIN_12, GPIO_PIN_SET);	//	LED1 off
  HAL_GPIO_WritePin(GPIOI, GPIO_PIN_13, GPIO_PIN_SET);	//	LED2 off
  HAL_GPIO_WritePin(GPIOI, GPIO_PIN_14, GPIO_PIN_SET);	//	LED3 off
  HAL_GPIO_WritePin(GPIOI, GPIO_PIN_15, GPIO_PIN_SET);	//	LED4 off

  /* USER CODE END 2 */

  /* Infinite loop */
  /* USER CODE BEGIN WHILE */
  while (1)
  {
    /* USER CODE END WHILE */
	  HAL_GPIO_WritePin(GPIOI, GPIO_PIN_12, GPIO_PIN_RESET);	//	LED1 on
	  HAL_Delay(500);	//	500 ms delay
	  HAL_GPIO_WritePin(GPIOI, GPIO_PIN_13 | GPIO_PIN_14, GPIO_PIN_RESET);	//	LED2 and 3 on
	  HAL_Delay(500);	//	500 ms delay
	  HAL_GPIO_WritePin(GPIOI, GPIO_PIN_15, GPIO_PIN_RESET);	//	LED4 on
	  HAL_GPIO_WritePin(GPIOI, GPIO_PIN_12, GPIO_PIN_SET);	//	LED1 off
	  HAL_Delay(500);	//	500 ms delay
	  HAL_GPIO_WritePin(GPIOI, GPIO_PIN_13 | GPIO_PIN_14 | GPIO_PIN_15, GPIO_PIN_SET);	//	LED2, 3 and 4 off
	  HAL_Delay(500);	//	500 ms delay
    /* USER CODE BEGIN 3 */
  }
```