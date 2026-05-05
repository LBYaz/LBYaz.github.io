# NANO

## 一.初识

模拟输入：A0-A7

数字引脚：D2-D13

### 结构

Setup()函数：初始化

Loop()函数：主函数

pinMode（pin,mode）————pin表示0-13，mode表示OUTPUT输出和INPUT输入

digitalWrite(pin,value)————value表示HIGH高电平和LOW低电平

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