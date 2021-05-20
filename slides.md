---
theme: seriph
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
---
# 研究室ツール紹介
## Drone編

岩見彰太

### 武市研究室　M2
### 2021/05/20


---

# Agenda

1. ドローン関係の法律
   - 航空法, 民法, 条例, 電波法...
2. ドローン業界図
   1. PX4
   2. DJI
3. 研究室で使用しているツール
   1. SITL
      1. Drone Kit
      2. Gazebo
      3. QGroud Control
      4. (ulog)
      5. (Flight Review)
  
<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>


---

# 航空法

- 人口密集地などの空域においては、あらかじめ航空局に申請を提出し、承認を受けなければならない
- 飛行方法
  - 日の出から日没まで（夜間飛行は別途申請が必要）
  - 催しが行われている上空での飛行禁止（別途申請が必要）　etc.
- ※ しかし、200g以下の機体は、規制される無人航空機に含まれない
  <br>（2022年度に100gに制限が引き下げられる予定…）

<br>

# 民法
- 土地所有権
  - 民法207条「土地所有権の範囲」に基づき、他人の土地で無許可にドローンを飛行させてしまうと土地所有権の侵害
  - しかし、現状「飛行させた際の不利益」証明できなければ訴えることができない


<style>
h1 {
  font-size: 30px;
  margin-top: 10px;
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>

---

# 小型無人気筒飛行禁止法（議員立法）
- 「重要な施設の周辺地域の上空における小型無人機等の飛行の禁止関する法律」

# 道路交通法
- 公道上空での飛行は、一般交通に影響を及ぼすものとされるため、一般的には所轄警察署所長の許可が必要

# 条例
- 各地域で独自に無人航空機に関する条例が定められている
  - ex.) 東京都立公園条例


# 電波法
- セルラードローンの規制
  - 携帯キャリアの通信網を利用して通信を行うドローンのこと
  - 現在は実用化試験局の免許手続きを行った場合に限り、実用化試験可能


