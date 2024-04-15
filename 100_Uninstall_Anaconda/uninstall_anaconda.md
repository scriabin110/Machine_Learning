# Anacondaのアンインストール
## 概要
- 本ドキュメントには、既存の環境の保存、再構築方法とAnacondaをアンインストールするためのサイトのURLを記載する。
## 対象のユーザー
- Anacondaで作成した仮想環境の保存と再構築したい人
- Anacondaをアンインストールしたい人
- 従業員数が200人以上の企業では、営利・非営利目的によらず、有償版の購入が必要である。そのため、有償版の購入予定が無ければ、Anacondaをアンインストールする必要がある。

## 仮想環境の保存と再構築
### 参考にした記事
- [Anacondaを使った仮想環境を保存・再構築、複製](https://qiita.com/ozaki_physics/items/13466d6d1954a0afeb3b)
### ymlファイルに出力して保存
- 保存したい仮想環境に入る。`conda activate <OWN_ENV>`で入れます。その後、以下のコマンドを実行する。FILE_NAMEは仮想環境名にすると再構築が分かりやすい。 <br>
```conda env export > FILE_NAME.yml```
### 再構築
- ymlファイルを保存したディレクトリで以下のコマンドを実行する。<br>
``` conda env create -n NEW_ENV -f FILE_NAME.yml ```
## オススメの記事
- [Windows10でAnacondaをアンインストールする方法](https://utakataworks.com/windows10-anaconda-uninstall/)

## あとがき
- 以上で、Anacondaはアンインストールされました。お疲れ様でした！