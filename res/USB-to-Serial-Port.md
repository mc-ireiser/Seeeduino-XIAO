## USB to Serial Port


### Hardware

**Materials required**

- [Seeeduino XIAO x1](http://www.seeedstudio.com/.html)

- [UartSBee v5 x1](https://www.seeedstudio.com/UartSBee-V5.html)

- USB typc cable x1

- Type-C cable x1

**Hardware Connection**

- **Step 1.** UartSBee v5's **TX** is connected to Seeeduino XIAO's **RX**

- **Step 2.** UartSBee v5's **RX** is connected to Seeeduino XIAO's **TX**

- **Step 3.** UartSBee v5's **GND** is connected to Seeeduino XIAO's **GND**

- **Step 4.** Connect Seeeduino XIAO to PC via a Type-C cable.

- **Step 5.** Connect UartSBee v5 to PC via a USB cable.

![](https://raw.githubusercontent.com/SeeedDocument/Seeeduino-XIAO/master/img/usb-ttl.jpg)

### Software


!!!Attention

    If this is the first time you work with Arduino, we strongly recommend you to see [Getting Started with Arduino](http://wiki.seeedstudio.com/Getting_Started_with_Arduino/) before the start.



- **Step 1.** Copy the code below into Arduino IDE and upload. If you do not know how to upload the code, please check [how to upload code](http://wiki.seeedstudio.com/Upload_Code/).


```c
/*
   This example is used for USB to ttl.
   update file Arduino15\packages\Seeeduino\hardware\samd\1.6.0\cores\arduino\USB\USBAPI.h

    class Serial_ : public Stream
    {
    public:
      ......
      ......
      //add
      uint32_t getBaud(void);
      ......
    }

   update file Arduino15\packages\Seeeduino\hardware\samd\1.6.0\cores\arduino\USB\CDC.cpp
   //add
    uint32_t Serial_::getBaud(void)
    {
     return _usbLineInfo.dwDTERate;
    }
*/

uint32_t baud;
uint32_t old_baud;
void setup() {

  // put your setup code here, to run once:
  SerialUSB.begin(115200);
  baud = SerialUSB.getBaud();
  old_baud = baud;
  Serial1.begin(baud);
  while (!Serial);
  while (!SerialUSB);
}

void loop() {
  // put your main code here, to run repeatedly:
  baud = SerialUSB.getBaud();
  if (baud != old_baud) {
    Serial1.begin(baud);
    while (!Serial);
    old_baud = baud;
    //     SerialUSB.println(baud);
  }
  if (SerialUSB.available() > 0)
  {
    char c = SerialUSB.read();
    Serial1.write(c);
  }
  if (Serial1.available() > 0) {
    char c = Serial1.read();
    SerialUSB.write(c);
  }
}
```
- **Step 2.** Open the **Serial Monitor** of Arduino IDE by click **Tool-> Serial Monitor**. Or tap the **ctrl+shift+m** key at the same time. Set the baud rate to **9600**.
- **Step 3.** Open the serial debugging assistant, set the baud rate to 9600.
- **Step 4.** Now you can communicate between USB and serial port.