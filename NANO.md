# NANO

## 一.初识

模拟输入：A0-A7

数字引脚：D2-D13

### 结构

Setup()函数：初始化

Loop()函数：主函数

pinMode（pin,mode）————pin表示0-13，mode表示OUTPUT输出和INPUT输入

digitalWrite(pin,value)————value表示HIGH高电平和LOW低电平

digitalRead(pin)————数字IO读取

delay(ms)————延迟函数（单位ms）（毫秒）

delayMicroseconds(us)————（微秒）

### 点亮led灯

text01

```c++
void setup() {
    pinMode(2, OUTPUT);
}
void loop() {
    digitalWrite(2, HIGH);
    delay(1000);
    digitalWrite(2, LOW);   
    delay(1000);
}
```

### Arduino循环

- **while循环**

while循环将会连续、无限循环，直到括号()内的表达式变为false。必须用一些东西改变被测试的变量，否则while循环永远不会退出。

- **do...while循环**

**do ... while**循环类似于while循环。在while循环中，循环连续条件在循环开始时测试，然后再执行循环体。do ... while语句在执行循环体之后测试循环连续条件。因此，循环体将被执行至少一次。

-  **for循环**

**for循环**执行语句预定的次数。循环的控制表达式在for循环括号内完全的初始化，测试和操作。

-  **嵌套循环**

C语言允许你在另一个循环内使用一个循环。

- **无限循环**

它是没有终止条件的循环，因此循环变为无限。

```c++
for (;;) {
   // statement block
}
```

```c++
while(1) {
   // statement block
}
```

```c++
do {  
   Block of statements;
   }  
   while(1);
```

### 七彩LED灯闪烁

注意：模块上有两个GND，你只需要连接其中一个

实验原理：电源打时，7彩LED将闪烁内置颜色

### 关键字

**if（){...}else{...}**     如果（条件）执行...否则执行...

### 数据类型

**boolean**    布尔类型

### 轻触开关按键实验

text02

````c++
int p2 = 2;

int p3 = 3; 

void setup() {

  pinMode(2, OUTPUT);//数字2管脚输出，led

  pinMode(3,INPUT);//数字3管脚，按钮输入

  }

void loop() {

  boolean value = digitalRead(p3);

  if(value == HIGH){

  digitalWrite(p2, LOW);

  }

  else{

  digitalWrite(2, HIGH);  

  }  

}
````

### 振动开关传感器实验

实验原理：一旦摇动，led灯就亮（动为high,不动为low）

text03

```c++
int p2 = 2;

int p3 = 3;

int p10 = 10; 

void setup() {

  pinMode(2, OUTPUT);//数字2管脚输出，led

  pinMode(3,OUTPUT);

  pinMode(10,INPUT);//数字10管脚，振动模块输入

  }

void loop() {

  boolean value = digitalRead(p10);

  if(value == HIGH){

  digitalWrite(p2, HIGH);

  digitalWrite(p3, HIGH);

  }

  else{

  digitalWrite(p2, LOW);  

  digitalWrite(p3, LOW);

  }  

}
```

### 触摸开关传感器实验

实验原理：触摸点亮小灯

摸：HIGH；不摸：LOW

代码自己写写，跟上面类似

### 红外遥控实验

红外接收头只要接受38KHz的频率红外线，对其他频率段的红外信号不敏感。这样遥控器就可以发出载波在38KHz的频率，就能接受信号，从而构成通讯。

任务：通过遥控器控制某个键（如电源键），按键时让双色灯发红，不按为蓝。

IRremote库[IRremote库 – 太极创客](http://www.taichi-maker.com/homepage/reference-index/arduino-library-index/irremote-library/)

常用红外协议资料

NEC协议：地址信息+指令信息

1838红外接收器

![6](imageaduino/6)

安装IRremote库：项目--导入库--管理库![7](imageaduino/7.png)

decode函数：用于判断红外接收器所接收到的红外信号是否可以被解析。if成功，返回非零值，将解析结果存储于results;if不成功，返回0。

text04

```c++
// 1. 包含新版红外库的头文件
#include <IRremote.hpp>

// 2. 定义引脚名字（方便改，一看就懂）

const int irReceiverPin = 7;  // 红外接收器信号脚接 D7

const int ledPin = 13;     // 板载LED脚 D13

// 3.  setup：只运行一次（初始化）

void setup() {

 pinMode(ledPin, OUTPUT);   // 把LED脚设置为输出模式

 Serial.begin(9600);      // 开启串口，波特率9600（看打印信息）

 IrReceiver.begin(irReceiverPin); // 启动红外接收功能

}

// 4. loop：不断重复运行

void loop() {

 // 如果**接收到了红外信号**

 if (IrReceiver.decode()) {

  // 把收到的红外码打印到串口监视器（方便你看）

  Serial.print("收到红外码: 0x");

  Serial.println(IrReceiver.decodedIRData.decodedRawData, HEX);

  // 判断：是不是我们要的那个按键码

  if (IrReceiver.decodedIRData.decodedRawData == 0xBA45FF00) {

   digitalWrite(ledPin, HIGH);  // 是 → 点亮LED

  } else {

   digitalWrite(ledPin, LOW);  // 不是 → 熄灭LED

  }

  IrReceiver.resume(); // 准备接收下一个信号

 }

}
```

