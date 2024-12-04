### README for Exercise 6: Using Critical Sections for Resource Protection

---

#### **Overview**
This program is based on Exercise 6 from the book, focusing on using **critical sections** to manage access to shared resources in a multitasking environment. It demonstrates how critical sections can prevent contention issues and ensure data integrity when multiple tasks access the same resource.

---

#### **Objectives**
- Learn how to use critical sections (`portENTER_CRITICAL()` and `portEXIT_CRITICAL()`) to protect shared resources.
- Understand how critical sections temporarily disable task switching to avoid resource contention.
- Explore task synchronization in FreeRTOS to manage shared resource access effectively.

---

#### **Program Behavior**
1. **Tasks Overview:**
   - **Task 1 (`FlashRedLedTask`):**
     - Toggles the Red LED every 500 ms.
     - Accesses the shared resource (`StartFlag`) within a critical section.
   - **Task 2 (`FlashGreenLedTask`):**
     - Toggles the Green LED every 2.5 seconds.
     - Also accesses the shared resource using the same critical section.

2. **Shared Resource:**
   - A volatile variable `StartFlag` is used to simulate a resource being accessed.
   - The `AccessSharedResource()` function protects access to this variable using critical sections, ensuring no other task can interrupt while it is being accessed.

3. **Visual Indicators:**
   - **Red LED** and **Green LED** indicate task execution.
   - **Blue LED** (via `LED_Indicator`) lights up if contention is detected (should not occur with critical sections enabled).

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
1. **Critical Sections:**
   - `portENTER_CRITICAL()` suspends the scheduler, disabling context switching to ensure the current task completes its critical section uninterrupted.
   - `portEXIT_CRITICAL()` resumes the scheduler, allowing other tasks to execute.

2. **Tasks and Priority:**
   - **FlashRedLedTask** has a higher priority (`osPriorityAboveNormal`) and toggles the Red LED.
   - **FlashGreenLedTask** has a normal priority (`osPriorityNormal`) and toggles the Green LED.

3. **Key Functionality:**
   - The `AccessSharedResource()` function wraps access to the `StartFlag` variable with critical sections to ensure data consistency and avoid contention.

---

#### **Key Learning Points**
- **Critical Sections Prevent Contention:**
  - Critical sections ensure only one task accesses the shared resource at a time by suspending task switching.
- **Trade-offs of Critical Sections:**
  - While effective, critical sections block all other tasks, potentially impacting real-time performance if overused or used with long delays.

---

## Demonstration Video

Watch the demonstration video [here](https://drive.google.com/file/d/1VJUkvpv0U2Oy3iaWjEJf58CmnxDwJzz5/view?usp=sharing).


---

#### **References**
- **Book**: Jim Cooling - Real-time Operating Systems Book 2: The Practice.
- **Chapter**: Exercise 6 - Using Critical Sections for Resource Protection.
- **FreeRTOS Documentation**: For APIs related to task synchronization.

