### README for Exercise 5: Demonstrating Access Contention Problems

---

#### **Overview**
This program is part of Exercise 5 in the book, focusing on demonstrating **access contention problems** in a multitasking system. It shows how two tasks attempting to access a shared resource without proper synchronization can lead to conflicts. The program utilizes FreeRTOS and runs on an STM32 board.

---

#### **Objectives**
- Demonstrate what happens when tasks access shared resources concurrently without protection.
- Highlight the importance of resource synchronization in multitasking environments.
- Introduce the concept of contention detection through visual indicators (e.g., an LED).

---

#### **Program Behavior**
1. **Tasks Overview:**
   - **Task 1 (FlashRedLedTask):**
     - Toggles the Red LED rapidly (every 100 ms).
     - Attempts to access a shared resource using the `AccessSharedResource()` function.
   - **Task 2 (FlashGreenLedTask):**
     - Toggles the Green LED at a slower rate (every 500 ms).
     - Also attempts to access the shared resource.

2. **Shared Resource:**
   - A variable (`StartFlag`) is used as a pseudo-lock to simulate a critical section.
   - When contention occurs (i.e., both tasks try to access the resource simultaneously), the Blue LED (`LED_Indicator`) is turned on as a visual indicator of the conflict.

3. **Expected Outcome:**
   - The Blue LED will light up whenever contention occurs, showing that the shared resource was accessed simultaneously by both tasks.

---

#### **How It Works**
1. The shared resource (`StartFlag`) is checked and modified in the `AccessSharedResource()` function.
2. If the resource is already in use, the Blue LED is turned on to indicate contention.
3. Both tasks call this function during their execution, simulating a real-world scenario where multiple processes need access to the same resource.

---

#### **Hardware and Software Requirements**
1. **Hardware:**
   - STM32F407G-DISC1 board (STM32F4 Discovery Kit).
   - LEDs connected to specific GPIO pins.
2. **Software:**
   - STM32CubeMX for project configuration.
   - FreeRTOS middleware integrated within CubeMX.
   - IDE (Keil MDK, TrueSTUDIO, or equivalent) for development and debugging.

---

#### **Implementation Details**
1. **Tasks and Priority:**
   - **FlashRedLedTask** has a higher priority (`osPriorityAboveNormal`).
   - **FlashGreenLedTask** has a normal priority (`osPriorityNormal`).
2. **Shared Resource Access:**
   - Both tasks call `AccessSharedResource()` where contention may occur.

3. **Visual Indicators:**
   - **Red LED** and **Green LED** show task execution.
   - **Blue LED** indicates contention.

4. **Key Code Sections:**
   - `AccessSharedResource()` manages access to the shared variable and contention detection.

---

#### **Key Learning Points**
- **Access Contention:** 
  - When two tasks access a shared resource without synchronization, conflicts can arise, leading to inconsistent states or unexpected behavior.
- **Visual Feedback:** 
  - The Blue LED is used to provide immediate feedback on contention events.
- **Task Priorities:**
  - Higher-priority tasks can preempt lower-priority ones, increasing the likelihood of contention if proper mechanisms are not in place.

---
## Demonstration Video

Watch the demonstration video [here](https://drive.google.com/file/d/1V8gGLc9AtQLAo1yrRkqYcxEiCe2RpiYf/view?usp=sharing).


---

#### **References**
- **Book**: Jim Cooling - Real-time Operating Systems Book 2: The Practice.
- **Chapter**: Exercise 5 - Demonstrating Access Contention Problems.
- **FreeRTOS Documentation**: For synchronization primitives like semaphores and mutexes.

---