<style>
h1 {
  font-size: 30px;
  margin-top: 10px;
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>



---

# ドローン業界図

## 業界シェア


<br>

<!-- <div class="grid grid-cols-2 gap-2"> -->
<div class='flex mb-10'>

<div class="w-6/10">

- 中国の大手メーカー DJI がトップを独走
- しかし外交関係から、アメリカなどではDJIの機体を政府の利用するから完全に除外する制裁を発動
- 今後、DJI以外のメーカーからこの辺りの需要を突くような製品の開発が進んでいくと思われる
  - と、ずっと言われているがDJIの技術力が高すぎるためどこも追いつけない
- ENRIでもDJIのドローンの使用は禁止されたらしいので、日本でも政府系の利用は今後厳しいかもしれない
- 民間ではDJI機体は積極的に用いられている



</div>

<div class="w-4/10" m="-t-13">
<!-- <div m="-t-13"> -->
  <img border="rounded" src="https://www.drone.jp/wpdronenews/wp-content/uploads/2021/03/DIII2021.jpg" class='object-contain object-bottom h-full w-full'>
  
  ### 2021年3月現在アメリカのドローン市場

</div>

</div>


### [DRONEII、ドローンメーカーマーケットシェア2020 TOP10発表！中米紛争後の米国ドローン市場シェアはどうなった？](https://www.drone.jp/news/2021030811351043980.html)



---

# ドローン業界図


<div class="grid grid-cols-2 gap-2" m="-t-2">
<div>
  
  ## PX4
  
  - 世界で最も大きなOSS ドローンソフトウェア
  - 各社製品で、これをベースに自社開発しているプロダクトも多い（最近だとSONYとか）
  - かつて3D Ropbotics社が管理しており、その際に作られたラッパーライブラリも多い
	（以前使用した `drone-kit` はこれ）


  
  
</div>

<div>
  
  ## DJI
  - 世界最大手中国ドローンメーカー
  - テレビで空撮の映像が流れたら、100% DJI製
  - 実は元々ジンバルを作っていた会社
  - DJI SDK を利用可能な機体は、自分でカスタマイズできる（後述）


</div>

<img border="rounded" src="https://www.dronecode.org/wp-content/uploads/sites/24/2018/12/px4-logo.png" class='object-contain object-bottom h-30 w-full'>


<img border="rounded" src="https://i.pinimg.com/600x315/11/98/9c/11989c78749b3a01f0f201ef25971035.jpg?raw=true" class='object-contain object-bottom h-30 w-full'>
  
</div>


---
layout: image-left
image: https://shop.skylinkjapan.com/html/upload/save_image/0527121648_5ceb56a0be7e1.jpg
---


# Matrice 600

## 研究室で買った機体

<br>

- いくつかある DJI SDK の内 **Onbord SDK** が使える
  - シリアル接続により、直接フライトコントローラーと通信ができる
  - センサーのデータを自由に取れる
  - それを利用して飛行軌道の制御ができる
- 高い

---

# そもそも DJI SDK とは

- DJI製の機体を開発するためのキット
- それぞれ用途により分かれている
- 研究において（もし使うとしたら）関係あるのは Mobile SDK と Onbord SDK
  - Mobile SDK
    - RC で操作するAndroid or iOS アプリ開発用のSDK（Swift, Kotlin） 
    - サポートされているセンサーデータの取得や飛行指示などが利用できるはず
  - Onbord SDK
    - 機体に相乗りさせて利用する際に使用するSDK
    - Raspberry piなどのマイコンから何か操作する際に利用

<img border="rounded" src="https://www.drone.jp/wpdronenews/wp-content/uploads/2019/02/Bpl28_4.jpg" class='object-contain object-centor h-40 w-full'>


---
layout: fact
---


# PX4

今まで研究室（自分）が利用してきたのはこっち


---

# 最終実装目標はこのSITLが回せること

<Youtube id="LXGnrjaE5Fg?t=98" class="h-100 w-full"/>


<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>

---


# 技術スタック

1. Drone Kit
   - Pythonのラッパーライブラリ
2. Gazebo
   - 3D シミュレーター（ ※ Windows では動きません）
3. QGroud Control
   - PX4 を制御・監視モニタリングする地上局ソフト
4. ulog
   - PX4 などのデバイスで使用される特殊な log ファイル
5. Flight Review
   - 即座にフライトログを確認できるWEB App

---


# SITLとは？

## Software in the Loop

<div class="grid grid-cols-2 gap-10" m="-t-2">

<div>

<br>

- ハードウェアなしで、機体の飛行をシミュレーションすること。
- 今回の場合は、シミュレーターで PX4 を起動して、そこに対して Gazebo で仮想環境（風や重力加速度等）を模擬して検証する
</div>
<div>
  
[![Image from Gyazo](https://i.gyazo.com/a14a66adb75dca55990ef6e52220bcee.png)](https://gyazo.com/a14a66adb75dca55990ef6e52220bcee)

</div>
</div>

---

# 環境構築（Mac OS の場合)

```py {all|1-2|4-7|9-10|0}
$ brew tap PX4/px4
$ brew install px4-dev

# install required packages using pip3
$ python3 -m pip install --user pyserial empy toml numpy pandas jinja2 pyyaml pyros-genmsg packaging
# if this fails with a permissions error, your Python install is in a system path - use this command instead:
$ sudo -H python3 -m pip install --user pyserial empy toml numpy pandas jinja2 pyyaml pyros-genmsg packaging

$ brew install --cask xquartz
$ brew install px4-sim-gazebo`

```

clone
sumodule が大量にあるので、--recursiveを忘れない

```py{0|1|0}
$ git clone https://github.com/PX4/PX4-Autopilot.git --recursive
```

シミュレーター実行

```py{0|all}
$ cd /path/to/PX4-Autopilot
$ make px4_sitl gazebo
```

---

# drone-kit の install 
### （これで、pythonで機体を操作できるようになる）


<div class="grid grid-cols-2 gap-10" m="-t-2">

<div>

作業ディレクトリで実行
自分の場合は、pyenvで仮想環境を作った
```py {all|1-3|5-6|8-9|11|all}
# $ python -m venv [newenvname]
# 名前はvenvにするのが無難
$ python -m venv venv

# activate
$ source [newenvname]/bin/activate

$ vi requirements.txt
# 右の記載をする

$ pip install -r requirements.txt


```

</div>

<div>

`requirements.txt`

```txt
flask
dronekit
dronekit-sitl
schedule
pyserial
pyulog
pandas
matplotlib
```


</div>


</div>



---

# 全体像



- あとは、localhost:14540 に対して **drone-kit** で接続すればいい
- 機体の操作は drone-kit のリファレンスを参照
- ここの通信は MavLink という特殊なプロトコルで行われているが、これをラッパーしたライブラリは実は Python 製以外も存在する（ex, Golang 製 の Gobot など）

<img border="rounded" src="https://i.gyazo.com/1b47e2446efb42d4416ab68b404159fb.png" class='object-contain object-centor h-80 w-full'>

