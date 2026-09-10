# 1. In 32-bit mode, aside from the stack pointer (ESP), what other register points to variables on the stack? 
(32비트 모드에서 스택 포인터(ESP) 외에 스택상의 변수를 가리키는 다른 레지스터는 무엇인가?)

## 정답 및 해설

* **정답:** EBP (Extended Base Pointer, 베이스 포인터), 흔히 프레임 포인터(Frame Pointer)라고 부릅니다.
* **해설:**
  * **EBP (Base Pointer):** 함수가 호출될 때 생성되는 스택 프레임의 기준점(고정점) 역할을 합니다. 함수가 실행되는 동안 EBP의 값은 유지되므로, 컴파일러는 이를 기준으로 일정한 오프셋(예: `[ebp-4]`, `[ebp+8]`)을 적용하여 지역 변수나 매개변수에 안정적으로 접근합니다.
  * **ESP (Stack Pointer):** 스택의 가장 꼭대기(Top)를 가리킵니다. 데이터를 넣고(push) 뺄 때마다(pop) 주소가 계속해서 동적으로 변하기 때문에, 변수의 위치를 고정해서 가리키는 용도로는 사용하기 어렵습니다.
