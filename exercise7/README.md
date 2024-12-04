### README for Exercise 7: Understanding Task Preemption and Resource Synchronization

---

#### **Overview**
This program builds on Exercise 7 from the book, focusing on **task preemption** and **resource synchronization** in FreeRTOS. By introducing a new task and exploring priorities, it demonstrates how tasks interact in a multitasking environment while accessing shared resources.

---

#### **Objectives**
- Observe how task priorities affect execution order in a multitasking system.
- Understand how critical sections can protect shared resources in the presence of preemptive scheduling.
- Learn about the implications of introducing additional tasks with varying priorities.

---

#### **Program Behavior**
1. **Tasks Overview:**
   - **Task 1 (`FlashGreenLedTask`):**
     - Toggles the Green LED at a regular interval (200 ms).
     - Attempts to access a shared resource (`StartFlag`) within a critical section.
   - **Task 2 (`FlashRedLedTask`):**
     - Toggles the Red LED with a longer delay (550 ms).
     - Also accesses the shared resource within the critical section.
   - **Task 3 (`FlashOrangeLedTask`):**
     - Toggles the Orange LED at a rapid pace (50 ms), demonstrating high-priority task preemption.

2. **Shared Resource:**
   - A volatile variable `StartFlag` simulates a resource being accessed by multiple tasks.
   - Critical sections (`portENTER_CRITICAL` and `portEXIT_CRITICAL`) ensure that only one task can access the shared resource at a time.

3. **Visual Indicators:**
   - **Green LED** and **Red LED** indicate the execution of their respective tasks.
   - **Orange LED** indicates high-priority task preemption.
   - **Blue LED** (`Led_Indicator`) lights up if contention occurs (should not occur due to critical sections).

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
1. **Task Priorities:**
   - **FlashOrangeLedTask** has the highest priority (`osPriorityAboveNormal`), ensuring it preempts other tasks whenever ready to run.
   - **FlashGreenLedTask** and **FlashRedLedTask** have normal priority, allowing them to execute in turn unless preempted by a higher-priority task.

2. **Critical Sections:**
   - Protect access to the shared resource `StartFlag` to ensure consistent behavior.

3. **Key Functions:**
   - `AccessSharedResource()`: Ensures resource synchronization using critical sections and visualizes contention if any.

---

#### **Key Learning Points**
- **Preemptive Scheduling:**
  - Higher-priority tasks (e.g., `FlashOrangeLedTask`) preempt lower-priority ones, demonstrating the scheduler's behavior in FreeRTOS.
- **Critical Sections:**
  - Critical sections effectively prevent resource contention, even with multiple tasks accessing the same resource.
- **Task Synchronization:**
  - Proper synchronization is essential for system stability in multitasking environments.

---
## Demonstration Video

Watch the demonstration video [here](https://drive.google.com/file/d/1V_rME-p-gQH_Vk_2nnmqTX61808MQc9I/view?usp=sharing).


---

#### **References**
- **Book**: Jim Cooling - Real-time Operating Systems Book 2: The Practice.
- **Chapter**: Exercise 7 - Understanding Task Preemption and Resource Synchronization.
- **FreeRTOS Documentation**: For APIs related to task synchronization and scheduling.
