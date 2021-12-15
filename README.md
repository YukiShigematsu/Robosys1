# Robosys1
ロボットシステム学＿課題１
---
## 概要
ロボットシステム学の課題１として作成したデバイスドライバです。
入力するアルファベット(f,t,c,b)に応じて信号を他のデバイス（ここではSTM32F446RE_NUCLEO_board）に送信するデバイスドライバです。
本デバイスドライバは、上田隆一准教授が授業で作成したデバイスドライバを改変し作成しています。

[講義動画](https://youtu.be/xQW8-FNuboo)

---
## 使用用途
本ドライバは複数の他マイコンボードに同時に信号を送ることができるため、複数のマイコンボードを同時に操作したり、Raspberry Pi4だけではピンが足りない場合に他のマイコンボードを使用しピン数を拡張することができます。

---
## 動画
- 画像をクリックするとYoutubeで動画が再生されます
[![動画](https://user-images.githubusercontent.com/71487860/145938169-916bef1c-61d3-44b5-a926-83bbaa775269.png)](https://youtu.be/oucpeo4s29Q)

---
## 使用物品
|No.|物品名|数量|
|---|---|---|
|1|Raspberry Pi4 ModelB / 8GB|1|
|2|ブレッドボード|3|
|3|ジャンパ線|29|
|4|ラズベリーパイＢ＋／Ａ＋用ブレッドボード接続キット|1|
|5|NUCLEO-F334R8|2|
|6|抵抗器(220Ω)|9|
|7|抵抗内蔵LED(青)|4|
|8|抵抗内蔵LED(赤)|3|
|9|抵抗内蔵LED(緑)|4|
|10|LED(青)|3|
|11|LED(白)|3|
|12|LED(黄)|3|

---
## 回路
- 回路図

[回路図](https://github.com/YukiShigematsu/Robosys1/files/7704363/robosys.pdf)
<img src="https://user-images.githubusercontent.com/71487860/145825689-92980b45-2893-464c-b717-ce4328092da1.png" width="1280px">

- 実配線
<img src="https://user-images.githubusercontent.com/71487860/145822958-991d4a53-fa69-4dfc-919d-0c086c2d226a.jpg" width="640px">

#### 使用するGPIOピンと用途
- Raspberry Pi4 ModelB / 8GB

|NO.|GPIOピン|用途|
|---|---|---|
|1|５V PWRV PWR|NUCLEO-F446REへの5V供給|
|2|GND|NUCLEO-F446RE、各LEDとのGND共通化|
|3|GPIO24|通信の開始と終了の信号を送信|
|4|GPIO25|通信の内容を送信|

- NUCLEO-F446RE

|NO.|GPIOピン|用途|
|---|---|---|
|1|+５V|Raspberry Pi4 からの5V供給|
|2|GND|Raspberry Pi4、各LEDとのGND共通化|
|3|PA5|LEDのアノードへ電圧供給|
|4|PA6|LEDのアノードへ電圧供給|
|5|PA7|LEDのアノードへ電圧供給|
|6|PA8|LEDのアノードへ電圧供給|
|7|PA9|LEDのアノードへ電圧供給|
|8|PB4|LEDのアノードへ電圧供給|
|9|PB6|LEDのアノードへ電圧供給|
|10|PB8|Raspberry Pi4から通信の開始と終了の信号を受信|
|11|PB9|Raspberry Pi4から通信の内容を受信|
|12|PB10|LEDのアノードへ電圧供給|
|13|PC7|LEDのアノードへ電圧供給|

---

## ビルド方法(Raspberry Pi4 ModelB / 8GB)
~~~
$ git clone https://github.com/YukiShigematsu/Robosys1.git
$ cd Robosys1
$ make
$ sudo insmod signal.ko
$ sudo chmod 666 /dev/signal0
~~~

## ビルド・デバック方法（NUCLEO-F446RE）

[Cube IDE](https://www.st.com/ja/development-tools/stm32cubeide.html)を使用して[Receive.c](https://github.com/YukiShigematsu/Robosys1/blob/main/STM_Receive.c)を書き込んでいます。

---

## 実行方法
1. #### flow

`$ echo f > /dev/signal0`
- NUCLEO-F446REに接続されているLEDが流れるように点滅する信号を送信します

2. #### cross

`$ echo c > /dev/signal0`
- NUCLEO-F446REに接続されているLEDが交わるように点滅する信号を送信します

3. #### together

`$ echo t > /dev/signal0`
- NUCLEO-F446REに接続されているLEDが3つずつ点滅する信号を送信します

4. #### blinking

`$ echo b > /dev/signal0`
- NUCLEO-F446REに接続されているLEDが同時に点滅する信号を送信します

---
## 終了方法

```
$ sudo rmmod signal
$ make clean
```
---

## License
[GNU General Public License v3.0](https://github.com/YukiShigematsu/Robosys1/blob/main/COPYING)
