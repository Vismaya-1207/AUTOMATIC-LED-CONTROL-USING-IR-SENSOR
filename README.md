# AUTOMATIC-LED-CONTROL-USING-IR-SENSOR
##  AIM
To design and implement a system using the **STM32 microcontroller** where an LED automatically turns ON or OFF based on the input from an **IR sensor**.

---

##  Components Required
- STM32 Nucleo or Discovery Board (e.g., **Nucleo-G071RB**)
- IR Sensor Module
- LED (5mm Green or any color)
- Jumper wires
- Breadboard

---

##  Theory
An **IR sensor** detects the presence of an object by emitting and receiving infrared light.

### IR Sensor Behavior
- When an **object is detected**, the IR sensor output goes **LOW (0V)**.
- When **no object is detected**, the output stays **HIGH (3.3V)**.

### Microcontroller Response
- If **IR output = LOW** → **LED ON**
- If **IR output = HIGH** → **LED OFF**
### **Procedure**

1. Open **STM32CubeIDE**.


   <img width="613" height="441" alt="image" src="https://github.com/user-attachments/assets/ae29e25a-206e-482a-b630-8debb4a857fa" />


2. Click **File → New STM32 Project**.
<img width="614" height="384" alt="image" src="https://github.com/user-attachments/assets/d474cb39-cdc2-4430-9787-dc4151d2de96" /> 
<img width="733" height="458" alt="image" src="https://github.com/user-attachments/assets/d399bace-6515-4b2d-b0b6-01e7c3c6be07" />

  
3. Select the **target microcontroller** or board and click **Next**.
  <img width="775" height="484" alt="image" src="https://github.com/user-attachments/assets/e4eb2a0a-30ae-4da4-9090-bf74c7a56b98" />



4. Name the project.

  <img width="645" height="681" alt="Screenshot 2025-11-03 205253" src="https://github.com/user-attachments/assets/86b7c6d7-e880-413d-9755-7808123678f1" />


5. The corresponding `.ioc` file will be generated automatically.
  <img width="1920" height="1200" alt="Screenshot (548)" src="https://github.com/user-attachments/assets/ecf81c5b-8afe-4aba-8986-6451cbfc1d60" />


6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
  <img width="1920" height="1200" alt="Screenshot (549)" src="https://github.com/user-attachments/assets/fdf4eb6f-7233-4220-9029-8e787ec96ffa" />
<img width="1920" height="1200" alt="Screenshot (550)" src="https://github.com/user-attachments/assets/7aa60f1d-3248-4554-9c71-04165ca41aa4" />
7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
  <img width="1920" height="1200" alt="Screenshot (467)" src="https://github.com/user-attachments/assets/810dc411-00f1-4788-949f-31f7f44641cc" />

8. Edit the generated main program as required.
   <img width="1920" height="1200" alt="Screenshot (541)" src="https://github.com/user-attachments/assets/604c6b67-21f0-4946-8633-a41a1ee12113" />

9. Click **Project → Build All**.
   <img width="1920" height="1200" alt="Screenshot (542)" src="https://github.com/user-attachments/assets/0dc79653-2584-4dee-b076-5cf782f5a31e" />
 

10. Link the **HEX file** using the post-build process.
    <img width="1920" height="1200" alt="Screenshot (544)" src="https://github.com/user-attachments/assets/6816c690-6e69-40be-bb4b-f1964efbed2d" />

11. Click **Debug** and connect the **STM Nucleo Board**.
<img width="1920" height="1200" alt="Screenshot (546)" src="https://github.com/user-attachments/assets/5019c219-49b7-40c9-a0fb-0f71c30da414" />
<img width="1920" height="1200" alt="Screenshot (547)" src="https://github.com/user-attachments/assets/0cffdeb3-9ca6-46f1-97a7-7912a4cf1213" />


12. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        GPIO_PinState ir = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_10); // IR OUT at PA10 (D2)

	      if (ir == GPIO_PIN_RESET)  // IR sensor HIGH = object detected
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET); // Turn ON LED
	      }
	      else
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET); // Turn OFF LED
	      }

	      HAL_Delay(100);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 


CASE 2: LED OFF

---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




