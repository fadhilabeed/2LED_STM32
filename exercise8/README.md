### README for Exercise 8: Using Semaphores for Resource Synchronization

---

#### **Overview**
This program is designed based on Exercise 8, demonstrating the use of **semaphores** to synchronize access to shared resources in a multitasking environment. Semaphores prevent contention and ensure that only one task accesses the shared resource at a time, even in a preemptive scheduling system.

---

#### **Objectives**
- Learn how to use semaphores for resource synchronization in FreeRTOS.
- Understand how semaphores manage access to shared resources among multiple tasks.
- Observe the behavior of tasks with varying priorities when accessing shared resources.

---

#### **Program Behavior**
1. **Tasks Overview:**
   - **Task 1 (`FlashGreenLedTask`):**
     - Toggles the Green LED every 200 ms.
     - Uses a semaphore to access the shared resource (`StartFlag`).
   - **Task 2 (`FlashRedLedTask`):**
     - Toggles the Red LED every 550 ms.
     - Also uses the semaphore for resource access.
   - **Task 3 (`FlashOrangeLedTask`):**
     - Toggles the Orange LED every 50 ms, demonstrating high-priority task preemption.

2. **Shared Resource:**
   - The semaphore ensures mutual exclusion when accessing the shared resource (`StartFlag`).
   - Tasks attempting to acquire the semaphore wait until it is released if another task is using the resource.

3. **Visual Indicators:**
   - **Green LED** and **Red LED** indicate task execution and successful access to the resource.
   - **Blue LED (`LED_Indicator`)** lights up if a contention scenario is detected (optional for demonstration purposes).

---

#### **Hardware and Software Requirements**
1. **Hardware:**
   - STM32F407G-DISC1 board (STM32F4 Discovery Kit).
   - LEDs connected to GPIO pins.
2. **Software:**
   - STM32CubeMX for project configuration.
   - FreeRTOS middleware integrated within CubeMX.
   - IDE (Keil MDK, TrueSTUDIO, or equivalent) for development and debugging.

---

#### **Implementation Details**
1. **Semaphores:**
   - A binary semaphore (`CriticalResourceSemaphoreHandle`) is created and used to control access to the shared resource.
   - The semaphore is acquired before accessing the resource and released afterward.

2. **Task Synchronization:**
   - Tasks attempt to acquire the semaphore using `osSemaphoreAcquire()`.
   - If the semaphore is unavailable, tasks either wait or handle the situation (e.g., by lighting up the Blue LED).

3. **Task Priorities:**
   - **FlashOrangeLedTask** has the highest priority (`osPriorityAboveNormal`) and demonstrates preemption of other tasks.
   - **FlashGreenLedTask** and **FlashRedLedTask** share equal priorities and access the resource in turn.

4. **Key Functions:**
   - `AccessSharedResource()` manages resource access using the semaphore and includes delays to simulate task work.

---

#### **Key Learning Points**
- **Semaphore Basics:**
  - Semaphores provide a simple and effective mechanism for managing shared resources in a multitasking environment.
- **Task Synchronization:**
  - Semaphores prevent race conditions and ensure consistent resource states.
- **Task Preemption:**
  - High-priority tasks can preempt lower-priority ones, but synchronization mechanisms like semaphores ensure orderly access to resources.

---
## Demonstration Video

Watch the demonstration video [here](https://drive.google.com/file/d/1Vb5CwKpQc-JW7qlxPKhG2Z00pV77W7dY/view?usp=sharing).

---

#### **References**
- **Book**: Jim Cooling - Real-time Operating Systems Book 2: The Practice.
- **Chapter**: Exercise 8 - Using Semaphores for Resource Synchronization.
- **FreeRTOS Documentation**: For APIs related to semaphores and task synchronization.

