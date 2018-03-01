# 4d-component-label-editor

About
-----
4D v~~13/v14~~ v16用のラベルエディター・コンポーネントです。

![](https://github.com/miyako/4d-component-label-editor/blob/master/images/3.png)

**特徴**

* 従来のラベル定義ファイル（拡張子4LB）を取り込むことができます。
* ドラッグ＆ドロップでファイルを開くことができます。
* 取り消し・やり直し・オブジェクトのコピー＆ペーストができます。
* マルチスタイルフィールドをサポートしています。
* 文字列をバーコードとして出力することができます。（CODE39など）
* ピクチャの拡大・縮小・アスペクト比保持・アルファチャンネルをサポートしています。
* ピクチャをデスクトップからドラッグ＆ドロップすることができます。

**修正**

* 64ビット版のDOM参照を判別するようにしました。

``Editor_SELECT_Clear``  

```
  //If ($selectObject#"0000000000000000")
If (Match regex("(?:0{16}){1,2}";$selectObject))
```

* サーバー側でフィールドリストを構築するようにしました。
* ``GET ALLOWED METHODS``が0件のときはポップアップを``disable``するようにしました。
* 再帰的にリレートテーブルを追求しないようにしました。

**追加**

* QRコードが出力できるようになりました。
* パレットで選択したフォントがリアルタイムで反映されるようになりました。
* 定型ラベルが選択できるようになりました。（KOKUYO，HISAGO）
* フォーミューラー（fx）オブジェクトを作成できるようになりました。
* ダブルクリックでもテキストが編集できるようになりました。

Install
-------
Componentsフォルダーに置くだけです。

定義ファイルのパスを省略した場合，空のエディターが表示されます。

```
ALL RECORDS([Person])

If (True)
 LABEL_OPEN_EDITOR (->[Person])
Else 
 LABEL_OPEN_EDITOR (->[Person];Get 4D folder(Current resources folder)+"sample.4lb")
End if 
```

* レイアウトページ

![](https://github.com/miyako/4d-component-label-editor/blob/master/images/4.png) 

ラベルのサイズ・用紙・レイアウトなどを決めることができます。

* 行数・列数・開始・枚数は，上下矢印キーでも値を増減することができます。
* 開始位置はマウスで指定することもできます。

**注記**: 従来のエディターと同じように，数値は内部的にポイント単位で処理されていますが，従来のエディターとは違い，整数に丸めることはしないので，正確に位置を指定（たとえばミリ単位）することができます。また，ラベル専用紙の特性を考慮し，マージンはすべて0として出力します。

* メソッド名・実行タイミングの扱いは，従来のエディターと同様です。なお，印刷は別プロセスにセレクションを転送して実行します。なお，レコードロード毎にRELATE ONEが実行されます。

* ラベルページ

ラベルのデザインを決めることができます。

* ファイル（4LBまたは4LBX）を直接，エディターにドロップすることにより，ラベル定義を開くことができます。

* フィールド名は，SET FIELD TITLESで定義した名前（ダイナミックストラクチャ）が表示され，同コマンドで許可したものだけが列挙されます。リレーションが設定されている『1テーブル』のフィールドも表示されます。

* フィールドはドラッグ＆ドロップで追加することができます。フィールドの上にドロップした場合，『+』記号で連結されます。Shiftキーを押しながらドロップした場合，フィールドは改行コードを挟んで縦に連結されます。縦に連結したフィールドは，行の内容が空の場合，繰り上げて印刷されます。

* Commandキーを押しながらクリックすることにより，フィールド名や連結の仕方を編集することができます。ここには，SET ALLOWED METHODSやデータベース設定で許可されている一般的なフォーミュラーが入力できます。また，文字・日付・数値・時間は，そのまま入力することができます。文字型に変換する必要はありません。

* ピクチャは，デスクトップからドラッグ＆ドロップすることができます。エディター表示中は，一時ファイルが作成され，同じ画像は，ファイルを共有します。ラベル定義を書き出すときに，そのような画像はBASE64形式で文書と一緒に保存されます。なお，ラベル定義ファイル（拡張子4LBX）は，XML形式です。

* オブジェクトは，Command+Dで複製することができます。また，Shift+矢印キーでステップ移動することができます。その他，代表的な操作は，ツールボタンまたはコンテキストメニューから実行することができます。

* フォームを選択することができませんが，フォームを参照しているラベル定義ファイル（4LBまたは4LBX）を開くことはできます。v13では，プロジェクトフォーム，v14では，テーブルのフォームを使用します。

* 定型ラベルの設定ファイルは，Resourcesフォルダー内のlocalized.xmlでカスタマイズすることができます。書式は4D本体のものと同じです。
