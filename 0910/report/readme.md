# 1. In 32-bit mode, aside from the stack pointer (ESP), what other register points to variables on the stack? 
(32비트 모드에서 스택 포인터(ESP) 외에 스택상의 변수를 가리키는 다른 레지스터는 무엇인가?)

## 정답 및 해설

* **정답:** EBP (Extended Base Pointer, 베이스 포인터), 흔히 프레임 포인터(Frame Pointer)라고 부릅니다.
* **해설:**
  * **EBP (Base Pointer):** 함수가 호출될 때 생성되는 스택 프레임의 기준점(고정점) 역할을 합니다. 함수가 실행되는 동안 EBP의 값은 유지되므로, 컴파일러는 이를 기준으로 일정한 오프셋(예: `[ebp-4]`, `[ebp+8]`)을 적용하여 지역 변수나 매개변수에 안정적으로 접근합니다.
  * **ESP (Stack Pointer):** 스택의 가장 꼭대기(Top)를 가리킵니다. 데이터를 넣고(push) 뺄 때마다(pop) 주소가 계속해서 동적으로 변하기 때문에, 변수의 위치를 고정해서 가리키는 용도로는 사용하기 어렵습니다.
---

# 2. Name at least four CPU status flags.
(CPU 상태 플래그를 최소 4개 이상 나열하시오.)

## 정답 및 해설

* **정답:** CF, ZF, SF, OF (이 외에도 PF, AF 등이 있습니다.)
* **해설:**
  * **CF (Carry Flag, 캐리 플래그):** 부호 없는 연산에서 자리올림(Carry)이나 자리내림(Borrow)이 발생했을 때 1로 설정됩니다.
  * **ZF (Zero Flag, 제로 플래그):** 연산 결과가 0일 때 1로 설정됩니다.
  * **SF (Sign Flag, 부호 플래그):** 연산 결과가 음수일 때(최상위 비트가 1일 때) 1로 설정됩니다.
  * **OF (Overflow Flag, 오버플로우 플래그):** 부호 있는 연산(Signed arithmetic) 과정에서 범위를 벗어나는 오버플로우가 발생했을 때 1로 설정됩니다.
 ---

  # 3. Which flag is set when the result of an unsigned arithmetic operation is too large to fit into the destination?
(부호 없는 산술 연산 결과가 너무 커서 목적지에 들어가지 못할 때 설정되는 플래그는 무엇인가?)

## 정답 및 해설

* **정답:** CF (Carry Flag, 캐리 플래그)
* **해설:** 부호 없는(unsigned) 연산 과정에서 데이터가 표현할 수 있는 범위를 벗어나 자리올림(Carry)이나 자리내림(Borrow)이 발생했을 때 1로 설정됩니다. 부호 있는 연산의 오버플로우는 OF(Overflow Flag)가 담당합니다.
---

# 4. Which flag is set when the result of a signed arithmetic operation is either too large or too small to fit into the destination?
(부호 있는 산술 연산 결과가 너무 크거나 작아서 목적지에 들어가지 못할 때 설정되는 플래그는 무엇인가?)

## 정답 및 해설

* **정답:** OF (Overflow Flag, 오버플로우 플래그)
* **해설:** 부호 있는(signed) 연산 과정에서 결과값이 해당 비트로 표현할 수 있는 범위를 초과하거나 미달하여 오버플로우가 발생했을 때 1로 설정됩니다. 이를 통해 부호 비트가 예상치 않게 변경되었음을 감지할 수 있습니다.
---

# 5. (True/False): When a register operand size is 32 bits and the REX prefix is used, the R8D register is available for programs to use.
((참/거짓): 레지스터 피연산자 크기가 32비트이고 REX 접두사가 사용될 때, R8D 레지스터를 프로그램에서 사용할 수 있다.)

## 정답 및 해설

* **정답:** True (참)
* **해설:** x86-64 아키텍처에서 REX 접두사(REX prefix)는 64비트 확장 레지스터인 R8부터 R15까지에 접근할 수 있게 해줍니다. 여기서 `R8D`는 R8 레지스터의 32비트(Doubleword) 하위 레지스터를 의미하며, REX 접두사를 통해 프로그램에서 사용할 수 있습니다.
---

# 6. Which flag is set when an arithmetic or logical operation generates a negative result?
(산술 또는 논리 연산 결과가 음수를 생성할 때 설정되는 플래그는 무엇인가?)

## 정답 및 해설

* **정답:** SF (Sign Flag, 부호 플래그)
* **해설:** 산술 또는 논리 연산 결과의 최상위 비트(MSB)가 1이 되어 결과가 음수임을 나타낼 때 1로 설정됩니다.
---

