
![](http://raw.githubusercontent.com/SeeedDocument/Seeeduino-XIAO/master/img/Seeeduino-XIAO-preview-1.jpg)

Seeeduino XIAO是Seeeduino最小的开发板。它搭载了功能强大的ATSAMD21G18A-MU低功耗微控制器。另一方面，这种小电路板具有良好的处理性能，并且需要的功率较小。它的设计尺寸很小，可用于可穿戴设备和小型项目。

Seeeduino XIAO有14个GPIO引脚，可用于11个数字接口、11个模拟接口、10个PWM接口（D1-D10）、1个DAC输出引脚D0、1个SWD 焊盘接口、1个I2C接口、1个SPI接口、1个UART接口、串行通信指示灯（T/R）、闪烁灯（L）。LED（电源、L、RX、TX）的颜色为绿色、黄色、蓝色和蓝色。此外，Seeeduino XIAO使用Type C接口，用来提供电源和下载代码。有两个复位按钮，可以短接复位。

[Get One Now](http://www.seeedstudio.com/Seeeduino-XIAO-Arduino-Microcontroller-SAMD21-Cortex-M0+-p-4426.html)


## 特征


- 强大的CPU: ARM·Cortex-M0+32位48MHz微控制器（SAMD21G18），256KB闪存，32KB SRAM。

- 灵活兼容性：兼容ARDUNO IDE。

- 简单的项目操作：好用的开发板。

- 小尺寸：适用于可穿戴设备和小型项目，尺寸为23.5x17.5mm。

- 多个开发接口：11个数字/模拟管脚、10个PWM管脚、1个DAC输出、1个SWD焊盘接口、1个I2C接口、1个UART接口、1个SPI接口。


## 参数


|项目 |参数|
|----|----|
|CPU |ARM Cortex-M0+CPU（SAMD21G18，运行频率高达48MHz |
|闪存|256KB|
|内存|32KB|
|数字I/O引脚|11|
|I2C接口|1|
|SPI接口|1|
|UART接口||
|电源及下载接口|Type C|
|电源|3.3V/5V DC|
|尺寸|23.5×17.5×3.5mm |



 
！注意： 

1.本设计的单片机采用3.3v供电，请注意不要将5V的IO电平引入系统的IO接口，否则会损坏芯片。 

2.请小心使用，不要掀起外壳。 
 


## 硬件概述


![](https://raw.githubusercontent.com/SeeedDocument/Seeeduino-XIAO/master/img/Seeeduino-XIAO-pinout.jpg)

![](https://github.com/SeeedDocument/Seeeduino-XIAO/raw/master/img/Seeeduino%20XIAO%20pinout2.jpg)

## 入门


#### 硬件

**所需材料**



- Seeeduinox1

- 计算机x1

- Type C线x1 
 
!!!提示

    有些USB电线只能供电，不能传输数据。如果您没有USB线或不知道您的USB电线是否可以传输数据，您可以检查一下[USB Type-C ]（https://www.seeedstudio.com/usb-type-C-to-a-cable-1Meter-p-4085.html）。



- 步骤1.准备一个Seeeduino XIAO和一根C型电缆。 



- 步骤2.将Seeeduino XIAO连接到您的计算机。黄色电源指示灯会亮起。
 

#### 软件


!!!注意 

    如果这是您第一次使用Arduino，我们强烈建议您参考[Arduino入门]（http://wiki.seed.cc/Getting_Started_with_Arduino）



- **步骤1.你需要安装一个Arduino软件**
 

[下载 Arduino IDE](http://www.arduino.cc/en/Main/Software)  

启动Arduino应用程序

双击之前下载的Arduino应用程序（Arduino.exe）。

!!!注意

如果Arduino软件以其他语言加载，则可以在“首选项”对话框中对其进行更改。有关详细信息，请参阅[Arduino软件（IDE）页面]（https://www.Arduino.cc/en/Guide/Environment#languages）。



- **步骤2.打开闪烁示例**

打开LED闪烁示例程序：文件>示例>01.Basics>Blink。 
![](https://raw.githubusercontent.com/SeeedDocument/Seeeduino_GPRS/master/img/select_blink.png)

- **步骤3.将Seeeduino添加到Arduino IDE中**

单击“文件>首选项”，并用以下url填入到 其他开发板管理器url:[https://raw.githubusercontent.com/Seeed-Studio/Seeeduino-Boards/master/package_seeeduino_index.json]
![](https://raw.githubusercontent.com/SeeedDocument/Seeeduino-Femto/master/.img/wiki2.png))
 
 
单击“工具”->“电路板”->“电路板管理器…”，在搜索空白处输入关键字“Seeeduino XIAO”。这里是“Seeed SAMD板”。然后安装。

![](https://raw.githubusercontent.com/SeeedDocument/Seeeduino-XIAO/master/img/Seeeduino-XIAO-board.png )

- **步骤4.选择您的板和端口**

安装板后，点击工具->板，找到“Seeeduino XIAO M0”并选中。现在您已经在Arduino IDE中添加了Seeeduino XIAO开发板。

![](https://raw.githubusercontent.com/SeeedDocument/Seeeduino-XIAO/master/img/board.png )

从“工具”|“串行端口”菜单中选择Arduino板的串行设备。可能是COM3或更高版本（**COM1**和**COM2**通常为硬件串行端口保留）。如果您不清楚的话，可以断开开发板并重新打开菜单；消失的条目应该是这个开发板。重新连接板并选择该串行端口。

![](https://raw.githubusercontent.com/SeeedDocument/Seeeduino-XIAO/master/img/port.png )
 


- **步骤5.上传程序**

现在，只需在IDE中单击“上载”按钮。稍等几秒钟，如果上传成功，状态栏中将显示消息“Done uploading.”。

![](https://raw.githubusercontent.com/SeeedDocument/Seeeduino_GPRS/master/img/upload_image.png )

上传完成几秒钟后，您应该会看到板上的引脚13（L）LED开始闪烁（橙色）。如果是的话，恭喜你！你已经让Seeeduino XIAO开始运行了。如果您有问题，请参阅故障排除建议。 

## 示例应用程序 

- [USB转串口](https://github.com/SeeedDocument/Seeeduino-XIAO/blob/master/USB-to-Serial-Port.md)

- [SPI通信](https://github.com/SeeedDocument/Seeeduino-XIAO/blob/master/SPI-Communication-Interface.md)

## 资源


- **[PDF]** [Seeeduino XIAO](https://github.com/SeeedDocument/Seeeduino-XIAO/raw/master/res/Seeeduino-XIAO-v1.0-SCH-191112.pdf)

- **[PDF]** [ATSAMD218A-MU datasheet](https://github.com/SeeedDocument/Seeeduino-XIAO/raw/master/res/ATSAMD21G18A-MU-Datasheet.pdf)


## 技术支持

您可以把问题提交到我们的[论坛](http://forum.seeedstudio.com/)。
