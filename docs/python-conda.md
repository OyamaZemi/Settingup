# Python (`conda` を使う方法)

このページでは，自分のコンピュータで `conda` を使って Python 環境を作る方法をまとめる．  
大学のコンピュータで使う場合は，別ページを参照すること．

参考:
- [Setting up Your Python Environment](https://python-programming.quantecon.org/getting_started.html)

## 1. Anaconda Distribution をインストールする

Anaconda Distribution は，Python と `conda`，および主要なパッケージをまとめた配布物である．

1. [Anaconda Distribution の公式ダウンロードページ](https://www.anaconda.com/download) を開く．
2. 自分の OS に合ったインストーラをダウンロードする．
3. ダウンロードしたファイルを開き，案内に従ってインストールする．

インストール後，ターミナルで次を実行し，`conda` が使えることを確認する．

```bash
conda --version

## 2. 環境を作る

`conda` では，作業ごとに環境を分けて使う．
たとえば Python 3.13 の環境を作るには，次を実行する．

```bash
conda create -n py313 python=3.13
```

`py313` は環境名なので，好きな名前にしてよい．

## 3. 環境を有効化する

作成した環境を使うには，次を実行する．

```bash
conda activate py313
```

有効化したあと，次で Python の版を確認できる．

```bash
python --version
```

## 4. ライブラリをインストールする

環境を有効化したあと，必要なライブラリを入れる．
たとえば最小限の科学計算用ライブラリは次のように入れられる．

```bash
conda install numpy scipy matplotlib pandas jupyter
```

必要に応じて，他のライブラリも追加する．

`quantecon` を入れる場合は，次を実行する．

```bash
pip install quantecon
```

## 5. アップデート

`conda` 自体を更新するには，次を実行する．

```bash
conda update conda
```

現在の環境の Python を更新するには，次を実行する．

```bash
conda update python
```

個別のパッケージを更新したい場合は，たとえば次のようにする．

```bash
conda update numpy
```

依存関係の衝突が起きる場合は，既存環境を無理に変更するより，新しい環境を作り直す方が簡単なことが多い．


