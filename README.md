# Robosys1
ロボットシステム学＿課題１
---
## 概要
ロボットシステム学の課題１として作成したデバイスドライバです。
入力するアルファベット(f,t,c,b)に応じて信号を他のデバイス（ここではSTM32F446RE_NUCLEO_board）に送信するデバイスドライバです。
本デバイスドライバは、上田隆一教授が授業で作成したデバイスドライバを改変し作成しています。

[講義動画](https://youtu.be/xQW8-FNuboo)

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
|1|５V PWRV PWR|NUCLEO boardへの5V供給|
|2|５V PWRV PWR|NUCLEO board、各LEDとのGND共通化|
|3|GPIO24|通信の開始と終了の信号を送信|
|4|GPIO25|通信の内容を送信|

---
