# Shachi-lab Greaseweazle V4.1 plus Board

しゃちらぼで作成した、Greaseweazle V4.1 ベースの互換基板のKiCad設計データです。

この基板は、Greaseweazle V4.1を基にしつつ、5.25インチFDDやPC-98系FDDで扱いやすくするために、ほんの少しだけ変更を加えています。

そのため、このリポジトリでは便宜的に **V4.1 Plus** と呼んでいます。  
ただし、**これは公式のGreaseweazleの名称ではありません。**

<a href="./images/gw-v41-plus_1.jpg">
<img src="./images/gw-v41-plus_1.jpg" alt="Shachi-lab Greaseweazle V4.1 plus Board" width=400 style="max-width:100%; height:auto;"></a>

---

## Greaseweazle について

Greaseweazle は、PC用FDDをUSB経由で制御し、フロッピーディスクの読み書きを行うためのオープンソースプロジェクトです。

一般的なUSB接続FDDとは違い、Greaseweazleではフロッピーディスクをより低いレベルで扱うことができます。  
磁気記録のフラックス変化を読み書きできるため、通常のUSB FDDでは扱えない形式のディスクにも対応できる可能性があります。

詳細な使い方、ファームウェアの書き込み方法、ホストツールについては、元のGreaseweazleドキュメントを参照してください。

* Original Greaseweazle project  
  https://github.com/keirf/greaseweazle

* Greaseweazle Wiki  
  https://github.com/keirf/greaseweazle/wiki

---

## このリポジトリについて

このリポジトリでは、しゃちらぼで作成したGreaseweazle互換基板のKiCad設計データを公開しています。

この基板は、Greaseweazle V4.1 を基にしたクローン基板です。  
回路的にはGreaseweazle V4.1に近い構成で、基板外形、ホール、コネクタ、ピンヘッダ、LEDなどの位置は、できるだけ元のV4.1基板に合わせています。

一方で、実装しやすくすることと、5.25インチFDDやPC-98系FDDで扱いやすくすることを目的に、一部を変更しています。

---

## KiCad version

この基板データは **KiCad 10.0** で作成しています。

KiCadの古いバージョンでは、正しく開けない可能性があります。

---

## 元のV4.1基板との主な違い

* 2層基板にしています
  * 元のGreaseweazle V4.1は4層基板です
* SMT部品は、基本的に0603(1608)サイズを使用しています
  * 元の基板では0402(1005)サイズが使われています
  * 手実装しやすくするための変更です
* PC-98のFDD用に、信号を切るためのピンヘッダを追加しています
* 5.25インチFDDの+12V用に、一般的なACアダプタからBergコネクタへ出力できるようにしています

---

## 確認状況

現時点では、3.5インチFDDを接続して、DOS/Windows系の1.44MB FDを読み込めることを確認しています。

確認済みの内容は以下です。

* Greaseweazle Firmware 1.6 の書き込み
* Windows 11 でのUSB接続
* `gw info` による認識確認
* 3.5インチFDDの接続
* DOS/Windows系 1.44MB FD の読み込み
* `ibm.1440` プロファイルでのIMGファイル作成
* 7-ZipでIMGファイルの中身を確認

確認に使用したFDDは `SONY MPF920` です。

<a href="./images/gw-v41-plus_2.jpg">
<img src="./images/gw-v41-plus_2.jpg" alt="Shachi-lab Greaseweazle V4.1 plus Board" width=400 style="max-width:100%; height:auto;"></a>

---

## 未確認の内容

以下は、まだ確認中です。

* PC-98用 5.25インチFDの読み込み
* 5.25インチFDDでの安定動作
* 300rpm / 360rpm まわりの動作
* DENS信号まわりの確認
* さまざまなFDDでの互換性

---

## ファームウェアと使い方

ファームウェア、ホストツール、使い方は、元のGreaseweazleドキュメントに準じます。  
このリポジトリには、ファームウェアやホストツールは含めていません。

この基板では、AT32F4用のHEXファイルを使用しました。

例：

```text
greaseweazle-firmware-at32f4-1.6.hex
```

手元の環境では、`gw info` で以下のように認識されました。

```text
Host Tools: 1.23
Device:
  Port:     COM7
  Model:    Greaseweazle V4.1
  MCU:      AT32F403A, 216MHz, 224kB SRAM
  Firmware: 1.6
  Serial:   GW053C11222847000007E0A413
  USB:      Full Speed (12 Mbit/s), 128kB Buffer
```

ここで表示される `Greaseweazle V4.1` は、書き込んだGreaseweazle Firmware側が返しているモデル名です。  
この基板そのものが公式のGreaseweazle V4.1基板という意味ではありません。

---

## 注意

この基板は、しゃちらぼで作成した自作のGreaseweazle互換基板です。  
公式のGreaseweazle製品ではありません。

基板を作成する場合は、KiCadデータや回路を確認したうえで、自己責任でお願いします。  

また、FDDや古いFDメディアは状態に個体差があります。  
傷や汚れのあるFDを使用すると、FDD側の読み取りが不安定になる場合があります。

---

## 関連記事

しゃちらぼブログのGreaseweazle関連記事は、以下のカテゴリにまとめています。

- Greaseweazle - しゃちらぼブログ  
  https://blog.shachi-lab.com/category/microcontroller/greaseweazle/

---

## License

このリポジトリは、元のGreaseweazleプロジェクトに合わせて **Unlicense** で公開します。

この基板は、Keir Fraser 氏によるGreaseweazleプロジェクトを基にした互換基板です。  
ライセンス本文は `LICENSE` ファイルを参照してください。

- Original Greaseweazle project  
  https://github.com/keirf/greaseweazle

- Unlicense  
  https://unlicense.org/
