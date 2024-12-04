## **Exercise 4: Understanding Task Behavior with Priority Preemptive Scheduling**

**Overview**
Exercise 4 in the book focuses on understanding the behavior of tasks under a priority-preemptive scheduling policy using FreeRTOS. This exercise demonstrates how tasks interact when their execution order and CPU access are determined by assigned priorities.

**Objectives**
- Gain practical experience with priority-based preemptive scheduling.
- Observe how tasks of different priorities interact and execute in real-time.
- Learn how FreeRTOS handles task switching and resource allocation.

**Hardware and Software Requirements**
1. **Hardware:**
   - STM32F407G-DISC1 board (STM32F4 Discovery Kit)
2. **Software:**
   - STM32CubeMX for project configuration.
   - FreeRTOS middleware integrated within CubeMX.
   - IDE (Keil MDK, TrueSTUDIO, or equivalent) for development and debugging.

**Exercise Details**
1. **Problem Definition:**
   - Create multiple tasks with varying priorities.
   - Observe task behavior to understand how the FreeRTOS kernel manages CPU access.

2. **Implementation Steps:**
   - **Task Configuration:**
     - Configure tasks in CubeMX with distinct priorities.
     - Generate the initialization code using CubeMX.
   - **Code Implementation:**
     - Define the task functions in `main.c` or related files.
     - Use APIs like `vTaskDelay` and `vTaskPrioritySet` to create delays and adjust priorities during execution.
   - **Testing:**
     - Flash the program onto the STM32 board.
     - Observe LED toggling patterns to correlate with task priority and execution.

3. **Expected Behavior:**
   - Higher-priority tasks preempt lower-priority ones.
   - Lower-priority tasks resume only when higher-priority tasks are in a blocked state (e.g., due to delays).

**Code Summary**
In the provided program:
- **Task 1 (`FlashRedLedTask`)**:
  - Toggles the Red LED at 20Hz for 0.5 seconds, pauses for 1.5 seconds.
- **Task 2 (`FlashGreenLedTask`)**:
  - Toggles the Green LED at 20Hz for 4 seconds, pauses for 6 seconds.

Both tasks demonstrate preemptive scheduling, as the FreeRTOS kernel ensures that higher-priority tasks gain CPU access when required.

**Key Learning Points**
- The task with the highest priority runs first, preempting lower-priority tasks.
- Blocking operations (e.g., delays) allow lower-priority tasks to execute.
- Task synchronization and delay management are critical to avoid resource contention and ensure smooth operation.

**Extensions**
- Modify priorities dynamically during runtime to further explore preemption.
- Introduce additional tasks or use synchronization primitives like semaphores for resource sharing.

## Demonstration Video

Watch the demonstration video [here](https://drive.google.com/file/d/1UqSaFDJI6dtTvKUIfauODPFLVYQzVFBJ/view?usp=drive_link).


**References**
- **Book**: Jim Cooling - Real-time Operating Systems Book 2: The Practice.
- **STM32CubeMX Documentation**: For configuring FreeRTOS tasks.
- **FreeRTOS Documentation**: API guides and usage examples.

