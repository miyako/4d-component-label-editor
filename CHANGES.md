2015-03-17
---
複数レベルのリレーションに対応しました。

v14で《ワードラップ無し》が反映されない問題を修正しました。

2015-03-11
---

ショートカット（⌘I, ⌘B, ⌘U）でボールド・イタリック・アンダーライン属性が設定できるようにしました。

テキスト入力中でもOKです。

テキストの境界が細いときの印刷で右側が少し欠ける問題を修正しました。

複数行の《ワードラップ》有無を指定できるようにしました。

Windowsで設定ファイルを書き出すときに拡張子が指定されていなかった問題を是正しました。

2015-03-03
---
テキストやフォーミュラ（フィールドなど）の線はオブジェクトの外縁に描画されるようにしました。太い線が文字にかからないようにするためです。

![](https://github.com/miyako/4d-component-label-editor/blob/master/images/5.png) 

Command+shift+矢印でオブジェクトの幅や高さを調節できます。

テキスト編集中にエディター上部のボタンをクリックしたとき，編集を終了するようにしました。

編集/終了メニューを追加しました。もっとも，テキスト編集以外はメニューバーではなく，透明ボタンのショートカットで処理しています。

クリアボタンをクリックしても，履歴は継続するようにしました。

クリアボタンは表示されているページ（レイアウトまたはラベル）にのみ，適用されます。

複数オブジェクトの「右揃え」が効かない問題を修正しました。

「ラベル毎」「レコード毎」に実行されるメソッドは，コンポーネントと共有されていない場合，一時的に共有属性が付されるようにしました。（インタープリターモードのみ）

手動n対1リレーショがを一時的にSET FIELD RELATIONで自動モードに変されるようにしました。

均等配置コマンドがコンテキストメニューからも適用できるようになりました。

画像やテキストが直接，ペーストできるようになりました。

2015-02-26
---

**New**:```picture $preview := LABEL_Get_document_preview (->blob|text $label)```

* usage:

a. takes a path to a .4LB document, on success, returns its image as picture.

b. takes a BLOB .4LB document, on success, return its image as picture.

c. take a .4LBX as text, on success, return its image as picture.

d. takes a path to a .4LBX document, on success, returns its image as picture.

**New**:```boolean $success := LABEL_Convert_document (->blob|text $label{; boolean $withPrintSettings})``` 

* usage:

a. takes a path to a .4LB document, on success, returns the 4LBX (XML) as text.

b. takes a BLOB .4LB document, on success, return the 4LBX (XML) as BLOB.

optionally you can specify whether to include the print settings structure by setting $withPrintSettings to true. by default,  the information is excluded (it is not very useful and only increases the XML size). not very useful, in the sense that you would probably want to use regular 4D command to control the print settings.

**Modified**: ```LABEL_OPEN_EDITOR (->table{; blob|text $labelIn{; ->blob|text $labelOut}})```

you can now pass a 4LBX (XML) text instead of path. 

optionally you can receive the new .4LBX (XML) if the editor dialog was accepted.

**Modified**: ```LABEL_PRINT_SELECTION```

you can now pass a 4LBX (XML) text instead of path. 

**Fixed**: virtual structure support

**Fixed**: memory leak in ```LABEL_PRINT_SELECTION```

**Fixed**: allowed method name list correctly handle method groups (@)

**Fixed**: corrected some French localisation
