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
#### 1. mlws_env (『機械学習講座』全般用 )
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
  - 必要なライブラリをインストールする<br>
  ```conda install numpy pandas seaborn matplotlib scikit-learn -y```
  - 仮想環境"mlws_env"から抜ける<br>
  ```conda deactivate```<br>

#### 2. pycaret_env (AutoML用)
機械学習を楽チン実装できるPyCaretを使うための環境構築も行います。<br>
  - 仮想環境"pycaret_env"の構築 (mlws_envとバージョンが異なることに注意して下さい) <br>
    ```conda create -n pycaret_env python=3.8```
  - 構築した仮想環境に入る。<br>
    ```conda activate pycaret_env```
  - (pycaret_env)に切り替わっていることを確認して、以下を実行<br>
    内容は"mlws_env"と同じ。<br>
    ```conda install ipykernel ```<br>
    ```ipython kernel install --user --name pycaret_env  ```<br>
    ```conda install jupyterlab```<br>
  - **PyCaretをインストール**<br>
    ```pip install pycaret```<br>

### Jupyter labが動くかを確認
#### 1. mlws_env用
- miniconda3から "mlws_env"の仮想環境に入って、Jupyter Labを起動する<br>
```conda activate mlws_env ```<br>
```jupyter lab```
- Jupyter Labのブラウザが立ち上がる。
- 新規Notebookファイルを作成。以下のいずれかを行い、仮想環境をmlws_envに設定。
  1. ファイル作成の際に Notebook > "mlws_env" をクリック
  2. ファイルを作成後に、右上のカーネルをmlws_envに切り替える。
- セルに以下を入力して、実行(shift + Enter)する。<br>
  ```"Hello World"```
- "Hello World"がOutputされることを確認する。
- 左上の"File"タブ > "Shut Down" でJupyterLabを終了。

#### 2. pycaret_env用
- 仮想環境"pycaret_env"からJupyter Labを起動する<br>
```conda activate pycaret_env ```<br>
```jupyter lab```
- 仮想環境が"pycaret_env"となっていることを確認 (先ほどと同様)
- セルで以下を実行し、エラーとならないことを確認。<br>
```import pycaret```

## あとがき
- "Hello World"が出力されれば、本ドキュメントの目標はクリアです。お疲れ様でした！

