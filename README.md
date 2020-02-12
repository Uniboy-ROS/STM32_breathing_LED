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

### MCU TO LED

        MCU_A8(TIM1_CH1) --> 220Ω --> LED(長+) --> LED(短-) --> GND
        MCU_B6(TIM4_CH1) --> 220Ω --> LED(長+) --> LED(短-) --> GND

        示意圖(圖為小編的亂中有序天橋建築工法，如有問題不負責任):
        ![image](https://github.com/Uniboy-ROS/STM32_breathing_LED/blob/master/picture/circuit.jpg)

## 環境建置

    1.請先下載 Arduino IDE ，並安裝好
    2.到GitHub上下載[支援包](https://github.com/rogerclarkmelbourne)
    3.下載完後請解壓縮至路徑Arduino底下，範例: C:\Arduino\hardware 底下
    4.在 開發板/開發板管理員 上面輸入STM32F1 將開發包安裝
    5.接著在 檔案/偏好設定 額外的開發板網址輸入: http://dan.drown.org/stm32duino/package_STM32duino_index.json
    6.開啟Arduino IDE 在 工具/開發板 底下 便可以選擇 Generic STM32F103C series
    7.要用FTDI傳送記得 將Upload method 設為Serial

## 執行程式

    執行 程式 STM32_breathing_LED.ino 就可達到我們要的呼吸燈了
    也可使用 STM32_Serial.py 和 STM32_Serial.ino 來進行通訊(因設備不同COM_PORT可能有差異，小編內設為COM8)