# STM32G474E-EVAL1_BSP

The **STMicroelectronics STM32G474E-EVAL1 Board Support Pack (BSP)**:

- Contains examples and board layers in *csolution format* for usage with the [CMSIS-Toolbox](https://open-cmsis-pack.github.io/cmsis-toolbox/) and the  [VS Code CMSIS Solution](https://marketplace.visualstudio.com/items?itemName=Arm.cmsis-csolution) extension.
- Requires the [Device Family Pack (DFP) for the STM32G4 series](https://www.keil.arm.com/packs/stm32g4xx_dfp-keil).
- Is configured with [STM32CubeMX](https://www.st.com/en/development-tools/stm32cubemx.html) for the Arm Compiler 6 (MDK). [Using GCC Compiler](#using-gcc-compiler) explains how to configured it for a different compiler.

## Content in *csolution format*

- [Examples/Blinky](https://github.com/Open-CMSIS-Pack/STM32G474E-EVAL1_BSP/tree/main/Examples/Blinky) shows the basic usage of this board.

- [Board Layer](https://github.com/Open-CMSIS-Pack/STM32G474E-EVAL1_BSP/tree/main/Layers/Default) for device-agnostic [Reference Applications](https://open-cmsis-pack.github.io/cmsis-toolbox/ReferenceApplications/) that implements these API interfaces:

| Provided API Interface        | Description
|:------------------------------|:------------------------------------------------------------------------------
| CMSIS_USART                   | CMSIS-Driver USART connected to Motor-control connector (pins 5, 9) (CN4)
| CMSIS_USB_Device              | CMSIS-Driver USB Device connected to USB_FS connector (CN22)
| CMSIS_VIO                     | CMSIS-Driver VIO connected to LEDs (LD3, LD1) and TAMPER button (B2)
| STDIN, STDOUT, STDERR         | Standard I/O connected to Virtual COM port on ST-LINK connector (CN21)

## Using GCC Compiler

By default the [Board Layers](https://github.com/Open-CMSIS-Pack/STM32G474E-EVAL1_BSP/tree/main/Layers) are configured for the Arm Compiler 6 (AC6). Using STM32CubeMX it can be reconfigured for a different compiler. To configure it for the GCC compiler execute these steps:

- In the `<solution_name>.csolution.yml` project file select `compiler: GCC`.
- Launch the STM32CubeMX generator with this CMSIS-Toolbox command:
  `csolution <solution_name>.csolution.yml run -g CubeMX -c <context>`
- In STM32CubeMX:
  - Open from the menu `Project Manager - Project - Toolchain/IDE`:
  - Select `STM32CubeIDE` and disable `Generate Under Root`.
  - Click `GENERATE CODE` to recreate the CubeMX generated files for the GCC compiler.

- In the `Board.clayer.yml` file, update `linker:` node configuration to reference appropriate GCC linker script.
  The GCC linker script is typically generated in the `STM32CubeMX/STM32CubeIDE` folder. Customize the GCC linker script file to your project's requirements.
- Rebuild the project using the CMSIS-Toolbox command `cbuild <solution_name>.csolution.yml`.
