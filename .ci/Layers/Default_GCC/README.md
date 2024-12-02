# Board: STMicroelectronics [STM32G474E-EVAL1](https://www.st.com/en/evaluation-tools/stm32g474e-eval1.html)

## Default GCC Board Layer

Device: **STM32G474QETx**

System Core Clock: **150 MHz**

This setup is configured using **STM32CubeMX**, an interactive tool provided by STMicroelectronics for device configuration.
Refer to ["Configure STM32 Devices with CubeMX"](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/CubeMX.md) for additional information.

### System Configuration

| System resource       | Setting
|:----------------------|:--------------------------------------
| Heap                  | 64 kB (configured in the STM32CubeMX)
| Stack (MSP)           |  1 kB (configured in the STM32CubeMX)

### STDIO mapping

**STDIO** is routed to Virtual COM port on the ST-LINK (using **USART1** peripheral)

### CMSIS-Driver mapping

| CMSIS-Driver          | Peripheral            | Board connector/component                     | Connection
|:----------------------|:----------------------|:----------------------------------------------|:------------------------------
| Driver_USART1         | USART1                | ST-LINK connector (CN21)                      | STDIN, STDOUT, STDERR
| Driver_USART3         | USART3                | Motor-control connector pins 5, 9 (CN4)       | CMSIS_USART
| Driver_USBD0          | USB_FS                | USB Type-C connector (CN22)                   | CMSIS_USB_Device
| CMSIS-Driver VIO      | GPIO                  | LEDs (LD3, LD1) and TAMPER button (B2)        | CMSIS_VIO

### CMSIS-Driver Virtual I/O mapping

| CMSIS-Driver VIO      | Board component
|:----------------------|:--------------------------------------
| vioBUTTON0            | TAMPER button (B2)
| vioLED0               | LED red       (LD3)
| vioLED1               | LED green     (LD1)
