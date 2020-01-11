## How to use Seeeduino XIAO to log in to your Raspberry PI


Sometimes when we use Raspberry Pi, these situations can be very disturbing to us: no extra HDMI displays around, mouse and keyboard are not easy to connect, choose to log in to the raspberry pie with the USB to Serial adapter, but it's too expensive. Now, with Seeeduino XIAO, all problems are readily solved.

### Hardware

**Materials required**

- [Seeeduino XIAO x1](http://www.seeedstudio.com/.html)

- Raspberry PI Zero x1

- Dupont cable x3

- Type-C cable x1

### Hardware Overview

The following figure is the pin map of Raspberry Pi:


![](https://github.com/SeeedDocument/Seeeduino-XIAO/raw/master/img/Raspberry-PI-pinout.png)


The following figure is the pin map of Seeeduino XIAO:


![](https://raw.githubusercontent.com/SeeedDocument/Seeeduino-XIAO/master/img/Seeeduino-XIAO-pinout.jpg)


**Hardware Connection**

- **Step 1.** Raspberry PI's **TX** is connected to Seeeduino XIAO's **RX**

- **Step 2.** Raspberry PI's **RX** is connected to Seeeduino XIAO's **TX**

- **Step 3.** Raspberry PI's **GND** is connected to Seeeduino XIAO's **GND**

- **Step 4.** Connect Seeeduino XIAO to PC via a Type-C cable.

- **Step 5.** The raspberry pie is connected to a power supply.


### Software

Find the config.txt file on the TF card of the Raspberry Pi official system, and add a sentence at the end:

```c
enable_uart=1
```


After saving, first open the serial port communication software on your PC and set the serial port baud rate to 115200. This is the default serial port baud rate. It can be communicated correctly if it is consistent with the serial port baud rate of the Raspberry Pi. After inserting the card to start the Raspberry Pi, you will see the startup information in the terminal window.



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

