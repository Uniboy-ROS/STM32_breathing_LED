# (board_china) STM32_breathing_LED

## 模式介紹

    如下圖所示
    板子內建LED接腳為"PA4"
    Programming Mode Boot 下0上1
    Operating Mode Boot 上下皆0
    
![image](https://github.com/Uniboy-ROS/STM32_breathing_LED/blob/master/(china)%20STM32_test/image/Jumper_contrast.jpg)

## Micro USB(serial)

    *請切換到Programming Mode Boot 下0上1
    因為此板有整合CH340G(USB轉串口)的芯片，所以這個接口只能用serial燒錄
    記得在工具/開發板 將Upload method 設為Serial
    
    照範例Blink跑，應該會如圖所示
    
![image](https://github.com/Uniboy-ROS/STM32_breathing_LED/blob/master/(china)%20STM32_test/image/Micro_USB.jpg)
    
    回傳值應該如下

![image](https://github.com/Uniboy-ROS/STM32_breathing_LED/blob/master/(china)%20STM32_test/image/serial_output.PNG)

## ST-LINK

    * Programming Mode Boot 下0上1 按下Reset 會clear 斷電等同
    * Operating Mode Boot 下0上0 按下Reset 會loop 所以斷電後在接上一樣會繼續執行

    記得在工具/開發板 將Upload method 設為STLink
    但因為讀不到序列埠，所以看不到回傳值始屬正常

    從ST-LINK 拉出SWDIO.GND.SWCLK.3.3V 4條線接到 板子對應的腳位上(A13-SWDIO、A14-SWCLK)
    便可以跑範例程式Blink了

![image](https://github.com/Uniboy-ROS/STM32_breathing_LED/blob/master/(china)%20STM32_test/image/ST-LINK.jpg)

