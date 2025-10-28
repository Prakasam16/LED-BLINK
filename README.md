# LED-BLINK
# 💡 Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### 🎯 **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### ⚙️ **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board  

---

### 🧠 **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
### 🧩 **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
### 🔍 **LPC2148 Microcontroller**
The **LPC2148**, developed by NXP Semiconductors (Philips), is a 16/32-bit ARM7-based microcontroller featuring a wide range of peripherals.
#### **Key Features**
- 16/32-bit ARM7TDMI-S core in LQFP64 package  
- On-chip **Flash memory**: 32 KB – 512 KB  
- On-chip **SRAM**: 8 KB – 40 KB  
- **ISP/IAP** via on-chip bootloader  
- **Embedded ICE-RT** and **Real Monitor** for real-time debugging  
- **USB 2.0** full-speed device controller with 2 KB endpoint RAM  
- **10-bit ADC** (6 or 14 channels, 2.44 μs conversion time)  
- **10-bit DAC** for analog output  
- **Timers:** Two 32-bit timers, watchdog, and PWM unit  
- **RTC** with 32 kHz clock input  
- **UARTs (2x), I²C (2x)** up to 400 kbit/s  
- **5V-tolerant GPIOs**, 21 external interrupt pins  
- **Max CPU Clock:** 60 MHz using on-chip PLL (lock time 100 µs)  
- **Crystal Frequency:** 1 MHz – 25 MHz  
- **Power modes:** Idle and Power-down with peripheral clock scaling  

---

### 🧭 **Procedure**

1. Open **STM32CubeIDE**.
  <img width="1900" height="1067" alt="Screenshot 2025-10-28 192120" src="https://github.com/user-attachments/assets/8227ae9d-2e89-4cb4-98b0-d7276ed5bc78" />


2. Click **File → New STM32 Project**.
   <img width="1907" height="1068" alt="Screenshot 2025-10-28 221537" src="https://github.com/user-attachments/assets/b9043698-cc27-4497-8313-2f3aac765cde" />

<img width="1907" height="1068" alt="Screenshot 2025-10-28 221612" src="https://github.com/user-attachments/assets/63edddbe-50a3-45e7-b55c-d7325f87e8c7" />


3. Select the **target microcontroller** or board and click **Next**.
  <img width="1920" height="1080" alt="Screenshot 2025-10-28 223105" src="https://github.com/user-attachments/assets/a935e901-62d0-4f27-9636-efb908f86c9a" />


4. Name the project.
  <img width="1907" height="1068" alt="Screenshot 2025-10-28 231713" src="https://github.com/user-attachments/assets/7ed44115-3438-454c-8f42-ad998622c4ca" />


5. The corresponding `.ioc` file will be generated automatically.
 <img width="1907" height="1065" alt="Screenshot 2025-10-28 223239" src="https://github.com/user-attachments/assets/bec5685a-e104-4cc9-abcd-fc605d627e6f" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
  <img width="1907" height="1066" alt="Screenshot 2025-10-28 223304" src="https://github.com/user-attachments/assets/f893eca5-4840-43e8-aae0-6ab2a22fe5f4" />
<img width="1907" height="1065" alt="Screenshot 2025-10-28 223239" src="https://github.com/user-attachments/assets/09744ae5-f90d-41ac-b082-58819a05f20e" />


7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
  ![Screenshot 2025-10-28 223239](https://github.com/user-attachments/assets/e19f7ec0-204f-4928-9fbd-580aa6c3b9bf)

 
8. Edit the generated main program as required.
   ![WhatsApp Image 2025-10-28 at 23 08 31_6f0f8092](https://github.com/user-attachments/assets/5b88a777-e229-46fd-baa5-79a9ca832e22)

![WhatsApp Image 2025-10-28 at 23 09 14_e5c774c8](https://github.com/user-attachments/assets/50016e15-3e86-4788-bcbd-2b2e2636136a)


9. Click **Project → Build All**.
  ![WhatsApp Image 2025-10-28 at 23 09 14_e5c774c8](https://github.com/user-attachments/assets/50016e15-3e86-4788-bcbd-2b2e2636136a)

10. Link the **HEX file** using the post-build process.
    ![WhatsApp Image 2025-10-28 at 23 09 37_8ede9574](https://github.com/user-attachments/assets/7b4fa05a-7faa-444b-bbad-b4cf9ba81bf7)

11. Click **Debug** and connect the **STM Nucleo Board**.
     ![WhatsApp Image 2025-10-28 at 23 10 03_f75f39fb](https://github.com/user-attachments/assets/f81c5435-12c6-4a5d-a015-699bd617f508)

13. Click **Run** to execute the program.
    
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
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        HAL_Delay(1000);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 

CASE 2: LED OFF

---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
