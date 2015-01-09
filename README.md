# 4d-component-label-editor

About
-----
4D v13/v14用のラベルエディター・コンポーネントです。

![](https://github.com/miyako/4d-component-label-editor/blob/master/images/1.png)

**特徴**

* 従来のラベル定義ファイル（拡張子4LB）を取り込むことができます。
* 取り消し・やり直し・オブジェクトのコピー＆ペーストができます。
* マルチスタイルフィールドをサポートしています。
* 文字列をバーコードとして出力することができます。（CODE39など）
* ピクチャの拡大・縮小・アスペクト比保持・アルファチャンネルをサポートしています。
* ピクチャをデスクトップからドラッグ＆ドロップすることができます。

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