# 7. Which part of the CPU performs floating-point arithmetic?
(CPU의 어떤 부분이 부동소수점 산술 연산을 수행하는가?)

## 정답 및 해설

* **정답:** FPU (Floating Point Unit, 부동소수점 유닛), 또는 수학 보조프로세서(Math Coprocessor / x87 FPU)
* **해설:** CPU 내에서 정수 연산은 ALU(Arithmetic Logic Unit)가 담당하는 반면, 소수점이 있는 부동소수점(floating-point) 연산은 FPU라는 전용 하드웨어 유닛이 처리합니다. 현대의 CPU는 이 FPU가 프로세서 코어 내부에 통합되어 있습니다.
---

# 8. On a 32-bit processor, how many bits are contained in each floating-point data register?
(32비트 프로세서에서 각 부동소수점 데이터 레지스터에는 몇 개의 비트가 포함되어 있는가?)

## 정답 및 해설

* **정답:** 80 bits (80비트)
* **해설:** x86 아키텍처의 x87 FPU(부동소수점 유닛) 데이터 레지스터(`ST(0)` ~ `ST(7)`)는 기본적으로 80비트(Double-Extended Precision)의 정밀도로 데이터를 처리하고 저장합니다. 프로세서가 32비트 시스템이라 하더라도 부동소수점 레지스터의 크기는 80비트입니다.
---

# 9. (True/False): The x86-64 instruction set is backward-compatible with the x86 instruction set.
((참/거짓): x86-64 명령어 세트는 x86 명령어 세트와 하위 호환된다.)

## 정답 및 해설

* **정답:** True (참)
* **해설:** x86-64 아키텍처는 기존 32비트 및 16비트 x86 명령어 세트와 완벽한 하위 호환성(backward-compatible)을 제공하도록 설계되었습니다. 따라서 기존의 32비트 x86 프로그램과 코드를 수정 없이 64비트 환경에서도 실행할 수 있습니다.
 ---

 # 10. (True/False): In current 64-bit chip implementations, all 64 bits are used for addressing.
((참/거짓): 현재의 64비트 칩 구현에서는 64비트 전체가 주소 지정에 사용된다.)

## 정답 및 해설

* **정답:** False (거짓)
* **해설:** 현대의 64비트 프로세서(예: x86-64)는 64비트 전체를 메모리 주소 지정에 사용하지 않습니다. 일반적으로 48비트(또는 5단계 페이징을 지원하는 최신 프로세서의 경우 57비트)의 가상 주소 공간만 물리적으로 구현하여 사용하며, 나머지 상위 비트들은 예약되어 있거나 특정 규칙(Sign extension 등)을 따릅니다.
---

# 11. (True/False): The Itanium instruction set is completely different from the x86 instruction set.
((참/거짓): 아이테니엄(Itanium) 명령어 세트는 x86 명령어 세트와 완전히 다르다.)

## 정답 및 해설

* **정답:** True (참)
* **해설:** 인텔과 HP가 공동 개발한 아이테니엄(Itanium, IA-64) 아키텍처는 EPIC(Explicitly Parallel Instruction Computing) 설계 방식을 사용하여 기존의 x86 명령어 세트와는 완전히 다르며, 직접적인 호환성이 없습니다.
---

# 12. (True/False): Static RAM is usually less expensive than dynamic RAM.
((참/거짓): 정적 RAM(SRAM)은 일반적으로 동적 RAM(DRAM)보다 저렴하다.)

## 정답 및 해설

* **정답:** False (거짓)
* **해설:** SRAM(Static RAM)은 비트당 더 많은 트랜지스터(보통 6개)를 사용하여 속도가 빠른 대신 회로가 복잡하고 제조 단가가 비쌉니다. 반면 DRAM(Dynamic RAM)은 1개의 트랜지스터와 1개의 커패시터로 구성되어 집적도가 높고 가격이 훨씬 저렴합니다. 따라서 SRAM이 DRAM보다 비쌉니다.
---

# 13. (True/False): The 64-bit RDI register is available when the REX prefix is used.
((참/거짓): REX 접두사가 사용될 때 64비트 RDI 레지스터를 사용할 수 있다.)

## 정답 및 해설

* **정답:** True (참)
* **해설:** x86-64 아키텍처에서 64비트 확장 범용 레지스터 및 64비트 오퍼랜드 크기를 지정하기 위해 REX 접두사(특히 REX.W 비트 등)가 사용됩니다. 이를 통해 64비트 RDI 레지스터를 포함한 확장된 레지스터 세트를 프로그램에서 원활하게 사용할 수 있습니다.
---

