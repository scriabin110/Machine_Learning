# Python環境の構築

## 概要
- 本ドキュメントは、MinicondaでPythonの実行環境を構築し、Jupyter Lab上で"Hello World"を実行できるまでの手順を紹介します。
- 専門用語の説明は省きます。とりあえず、手順を踏めば、"Hello World"が実行できるようになります。気になる人は調べてみてください。

## 対象ユーザー
- 機械学習講座の受講生
- 既にPythonを使える人は本ドキュメントの対象外です。
- Anacondaは使用不可ですので、ご注意ください。

## 確認事項
- ネットワークの繋がる環境で下記の手順を実行してください。

## 手順
### 大きな流れ
- Minicondaのインストール
- パッケージレジストリの変更
- 仮想環境の構築
- Jupyter lab上で"Hello world"の実行の確認
- ライブラリのインストール
### インストール
- [Minicondaのインストーラー](https://docs.conda.io/en/latest/miniconda.html#windows-installers)から、Windows用の`Miniconda3 Windows 64-bit`(Latest version)をインストールする。
- 基本的にNextをクリックして前に進めるが、「Advanced Installation OptionsConda」では「Register Miniforge3 as my default Python 3.10」にチェックする。
- 最後にInstallをクリックする
- インストールが終わったら、Windowsの検索画面でAnacondaと打ち込み、Anaconda Prompt(miniconda3)を開く。
- 以下の手順はAnaconda Prompt(miniconda3)が開けないと出来ません。
#### パッケージレジストリの変更
- 以下のコマンドを一行ずつコピぺして、Enterを押して実行してください。<br>
```conda config --remove channels defaults```<br>
```conda config --add channels conda-forge```<br>
- 以上の操作が正しく実行できたかを確認するため、以下のコマンドをコピペして実行(Enterをクリック)してください。<br>
```conda config --show channels```<br>
以下のようになっていればOKです。
  ```
    channels:
      - conda-forge
  ```
### 仮想環境の構築
- 仮想環境"mlws_env"の構築<br>
```conda create -n mlws_env python=3.9```
- 構築した仮想環境が構築できるかを確認<br>
``` conda info -e```
- 構築した仮想環境に入る<br>
``` conda activate mlws_env```
- "C:"の前の表記に着目すると、(base)から(mlsw_env)に切り替わっていることが確認できる。
- (mlsw_env)に切り替わっていることを確認して以下のコマンドを実行する。<br>途中でYer/Noを聞かれるので、Yを入力してEnterを押して進める。<br>
``` conda install ipykernel ```<br>
```ipython kernel install --user --name mlws_env  ```
- Jupyter labのインストール<br>途中でYer/Noを聞かれるので、Yを入力してEnterを押して進める。<br>
```conda install jupyterlab```
### Jupyter lab上で"Hello World!"を実行する
- mlws_envの仮想環境に入る<br>
``` conda activate mlws_env ```
- "Jupyter lab"と入力して、Enterをクリックする
- Jupyter Labのブラウザが立ち上がる。
- 新規ファイルを作成して、セルに"Hello World"と入力して、実行(shiftを押しながらEnterを押す)する。
- 新規ファイルを作成する際に、mlws_envが選択されていることを確認する。もしくはファイルを作成後に、カーネルをmlws_envに切り替える。
- "Hello World"がOutputされることを確認する。

### 必要なライブラリのインストール
- Anaconda Prompt(miniconda3)を開く。
- mlws_envの仮想環境に入る<br>
``` conda activate mlws_env ```
- 以下のコマンドを実行して、必要なライブラリをインストールする。<br>
```conda install numpy pandas seaborn matplotlib scikit-learn -y```
## あとがき
- "Hello World"が出力されれば、本ドキュメントの目標はクリアです。お疲れ様でした！