## 概要
ESP32を用いて、WiFiとMQTTを組み合わせた遠隔アラームのプログラムについて共有します。このプログラムは、メッセージの受信に応じてアラームが鳴る機能を持っています。

## 使用場所
朝、子供がなかなか起きてこない時ありますよね。
そんな時にボタン一つで子供部屋のアラームを鳴らしたくないですか！！
そんなプロダクトになっています。
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2985443/2ad33a63-7b57-3b57-0976-cd9d0328ee93.png)

## 前準備
前準備としてMQTT メッセージ・ブローカーのクラウド・サービスを行っている shiftr.ioの登録をしておきます。

## 1. 必要なライブラリ

以下のライブラリが必要です：

- WiFi
- PubSubClient
- FreeRTOS
- TaskScheduler

## 2. WiFiの設定

ESP32はWiFiを内蔵しており、WiFiライブラリを用いてWiFiに接続します。接続情報はSSIDとパスワードで指定します。

## 3. MQTTの設定

MQTTはIoTデバイス間の通信プロトコルです。このプログラムでは、PubSubClientライブラリを用いてMQTTブローカーに接続し、メッセージの送受信を行っています。

## 4. FreeRTOSとタスクスケジューラ

FreeRTOSはリアルタイムオペレーティングシステムで、ESP32に標準で搭載されています。このプログラムでは、FreeRTOSのタスクとTaskSchedulerライブラリを組み合わせて、音の再生を制御します。
アラームを鳴らすタスクと音を止めるタスクを同時に処理するために使用しています

## 5. LED Control (LEDC)

ESP32のLEDCはPWM（Pulse Width Modulation）を使ってLEDの明るさを制御したり、スピーカーから音を出したりすることができます。このプログラムでは、音階とオクターブを指定して音を出すために使用しています。

## 6. デバウンス処理

スイッチの状態を読み取る際に、スイッチの接触不良による誤動作を防ぐためにデバウンス処理を行っています。

## 7. まとめ

以上が、私が作ったおかんアラームです。実用することを考えるとまだまだな点が多いですが、実装してみたかった挙動ができたので、いい経験になりました。
