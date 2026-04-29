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

```C++
void setup() {
    pinMode(2, OUTPUT);
}
void loop() {
    digitalWrite(2, HIGH);
    delay(1000);
    digitalWrite(2, LOW);   
    delay(1000);
}