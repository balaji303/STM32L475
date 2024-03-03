## Create a working project with STM32CubeMX↑
The starting point is the project generated with STM32CubeMX, described in the Step3 tutorial : Introduction to the UART I/F on B-L475E-IOT01A.
Follow the steps in the tutorial.
Name the generated project as L4_IOT_Sensors.

## Copy BSP drivers to your project↑

The BSP (board support package) drivers are available in the STM32CubeL4 package. This provides APIs corresponding to the hardware components of a board.
The lastest version of the STM32CubeL4 package is downloaded by default in the STM32CubeMX repository:

C:\Users\user_name\STM32Cube\Repository\STM32Cube_FW_L4_Vx.xx.x.

In this example, the STM32CubeL4 version used is 1.11.0. Version can increase over time.
Follow these steps to copy the BSP drivers to your project:
In the generated project, create a folder L4_IOT_Sensors/Drivers/BSP.
Copy the STM32CubeL4/Drivers/BSP/B-L475E-IOT01 folder and paste it in the L4_IOT_Sensors/Drivers/BSP folder.
Copy the STM32CubeL4/Drivers/BSP/Components folder and paste it under L4_IOT_Sensors/Drivers/BSP/Components.
Only the HTS221 temperature sensor is used. For this reason, any other files and folders copied to the working directory can be removed. This step is optional:
    * Keep only the req files under  L4_IOT_Sensors\Drivers\BSP\B-L475E-IOT01:
    

    * Keep only the req files under L4_IOT_Sensors\Drivers\BSP\Components:
    

## Support BSP in STM32CubeIDE workspace↑
Added folders appear automatically in the STM32CubeIDE workspace:


## Update include paths

Update the paths to support new header files:
Select the relevant project from the Project Explorer perspective:
Project select.png
From Project menu or File menu, go to Properties > C/C++ Build > Settings > Tool Settings > MCU GCC Compiler > Include paths.
Click on Add icon.png to include the new paths.
Add ../Drivers/BSP/B-L475E-IOT01 and ../Drivers/BSP/Components/hts221 paths.


## Quick Link:
https://wiki.st.com/stm32mcu/wiki/STM32StepByStep:Step4_Sensors_usage




       ,.,
      MMMM_    ,..,
        "_ "__"MMMMM          ,...,,
 ,..., __." --"    ,.,     _-"MMMMMMM
MMMMMM"___ "_._   MMM"_."" _ """"""
 """""    "" , \_.   "_. ."
        ,., _"__ \__./ ."
       MMMMM_"  "_    ./
        ''''      (    )
 ._______________.-'____"---._.
  \       @Balaji303         /
   \________________________/
   (_)                    (_)

uint8_t msg0[] = 

HAL_UART_Transmit(&huart1,( uint8_t *)str_tmp,sizeof(str_tmp),1000);


                                          &&&&&&&&&
                                        &&&
                                       &&
                                      &  _____ ___________
                                     II__|[] | |   I I   |
       @Balaji303                   |        |_|_  I I  _|
                                   < OO----OOO   OO---OO
**********************************************************


uint8_t train1[] = "                                          &&&&&&&&&\n\r                                        &&&\n\r                                       &&\n\r                                      &  _____ ___________\n\r                                     II__|[] | |   I I   |\n\r       @Balaji303                   |        |_|_  I I  _|\n\r                                   < OO----OOO   OO---OO\n\r**********************************************************\n\r";




    // 0x70 = 0b01110000
    // OM = 11 (ultra-high-performance mode for X and Y); DO = 100 (10 Hz ODR)
    writeReg(CTRL_REG1, 0x70);

    // 0x00 = 0b00000000
    // FS = 00 (+/- 4 gauss full scale)
    writeReg(CTRL_REG2, 0x00);

    // 0x00 = 0b00000000
    // MD = 00 (continuous-conversion mode)
    writeReg(CTRL_REG3, 0x00);

    // 0x0C = 0b00001100
    // OMZ = 11 (ultra-high-performance mode for Z)
    writeReg(CTRL_REG4, 0x0C);

    // 0x40 = 0b01000000
    // BDU = 1 (block data update)
    writeReg(CTRL_REG5, 0x40);