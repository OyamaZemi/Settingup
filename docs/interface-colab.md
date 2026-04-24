# Google Colab の使い方

## 1. このページの目的

このページでは，Google Colab を使ってブラウザ上で Python を実行する方法をまとめる．

Google Colab は，ローカルに Python 環境を作らなくても使えるノートブック型の実行環境である．
ただし，コードは自分のPCではなく，基本的には Google 側のランタイム上で実行される．
そのため，ローカルの `venv`，Poetry，`conda` 環境をそのまま使うわけではない．

## 2. Google Colab とは

Google Colab は，ブラウザ上で Jupyter Notebook 形式のファイルを作成・実行できるサービスである．
Python コードをセル単位で実行でき，出力として表・図・グラフなどをその場で確認できる．
Markdown を使って文章や数式を書くこともできる．

Colab は次のような場合に便利である．

- ローカル環境を作らずに Python を試したい
- 短いコードをすぐに実行したい
- Notebook を共有したい
- Google Drive 上のファイルを使いたい
- GPU や TPU を使った計算を試したい

一方で，ローカル環境の代わりとして完全に同じように使えるわけではない．
ランタイムは一時的な実行環境なので，必要なパッケージやファイルは適宜準備し直す必要がある．

## 3. Notebook を作成する

Colab を使い始めるには，次の手順を行う．

1. ブラウザで Google Colab を開く
2. Google アカウントでログインする
3. 新しい Notebook を作成する
4. コードセルに Python コードを書く
5. セルを実行する

Notebook ファイルの拡張子は `.ipynb` である．
これは Jupyter Notebook と同じ形式である．

## 4. セルを実行する

Colab では，コードをセル単位で実行する．
コードセルに Python コードを書き，左側の実行ボタンを押すか，`Shift + Enter` を押すとセルが実行される．

例:

```python
print("Hello, world!")
```

実行すると，セルの下に次のように表示される．

```text
Hello, world!
```

## 5. セルを追加する

Colab では，コードセルとテキストセルを追加できる．

* `+ Code`: Python コードを書くセルを追加する
* `+ Text`: Markdown で文章を書くセルを追加する

テキストセルでは，説明文や数式を書くことができる．

例:

```markdown
# 見出し

これは説明文である．

数式も書ける：

$$
y = ax + b
$$
```

## 6. パッケージをインストールする

Colab のランタイムには，よく使われるパッケージが最初から入っていることがある．
ただし，必要なパッケージが入っていない場合は，Notebook のセル内で `pip` を使ってインストールできる．

例:

```python
!pip install quantecon
```

`!` を付けると，Python コードではなくシェルコマンドとして実行される．

ただし，Colab のランタイムは一時的な実行環境である．
ランタイムが切断されたりリセットされたりすると，追加でインストールしたパッケージは消えることがある．
毎回必要なパッケージは，Notebook の最初の方にインストール用セルをまとめておくとよい．

例:

```python
!pip install quantecon
!pip install interpolation
```

## 7. ファイルを扱う

Colab 上で作成した一時ファイルは，ランタイムが終了すると消えることがある．
保存しておきたいファイルは，Google Drive に置くか，ローカルにダウンロードする．

左側のファイルアイコンから，ファイルをアップロードしたり，作成されたファイルを確認したりできる．

## 8. Google Drive を使う

Google Drive のファイルを Colab から使いたい場合は，Drive をマウントする．
Notebook のセルで次を実行する．

```python
from google.colab import drive
drive.mount('/content/drive')
```

実行すると，Google アカウントへのアクセス許可が求められる．
許可すると，Google Drive のファイルを Colab から読み書きできるようになる．

Drive 内のファイルは，通常次のようなパスから参照できる．

```text
/content/drive/MyDrive/
```

## 9. ローカル環境との違い

Colab は，ローカルの Python 環境とは別物である．

たとえば，ローカルで `venv`，Poetry，`conda` を使っていても，Colab の通常のランタイムはそれらの環境を直接使わない．
そのため，ローカルで入れたパッケージを Colab で使いたい場合は，Colab 側でもインストールする必要がある．

また，Colab のランタイムは一時的であり，永続的な作業場所ではない．
Notebook 自体は保存されても，ランタイム内の一時ファイルや追加インストールしたパッケージは残らない場合がある．

## 10. Jupyter / VS Code との使い分け

Jupyter，Colab，VS Code は，どれも Python を実行できるが，役割が少し異なる．

* Colab: ローカル環境を作らず，ブラウザだけですぐに実行したい場合に便利
* Jupyter: 自分のPC上の Python 環境で Notebook を使いたい場合に便利
* VS Code: 複数ファイルの開発や Git と組み合わせた作業に便利

学習や短い実験には Colab が使いやすい．
一方で，長期的なプロジェクトや再現性を重視する作業では，ローカル環境を整えて VS Code や Jupyter を使う方が管理しやすい．

## GPUを利用する

Google Colab を使うことで簡単にGPUを利用した処理を行える．
詳しくは [Quantitative Economics with JAX](https://jax.quantecon.org/intro.html) を参照のこと．
この一連の QuantEcon Lectures は JAX を利用した経済分析の講義を提供している．