# 14. (True/False): In native 64-bit mode, you can use 16-bit real mode, but not the virtual-8086 mode.
((참/거짓): 네이티브 64비트 모드에서는 16비트 리얼 모드를 사용할 수 있지만, 가상-8086 모드는 사용할 수 없다.)

## 정답 및 해설

* **정답:** False (거짓)
* **해설:** 네이티브 64비트 모드(64-bit mode)에서는 16비트 리얼 모드와 가상-8086 모드(virtual-8086 mode) **둘 다 지원되지 않습니다**. 따라서 16비트 리얼 모드를 사용할 수 있다고 한 부분 때문에 이 문장은 거짓(False)이 됩니다.
---

# 15. (True/False): The x86-64 processors have 4 more general-purpose registers than the x86 processors.
((참/거짓): x86-64 프로세서는 x86 프로세서보다 범용 레지스터가 4개 더 많다.)

## 정답 및 해설

* **정답:** False (거짓)
* **해설:** 기존 32비트 x86 프로세서는 8개의 범용 레지스터(EAX, EBX, ECX, EDX, ESI, EDI, EBP, ESP)를 가지지만, x86-64 프로세서는 여기에 R8부터 R15까지 **8개의 범용 레지스터가 추가**되어 총 16개의 범용 레지스터를 제공합니다. 따라서 4개가 아니라 8개가 더 많기 때문에 거짓(False)입니다.
---


 # 16. (True/False): The 64-bit version of Microsoft Windows does not support virtual-8086 mode.
((참/거짓): 64비트 버전의 마이크로소프트 윈도우는 가상-8086 모드를 지원하지 않는다.)

## 정답 및 해설

* **정답:** True (참)
* **해설:** 64비트 x86-64 프로세서의 하드웨어 특성상 64비트 롱 모드(Long mode)에서는 가상-8086 모드(virtual-8086 mode)가 하드웨어 레벨에서 지원되지 않습니다. 따라서 64비트 버전의 마이크로소프트 윈도우 운영체제에서도 16비트 레거시 DOS 애플리케이션 등을 실행하기 위한 가상-8086 모드를 지원하지 않습니다.
---

# 17. (True/False): DRAM can only be erased using ultraviolet (UV) light.
((참/거짓): DRAM은 자외선을 사용해서만 지워질 수 있다.)

## 정답 및 해설

* **정답:** False (거짓)
* **해설:** 자외선(UV light)을 사용하여 내용을 지우는(삭제하는) 메모리 유형은 자외선 소거형 프로그래머블 읽기 전용 메모리인 **EPROM(Erasable Programmable Read-Only Memory)**입니다. 반면, DRAM(Dynamic RAM)은 전원이 공급되는 동안 커패시터의 전하 유지를 위해 지속적인 리프레시(Refresh) 과정이 필요하며, 전원이 꺼지면 데이터가 자연스럽게 소실되는 휘발성 메모리입니다.
---


# 18. (True/False): In 64-bit mode, you can use up to eight floating-point registers.
((참/거짓): 64비트 모드에서는 최대 8개의 부동소수점 레지스터를 사용할 수 있다.)

## 정답 및 해설

* **정답:** True (참)
* **해설:** x86-64 아키텍처의 64비트 모드에서도 기존 x87 FPU(부동소수점 유닛)의 스택 구조가 유지되므로, 최대 8개의 부동소수점 데이터 레지스터(`ST(0)` ~ `ST(7)`)를 사용할 수 있습니다.
---

# 19. (True/False): A bus is a plastic cable that is attached to the motherboard at both ends, but does not sit directly on the motherboard.
((참/거짓): 버스는 양쪽 끝이 메인보드에 부착되어 있지만 메인보드 위에 직접 놓이지 않는 플라스틱 케이블이다.)

## 정답 및 해설

* **정답:** False (거짓)
* **해설:** 컴퓨터 아키텍처에서 버스(Bus)는 CPU, 메모리, I/O 장치 등 컴퓨터 내부의 다양한 부품들 간에 데이터와 제어 신호를 전송하기 위해 메인보드 회로 기판 위에 에칭(Etching)되어 있는 **전기적 배선 경로(Trace)**들을 의미합니다. 케이블이 아니라 메인보드 자체에 내장된 통로입니다.
---

# 20. (True/False): CMOS RAM is the same as static RAM, meaning that it holds its value without any extra power or refresh cycles.
((참/거짓): CMOS RAM은 정적 RAM과 같으며, 이는 추가적인 전력이나 리프레시 주기 없이 값을 유지한다는 것을 의미한다.)

## 정답 및 해설

