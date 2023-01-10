---
layout: post
title: "Implementasi Analog Turbidity Sensor pada ATTiny88 dengan BASCOM-AVR"
tags: software
---

Sensor yang saya pakai adalah _Gravity: Analog Turbidity Sensor For Arduino_ dari **DFROBOT** yang saya beli dari Tokopedia dengan [link ini](https://www.tokopedia.com/breakneck/dfrobot-analog-turbidity-sensor-for-arduino) dan dokumentasi yang bisa dibaca dengan [link ini](https://wiki.dfrobot.com/Turbidity_sensor_SKU__SEN0189).

Sensor ini saya pakai untuk proyek akhir mata kuliah Sistem Tertanam saya, dimana diwajibkan oleh dosen untuk mengimplementasikan sensor pada microcontroller dan hasil pengukuran dari sensor tersebut dikirimkan melalui TTL kepada laptop yang akan ditampilkan pada software _Labview_. TTL memiliki 4 kabel (Merah untuk 5V, Hitam untuk Ground, Putih untuk RXD, dan Hijau untuk TXD).

Kode yang saya pakai adalah seperti berikut:

```basic
$regfile = "attiny88.dat"
$crystal = 16000000
$hwstack = 32
$swstack = 10
$framesize = 40

Config Adc = Single , Prescaler = Auto , Reference = Internal
Start Adc

Dim Adcinput As Word

Open "COMD.1: 19200,8,n,1" For Output As #1
Open "COMD.0: 19200,8,n,1" For Input As #2

Do

   Adcinput = Getadc(0)

   Print #1 , Adcinput ; "#"

   Waitms 300

Loop
```

Berbeda dengan example 1 pada https://wiki.dfrobot.com/Turbidity_sensor_SKU__SEN0189, saya tidak diminta mengkonversi nilai ADC ke dalam bentuk volt. Dari kode diatas bisa dilihat bahwa:

- Saya memakai A0 pada ATTiny88 saya
- Saya memasang Kabel Hijau dari TTL saya pada D0
- Saya memasang Kabel Putih dari TTL saya pada D1

Intisari dari memakai ADC adalah kita harus mengalirkan ground dan Vout dari sensor, keduanya melalui resistor kepada pin ADC yg ingin kita pakai. Saya gambarkan melalui Tinkercad dibawah:

<img src="assets/posts/schematic-turbidity-2023.png" />

Untuk breadboardnya terlihat seperti berikut (maaf tidak begitu jelas):

<img src="assets/posts/breadboard-turbidity-2023.jpeg" />

Lalu, pada Terminal di BASCOM-AVR akan terlihat seperti berikut:

<img src="assets/posts/terminal-turbidity-2023.jpeg" />

dan pada Labview seperti ini:

<img src="assets/posts/labview-turbidity-2023.png" />

Jika ada pertanyaan, jangan sungkan bertanya melalui email: `caxvis at gmail dot com`.


