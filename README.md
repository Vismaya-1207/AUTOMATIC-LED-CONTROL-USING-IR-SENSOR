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
<img width="558" height="401" alt="image" src="https://github.com/user-attachments/assets/86d1f602-facd-47a8-af8f-c617dc53dd04" />



2. Click **File → New STM32 Project**.
<img width="604" height="378" alt="image" src="https://github.com/user-attachments/assets/41ecb6e4-311b-47df-a97c-2d9eee6661ee" />

<img width="574" height="474" alt="image" src="https://github.com/user-attachments/assets/2a432f17-ff48-4039-8f07-51e8c7fcdf17" />

  
3. Select the **target microcontroller** or board and click **Next**.

 <img width="468" height="409" alt="image" src="https://github.com/user-attachments/assets/532d2267-015c-440b-ac89-ce0ae4c9a93c" />



4. Name the project.


 <img width="485" height="698" alt="image" src="https://github.com/user-attachments/assets/52077c47-e675-4ed7-9601-80497d69bf06" />


5. The corresponding `.ioc` file will be generated automatically.

 <img width="573" height="588" alt="image" src="https://github.com/user-attachments/assets/8529003a-72d0-41ec-a5df-9e9489762af1" />


6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.

 <img width="489" height="505" alt="image" src="https://github.com/user-attachments/assets/3bf4f2ba-a35f-4de1-805f-ec070c243e14" />

<img width="544" height="611" alt="image" src="https://github.com/user-attachments/assets/d959830f-0036-4678-8c1d-ae646dbd274b" />


7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.

  <img width="479" height="448" alt="image" src="https://github.com/user-attachments/assets/a427861a-99dc-4572-9e4c-d39730eabc13" />

8. Edit the generated main program as required.

   <img width="556" height="477" alt="image" src="https://github.com/user-attachments/assets/b6e3d747-8695-4597-b321-131e4e19ace8" />

9. Click **Project → Build All**.

  <img width="484" height="468" alt="image" src="https://github.com/user-attachments/assets/826393a6-c71d-4bdf-8eeb-bb13ce15c18e" />


10. Link the **HEX file** using the post-build process.

    <img width="598" height="431" alt="image" src="https://github.com/user-attachments/assets/1e2517d7-f6b3-4ee1-aab4-69bebefb0367" />


11. Click **Debug** and connect the **STM Nucleo Board**.

<img width="608" height="508" alt="image" src="https://github.com/user-attachments/assets/e9e5cc32-482b-49bb-95f2-2ffc51a12a9f" />


<img width="683" height="588" alt="image" src="https://github.com/user-attachments/assets/fed752e5-3682-4cff-84c3-0ff949fea25e" />



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

<img width="436" height="799" alt="image" src="https://github.com/user-attachments/assets/31ac6180-d4fc-4d35-add0-b1f9191d0d35" />


CASE 2: LED OFF

<img width="609" height="624" alt="image" src="https://github.com/user-attachments/assets/8ca229a0-4232-4005-ac84-6ddc8d369e90" />



---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




