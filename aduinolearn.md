# Arduino 

（随便写着玩）

## 一、双色LED实验

### 1.介绍：双色LED模块

![](imageaduino\image.png)

双色LED是一种可以显示二色颜色的LED灯,  可以有三种状态:  灭,  颜色1亮, 颜色2亮 .  根据颜色组合的不同,  分为红蓝双色,  黄蓝双色, 红绿双色等等。

| - |中间|S|
| - | - | - |
| GND |数字IO|数字IO|

**中间高电平，LED亮灯一种颜**
**S高电平，LED亮灯另一种颜色**


### 2.实验原理

通过数字端口控制LED亮度。LED的颜色从红变绿并混合闪烁。

### 3.代码

```C++
int redPin=2;//2为中
int greenPin=3;//3为S
void setup() {
  // put your setup code here, to run once:
pinMode(redPin,OUTPUT);
pinMode(greenPin,OUTPUT);//为输出状态
Serial.begin(9600);
}

void loop() {
//熄灭
  digitalWrite(redPin, LOW);  
  digitalWrite(greenPin, LOW);  
  delay(1000); 
//颜色1亮
  digitalWrite(redPin, HIGH);  
  digitalWrite(greenPin, LOW);  
  delay(1000); 
  //颜色2亮
  digitalWrite(redPin, LOW);  
  digitalWrite(greenPin, HIGH);  
  delay(1000); 
 
  //颜色1亮 + 颜色2亮 （形成混合色小黄）
  digitalWrite(redPin, HIGH);
  digitalWrite(greenPin, HIGH); 
  delay(1000); 

}

```

## 二.七彩LED灯模块

### 1.介绍七彩LED灯模块

![](imageaduino\image1.png)

直接**S接5V,剩下俩二选一接GND**,就可以看的闪烁七种颜色

## 三.继电器实验

### 1.介绍

![](imageaduino\image2.png)

继电器本质上是一个**电磁开关**，其核心价值在于：

**小控大**：用一个很小的控制信号（比如来自微控制器的5V电压），去控制一个大电流或高电压电路（如220V交流电）的通断。

**电气隔离**：由于继电器内部通过电磁原理工作，控制电路和被控电路之间没有物理连接，起到了隔离保护作用，避免高压损坏微控制器。

### 2.实验原理

#### 2.1一个继电器由5个基本部件组成：

1.**电磁铁**：由一个线圈缠绕的贴心组成，当电流通过时，它变成磁性的，因此它被称为电磁铁。

2.**电枢**：可移动磁条被称为电枢。当电流流过时，线圈通电，从而产生一个磁场，用于造成断开或闭合。电枢可以在AC或DC上工作。

3.**弹簧**：当没有电流流过电磁铁上的线圈时，弹簧将电枢拉开，因此电路无法完成。

4.**触点**：有两个触点：

常开：线圈不通电 → 触点断开；线圈通电 → 触点闭合。

常闭：线圈不通电 → 触点闭合；线圈通电 → 触点断开。

5.**膜制外壳**：继电器覆盖有塑料以保护内部电路

#### 2.2继电器工作

继电器的工作原理很简单，当继电器供电时，电流开始流经控制线圈；结果电磁体开始通电，然后衔铁被吸引到线圈上，将动触点向下拉，从而与常开触点连接，进而让带负载的电路通电，然后断开电路会出现类似的情况。因为在弹簧的作用下，动触头将被拉离常开触点，这样，继电器的接通和断开就可以控制负载电路的状态了。

![](imageaduino\image3.png)

### 3.代码

```C++
const int relayPin=2;//定义2脚为信号引脚  const指不可修改relayPin的值，不加也可以
void setup() 
{
  pinMode(relayPin,OUTPUT);//定义输出端口
}
void loop() 
{
  digitalWrite(relayPin,HIGH);//输出高电平
  delay(1000);//延时1秒
  digitalWrite(relayPin,LOW);//输出低电平
  delay(1000);
}
```

将程序上传到Arduino板子上后，我们就可以听到滴答声了，这是常开触点打开和常开触点闭合的声音。

[← 点击返回首页](sslocal://flow/file_open?url=https%3A%2F%2FLBYaz.github.io%2Findex.html&flow_extra=eyJsaW5rX3R5cGUiOiJjb2RlX2ludGVycHJldGVyIn0=)