* **정답:** False (거짓)
* **해설:** CMOS RAM은 SRAM(Static RAM) 기술을 사용하여 구현되므로 주기적인 리프레시(Refresh) 사이클은 필요로 하지 않습니다. 하지만 전원이 꺼진 상태(컴퓨터 종료 시)에서도 BIOS 설정 등의 데이터를 유지하기 위해서는 메인보드의 **CMOS 배터리로부터 지속적인 미세 전력 공급**을 받아야 합니다. 따라서 "추가적인 전력 없이" 값을 유지한다는 설명은 틀렸습니다.
---

# 21. (True/False): PCI connectors are used for graphics cards and sound cards.
((참/거짓): PCI 커넥터는 그래픽 카드와 사운드 카드에 사용된다.)

## 정답 및 해설

* **정답:** True (참)
* **해설:** PCI(Peripheral Component Interconnect) 버스 및 슬롯은 사운드 카드, 네트워크 카드, 그리고 초기 및 전통적인 그래픽 카드 등 다양한 확장 카드(expansion cards)를 메인보드에 연결하기 위해 널리 사용되어 왔습니다. (비록 현대의 고성능 그래픽 카드는 주로 PCIe(PCI Express) 슬롯을 사용하지만, 컴퓨터 구조 및 하드웨어 구성 요소 학습 과정에서는 확장 장치의 대표적인 예시로 PCI 슬롯에 그래픽 카드와 사운드 카드가 포함됩니다.)
---

# 22. (True/False): The 8259A is a controller that handles external interrupts from hardware devices.
((참/거짓): 8259A는 하드웨어 장치로부터의 외부 인터럽트를 처리하는 제어기이다.)

## 정답 및 해설

* **정답:** True (참)
* **해설:** 8259A는 프로그램 가능한 인터럽트 제어기(PIC, Programmable Interrupt Controller)로, x86 아키텍처에서 여러 하드웨어 장치로부터 발생하는 외부 인터럽트 요청(IRQ)을 관리하고 우선순위를 정하여 CPU에 전달하는 역할을 담당합니다.
---

# 23. (True/False): The acronym PCI stands for programmable component interface.
((참/거짓): 약어 PCI는 programmable component interface의 약자이다.)
---


## 정답 및 해설

* **정답:** False (거짓)
* **해설:** PCI는 'programmable component interface'가 아니라 **Peripheral Component Interconnect**의 약자입니다. 컴퓨터 메인보드에서 주변 장치들을 연결하기 위한 표준 로컬 버스 규격을 의미합니다.
---

# 24. (True/False): VRAM stands for virtual random access memory.
((참/거짓): VRAM은 virtual random access memory의 약자이다.)

## 정답 및 해설

* **정답:** False (거짓)
* **해설:** VRAM은 'virtual random access memory'가 아니라 **Video Random Access Memory**의 약자입니다. 그래픽 카드에서 이미지와 영상을 프레임 버퍼 형태로 저장하고 화면에 렌더링하기 위해 사용하는 특수한 형태의 메모리를 의미합니다.
---

# 25. At which level(s) can an assembly language program manipulate input/output?
(어셈블리어 프로그램은 어떤 레벨(들)에서 입출력(I/O)을 조작할 수 있는가?)

## 정답 및 해설

* **정답:** 어셈블리어는 **하드웨어 수준(Hardware level)** 또는 **저수준(Low-level)**에서 입출력 포트나 레지스터를 직접 조작할 수 있습니다.
* **해설:** 고급 언어(High-level language)들은 운영체제나 라이브러리를 거쳐 간접적으로 I/O를 제어하는 반면, 어셈블리어는 `IN`, `OUT`과 같은 전용 기계어 명령어와 포트 어드레싱을 사용하여 CPU 레지스터와 하드웨어 장치 간의 통신을 직접 제어할 수 있습니다.
---

# 26. Why do game programs often send their sound output directly to the sound card’s hardware ports?
(게임 프로그램은 왜 종종 사운드 카드의 하드웨어 포트로 직접 사운드 출력을 보내는가?)

## 정답 및 해설

* **정답:** **지연 시간(Latency)을 최소화하고 실시간 성능을 극대화**하기 위해서입니다.
* **해설:** 게임에서는 화면 그래픽과 사운드의 싱크(동기화)가 매우 중요합니다. 운영체제(OS)나 고수준 API의 레이어를 거치면 처리 지연(오버헤드)이 발생할 수 있으므로, 하드웨어 포트(I/O Port)에 직접 접근하여 사운드 데이터를 전송함으로써 지연 시간을 줄이고 빠른 반응 속도와 실시간 성능을 확보할 수 있습니다.
