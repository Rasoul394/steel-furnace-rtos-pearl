# Real-Time Steel Furnace Control System (PEARL)

Hi there! Welcome to my repository. 
I created this project to demonstrate the core concepts of **Real-Time Operating Systems (RTOS)** and industrial automation using the **PEARL** programming language. 

The system simulates the control logic for a steel blast furnace, where safety, timing, and hardware constraints are critical.

##  How It Works
The program continuously monitors the temperature of the furnace. If the temperature exceeds the safe limit (1200°C), it automatically opens a cooling valve. If it reaches a critical level (1400°C) or if a worker presses the hardware emergency button, the system triggers an emergency protocol to sound the alarm and cool the furnace immediately.

##  Key RTOS Concepts Demonstrated

Here are the main real-time engineering principles I applied in this code:

* **Hardware Independence (Portability):** By using PEARL's architecture, the code is strictly divided into a `SYSTEM` part (hardware connections) and a `PROBLEM` part (logic). If a sensor is moved to a different port in the factory, only one line in the `SYSTEM` part needs to be updated without touching the core algorithm.
* **Priority Handling & Preemption:** The `Emergency_Task` is assigned the highest priority (Priority 1), while the `Monitor_Task` has a lower priority (Priority 5). This ensures that if a disaster happens, the OS will immediately preempt (pause) normal operations to handle the emergency.
* **Time-Driven vs. Event-Driven Scheduling:** * *Time-Driven:* The temperature is checked periodically (`ALL 2 SEC`).
  * *Event-Driven:* The emergency button is linked to a hardware interrupt (`WHEN EMERGENCY_BTN`), ensuring zero wasted CPU cycles on busy-waiting.
* **Analog vs. Digital I/O Handling:** The code differentiates between continuous analog signals (reading temperature) and binary digital outputs (valves and alarms).

##  Why PEARL?
PEARL (Process and Experiment Automation Realtime Language) is highly standardized in Germany (DIN 66253) for industrial applications. I chose it for this snippet to show my understanding of low-level, safety-critical system design.

---
*Feel free to reach out if you have any questions about this code or my background in real-time systems!*
