# STM32_breathing_LED

##  硬體部分

        1.STM32F103
        2.FTDI
        3.Mini USB

## 電路連接

### FTDI TO MCU

        FTDI_VCC --> MCU_5V
        FTDI_GND --> MCU_G
        FTDI_TXD --> MCU_A10(USART1_RX)
        FTDI_RXD --> MCU_A9(USART1_TX)

       * 接腳部份有問題 請參考tool裡面stm32f103的datasheet

### MCU TO LED

        MCU_A8(TIM1_CH1) --> 220Ω --> LED(長+) --> LED(短-) --> GND
        MCU_B6(TIM4_CH1) --> 220Ω --> LED(長+) --> LED(短-) --> GND

        * 最終示意圖(圖為小編的亂中有序天橋建築工法，如有問題不負責任):
![image](https://github.com/Uniboy-ROS/STM32_breathing_LED/blob/master/picture/circuit.jpg)

## 環境建置

    1.請先下載 Arduino IDE ，並安裝好
    2.到GitHub上下載[支援包](https://github.com/rogerclarkmelbourne)
    3.下載完後請解壓縮至路徑Arduino底下，範例: C:\Arduino\hardware 底下
![image](https://github.com/Uniboy-ROS/STM32_breathing_LED/blob/master/picture/01.PNG)

    4.在 開發板/開發板管理員 上面輸入STM32F1 將開發包安裝
![image](https://github.com/Uniboy-ROS/STM32_breathing_LED/blob/master/picture/02.PNG)

    5.接著在 檔案/偏好設定 額外的開發板網址輸入: http://dan.drown.org/stm32duino/package_STM32duino_index.json
![image](https://github.com/Uniboy-ROS/STM32_breathing_LED/blob/master/picture/03.PNG)

    6.開啟Arduino IDE 在 工具/開發板 底下 便可以選擇 Generic STM32F103C series
    7.要用FTDI傳送記得 將Upload method 設為Serial
    8.(port記得連COMX，X因設備不同而異)
![image](https://github.com/Uniboy-ROS/STM32_breathing_LED/blob/master/picture/serial.png)
## 執行程式

    執行前記得將jumper放在boot 0 進入Programming Mode
![image](https://github.com/Uniboy-ROS/STM32_breathing_LED/blob/master/picture/mode.jpg)

    執行 程式 STM32_breathing_LED.ino 就可達到我們要的呼吸燈了
    也可使用 STM32_Serial.py 和 STM32_Serial.ino 來進行通訊(因設備不同COM_PORT可能有差異，小編內設為COM8)


# 使用Micro USB連STM32F103

## 環境建置

    * 記得要在Programming Mode，FTDI端也要連線
    將tool裡面的en.flasher-stm32.zip解壓縮，並照預設路徑執行安裝檔案
    C:\Program Files (x86)\STMicroelectronics\Software\Flash Loader Demo 可找到執行檔 STMFlashLoader Demo.exe
    1.選擇com_port 
![image](https://github.com/Uniboy-ROS/STM32_breathing_LED/blob/master/picture/com_port.PNG)

    2.接下來連點next 直到這個畫面，路徑選為tool裡面的bin檔
![image](https://github.com/Uniboy-ROS/STM32_breathing_LED/blob/master/picture/bin.png)

    3.最後next，讓他安裝完便可來到最後一步
    4.在C:\Program Files (x86)\Arduino\hardware\Arduino_STM32-master\drivers\win底下執行
        install_drivers.bat和install_STM_COM_drivers.bat

## Arduino IDE

### 兄弟恭喜來到最後了

    * 在上述步驟都完成後，我們便可將Mini USB拔下來換插MicroUSB了 
    * 切記並切換到Operating Mode

    確認是否連接上
![image](https://github.com/Uniboy-ROS/STM32_breathing_LED/blob/master/picture/device.png)

    最後在Arduino IDE上TOOLS裡面將 Upload method 設為 bootloader (port記得連COMX，X因設備不同而異)
    這樣就能透過Micro USB燒錄程式到STM32F103了!! Congratulations!!