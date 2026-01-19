# 蓝牙小发明 Nano学习记录
## 一.关于nano简单学习

### 1.nano板子细节

REF 电压类比信号

A0-A7 模拟输入

D0-D13 数字输入输出(一般不用0和1)

UIF 通用输入/输出

RST 复位

L是D13

RX 接收  TX 发送

### 2.点亮第一个小灯

数字I/o :

#### 1.输入输出模式的定义函数：pinMode(pin, OUTPUT),pin表示引脚号，OUTPUT表示输出模式。输入模式用INPUT。

#### 2.digitalWrite(pin, HIGH),pin表示引脚号，HIGH表示高电平。LOW表示低电平。

```C++
void setup() {
  // put your setup code here, to run once:
pinMode(2, OUTPUT);
}

void loop() {
  // put your main code here, to run repeatedly:
digitalWrite(2, HIGH);
}
//自己把闪烁灯做出
```

#### 3.setup()初始化，loop()循环。

#### 4.延迟毫秒函数：delay(ms)
```C++
 delay(1000);                  // 等待一秒钟（1000毫秒）
```

### 3.蜂鸣器实验

#### 1.delayMicroseconds(us)微秒
1ms=1000us

#### 2.tone(pin, frequency),tone(pin, frequency, duration)发出声音，noTone(pin)停止发声
```C++
void setup() {
  // put your setup code here, to run once:
  pinMode(9, OUTPUT);           // 定义引脚9为输出模式
}

void loop() {
  // put your main code here, to run repeatedly:
  tone(9, 262);   
  delay(1000);                      // 发出262Hz的声音 
  noTone(9);                        // 停止发声
  delay(1000);                      // 等待一秒钟
```
```C++
void loop() {
  tone(3, 456,100);   
    delay(100);   
  noTone(3);                        
  delay(1000);     
  }   
  ```
#### 3.for循环,int 数据类型整数型变量
```C++
int i, sum=0;
    for(i=1; i<=100; i++){
       sum = sum + i;
    }  
```
```C++
void setup() {
  // put your setup code here, to run once:
  pinMode(3, OUTPUT);   
}

void loop() {
  // put your main code here, to run repeatedly:
int i=200; 
 for(i=200;i<=800;i++){
   tone(3, i);   
   delay(100); 
   }
 for(i=800;i>=200;i--){
  tone(3,i);
  delay(100);
 }  
}   
```
 

