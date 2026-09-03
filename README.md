# Project 2 — Traffic Light Robot

**Student:** Souad Mostafa Kamel  
**Module:** Microcontroller-Based Systems (Plain C)  
**Environment:** C99 Compliant (`gcc -std=c99 -Wall -Wextra`)

---

## 1. Project Overview
A modular finite-state-machine (FSM) implementation in standard C simulating an adaptive traffic light intersection. The system alternates between Green, Yellow, and Red phases, dynamically extends green-light duration during heavy traffic, tracks waiting and passed vehicles, supports blinking night mode, and maintains a rolling 20-tick history log.

---

## 2. Technical Rules & Requirements Verification
* **State Encapsulation:** The global `light` variable is strictly mutated through `nextState()`. No other function assigns or overrides the traffic state directly.
* **Bitwise Manipulation:** Night mode (`BIT_NIGHT`), busy queue flags (`BIT_BUSY`), and blinking states (`BIT_BLINK_ON`) are managed purely via bit macros (`SET_BIT`, `CLR_BIT`, `TOGGLE_BIT`, `READ_BIT`).
* **Dynamic Timing:** Green lasts 5 ticks under normal conditions and automatically increases to 7 ticks when `carsWaiting > 6` (`QUEUE_BUSY`), clearing back down when cars dissipate.
* **Input Safety & Size:** User input uses `readInt()` to prevent buffer hanging or loops. All functions are marked `static` and kept under 40 lines of code.

---

## 3. How to Build and Run
Compile with GCC:
```bash
gcc -std=c99 -Wall -Wextra -o app main.c
./app
