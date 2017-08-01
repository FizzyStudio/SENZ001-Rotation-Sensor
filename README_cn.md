# SENZ001 模拟多圈旋转角度传感器

###### Translation

[For English, please click here.](https://github.com/FizzyStudio/SENZ001-Rotation-Sensor/blob/master/README.md)
[For Chinese, please click here.](https://github.com/FizzyStudio/SENZ001-Rotation-Sensor/blob/master/README_cn.md)

![](https://github.com/FizzyStudio/SENZ001-Rotation-Sensor/blob/master/pic/SENZ001.jpg "SENZ001") 

### 产品介绍

> SENZ001 模拟多圈旋转角度传感器是一个Arduino兼容的多圈高精度模拟角度传感器。它基于一个高精度的电位器，可旋转十圈,如果给此传感器输入5V电压供电，这样就是5000mV被分成了3600份（10圈）.这样你旋转3度就可以调节2mV的电压变化,这样就可以精确地实现角度微小变化的互动效果。同时它可以很方便的通过传感器扩展版连接到您的Arduino板。
 
### 技术参数

* Arduino兼容
* 电源要求：+3.3-5V DC
* 外形尺寸：50x22mm
* 信号类型：模拟信号
* 接口模式：PH2.0-3
* 转动角度：3600°
* 重量：20g

### 引脚说明

![](https://github.com/FizzyStudio/SENZ001-Rotation-Sensor/blob/master/pic/SENZ001_pin.png "pin")  

### 使用教程

> 在这个教程中我们旋转模拟角度传感器即可在串口中输出此时的模拟角度传感器的模拟电压值。 

#### 准备

* 硬件
    * UNO x1
    * 模拟角度传感器 x1
* 软件
    Arduino IDE [Click to Download Arduino IDE from Arduino®](https://www.arduino.cc/en/Main/Software)

#### 接线图

![](https://github.com/FizzyStudio/SENZ001-Rotation-Sensor/blob/master/pic/SENZ001_Connection.png "Connection") 

#### 样例代码

    const int analogInPin = A0;         // Analog input pin that the potentiometer is attached to
    const int analogOutPin = 9;         // Analog output pin that the LED is attached to

    int sensorValue = 0;                // value read from the pot
    int outputValue = 0;                // value output to the PWM (analog out)
    
    void setup() {
      // initialize serial communications at 9600 bps:
      Serial.begin(9600);
    }
    
    void loop() {
      // read the analog in value:
      sensorValue = analogRead(analogInPin);
      // map it to the range of the analog out:
      outputValue = map(sensorValue, 0, 1023, 0, 255);
      // change the analog out value:
      analogWrite(analogOutPin, outputValue);
    
      // print the results to the serial monitor:
      Serial.print("sensor = ");
      Serial.print(sensorValue);
      Serial.print("\t output = ");
      Serial.println(outputValue);
    
      // wait 2 milliseconds before the next loop
      // for the analog-to-digital converter to settle
      // after the last reading:
      delay(20);
    }


### 结构图

![](https://github.com/FizzyStudio/SENZ001-Rotation-Sensor/blob/master/pic/SENZ001_Dimension.png "Dimension") 

### 更多
