# UART1 설정 방법
1. PIN 설정에서 PA9와 PA10을 먼저 UART1으로 설정
2. UART1에서 Async 모드로 설정 -> GPIO tab에서 PA9와 PA10이 잡히는지 확인
3. printf에서 floating을 사용할 경우, Project 우클릭 -> Properties -> C/C++ Build -> Settings -> Tool Settings -> MCU GCC Linker -> Miscellaneous에서 -u_printf_float 추가