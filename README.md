# ps_tv_whitelist_bat

Vita TVのホワイトリスト化(ゲームの起動制限解除)をほぼ自動で行うバッチファイルです。  
該当フォルダをドラッグ&ドロップし、指示に従うだけで処理が完了します。


## メリット(従来の方法との比較含む)
- 必要なツールを同梱済みのため、ほぼ自動で処理が完了します。
- 従来のホワイトリスト化の方法では**ゲームの更新やDLCが適用できない問題がありましたが、このバッチファイルではその点が解消されています。**
- 本体内蔵メモリーの内容だけをバックアップ・リストアするため、所要時間・必要サイズが最少ですみます。
- Vita TVを改造することなく利用可能です(最新のシステムソフトウェアでも動作します)。

## ホワイトリスト化の際の流れ
1. Vita TVのバックアップイメージを作成
2. 作成したバックアップイメージを展開
3. app.dbにホワイトリスト化処理を実施
4. バックアップイメージを再パック
5. 再パックしたバックアップイメージをVita TVにリストア

このバッチファイルでは上記の2.～4.を自動化します。

## ホワイトリスト化導入方法
これを実行する前に、一通り手順に目を通してください。また下記のQ&Aも事前に確認をお願いします。
1. 処理時間および容量削減のため、Vita TVの電源を切り**メモリーカードとゲームカートリッジを取り外します(重要)**。
2. Vita TVの電源を入れVita TVのトロフィーアプリを起動し、トロフィー情報をPSNと同期します。
3. PCに最新の[コンテンツ管理アシスタント](http://cma.dl.playstation.net/cma/win/jp/)をインストールし、起動します。
4. Vita TVの「コンテンツ管理」を起動し、PCと接続します。
5. 「バックアップユーティリティー」から「バックアップ」を選択し、名称は変更せずバックアップを実行します。  
NOTE: バックアップしたファイルはデフォルトでは `C:\Users\[ユーザー名]\Documents\PS Vita\SYSTEM\[16桁のID]\[作成日時作成時間]-01`フォルダに作成されます。  
例: `C:\Users\USER_NAME\Documents\PS Vita\SYSTEM\01234567ABCDEF\201912312359-01`  
6. [自動化バッチファイル](https://github.com/1jtp8sobiu/ps_tv_whitelist_bat/archive/master.zip)をダウンロードし、PCの任意の場所に展開します。
7. ステップ5.で作成された`[作成日時作成時間]-01` フォルダを展開した`Drag_and_Drop_Here.bat`にドラッグ&ドロップします。  
![](https://github.com/1jtp8sobiu/ps_tv_whitelist_bat/raw/master/img/25a2e475e4d5edcd602e242dbca8fd9e.png)
8. バッチファイルの指示に従いホワイトリスト化処理を完了します。
9. Vita TVの「コンテンツ管理」を起動し、「バックアップユーティリティー」から「リストア(復元)」を選択します。  
**NOTE: リストアする前に、メモリーカードが取り外されている事を必ず確認してください。メモリーカードが挿し込まれた状態で復元すると、内容が削除されてしまいます。**  
10. `999999999999-99`と言う名称のバックアップファイルを復元します。
11. リストア完了後、`999999999999-99`のバックアップファイルを削除し、Vita TVを再起動します。
12. **メモリーカードを挿し込み**データベースの更新完了後、目的のゲームが起動するか確認します。


## Q&A

- **ホワイトリスト化を実行する上で注意することはありますか？**  
Vita TV上でバックアップを作成する前にトロフィー情報をPSNと同期することをお勧めします(リストア時に、未同期のトロフィー情報は削除されるため)。  
また、リストアを実行するとPSNやPS Store接続時にパスワードの再入力が一度だけ必要になります(リストア時の仕様です)。  
もしパスワードを忘れている場合は事前に確認をお願いします。  
- **ホワイトリスト化を実行することでPSNアカウントや本体のBANの可能性はありますか？**  
データベースに簡易なトリガーを挿入しているだけの為、その心配はありません。  
- **必要なランタイムがダウンロードできず「コンテンツ管理アシスタント」のインストールができません**  
CMASetup.exeのプロパティ -> 互換性 -> 互換モード から "Windows XP Service Pack 3" を選択するとインストールできる場合があります。
- **バッチファイルを実行しましたが処理が始まりません。**  
バッチファイル実行時にアンチウイルスやWindows 10のスマートスクリーンの保護機能が動作する可能性があります。  
スマートスクリーンの保護画面は表示された場合は「詳細情報」をクリックして実行を選択してください。  
- **リストア時にメモリーカードと本体メモリーの内容が削除されると警告されますが問題ありませんか？**  
メモリーカードが取り外されている状態であれば問題ありません(セーブデータ等は基本的にメモリカード側に保存されているため)。  
本体メモリーに関しても、バックアップ時のファイルをそのままリストアするため、データを失う事はありません。  
- **リストアが完了しましたが、インストール済みのダウンロード版のゲームが起動できません。**  
メモリーカードを差し込みVita TVを起動するとデータベースが更新されゲームが起動可能になります。  
または、PS Storeから該当ゲームを再度ダウンロードすると起動可能になります。(セーブデータは保持されます。)  
- **システムソフトウェアを更新するとホワイトリスト化は解除されますか？**  
システムソフトウェアの更新後も維持されます。メモリーカードの入れ替え等でも維持されます。  
ホワイトリスト化が解除されるのは以下の場合です。  
 1. 本体設定を初期化した時(メモリーカードの初期化は問題なし)
 2. セーフモードから「データベースの再構築」を実行した時  
- **従来のホワイトリスト化を導入済みですが、このバッチファイルを利用する場合はどうすればいいですか？**  
まずセーフモードから「データベースの再構築」を実行し、従来のホワイトリストを解除した後、このバッチファイルの手順に従ってください。

## テスト環境
- Vita TV システムソフトウェア 3.73
- Windows 10 x64 Version 1903 
- コンテンツ管理アシスタント Version 3.56.7933.1204

## 同梱済みツール
psvimgtools v0.1 (psvimgtools-0.1-win32.zip)  
https://github.com/yifanlu/psvimgtools/releases/tag/v0.1  
SQLite (sqlite-tools-win32-x86-3300100.zip)  
https://www.sqlite.org/download.html

## 参考にしたページ
vitaTVの起動制限を解除する方法  
http://hp.vector.co.jp/authors/VA041465/How%20to%20install%20the%20PSTV%20Whitelist%20Patch.htm  
How to install the PSTV Whitelist Patch (v2)  
https://hackinformer.com/PlayStationGuide/PSV/tutorials/how_to_install_the_pstv_whitelist_patch_v2.html

## Credits
- Thanks to SilicaAndPina for his research for whitelist hack.
- Thanks to yifanlu for psvimgtools.
- Thanks to Davee and Proxima for http://cma.henkaku.xyz/.
