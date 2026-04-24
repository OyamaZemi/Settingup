# Jupyter の使い方

## 1. このページの目的

このページでは，Jupyter Notebook / JupyterLab を使って Python を実行する基本的な方法をまとめる．  
VS Code が主にファイル単位でコードを書くためのエディタであるのに対し，Jupyter はコード・実行結果・文章・数式を同じ画面にまとめて扱うためのインターフェースである．

Python 環境の作成方法は，[`venv`による環境構築](python-venv.md)，[Poetry による環境構築](python-poetry.md)，
[`conda`による環境構築](python-conda.md) を参照すること．

## 2. Jupyter とは

Jupyter は，ブラウザ上で Python を実行できるノートブック型の環境である．  
コードをセル単位で実行でき，出力として表・図・グラフなどをその場で確認できる．  
また，Markdown を使って文章や数式を書くこともできるため，分析内容や計算過程をまとめる用途にも向いている．

Jupyter は，次のような作業に向いている．

- Python を試しながら学ぶ
- 短いコードを実験する
- データ分析の結果を確認する
- 数式や説明文と一緒に計算結果をまとめる

一方で，大きなプログラムを複数ファイルで開発する場合は，VS Code の方が扱いやすいことが多い．

## 3. Jupyter をインストールする

Jupyter を使うには，利用している Python 環境に Jupyter をインストールする．  
インストール方法は，環境管理の方法によって異なる．

### `venv` を使う場合

仮想環境を有効化してからインストールする．

macOS / Linux:

```bash
source .venv/bin/activate
python3 -m pip install jupyterlab notebook
```

Windows:

```powershell
.venv\Scripts\Activate.ps1
py -m pip install jupyterlab notebook
```

### Poetry を使う場合

Poetry 管理下のプロジェクトでは，次のように追加する．

```bash
poetry add jupyterlab notebook
```

### `conda` を使う場合

Anaconda Distribution をインストールした場合，通常は JupyterLab と Jupyter Notebook
が最初から含まれているため以下の操作は必要ない．次節に進んでできなかったら戻ってくれば良い．

`conda` 環境を有効化してからインストールする．

```bash
conda activate py313
conda install jupyterlab notebook
```

## 4. Jupyter を起動する

JupyterLab を起動するには，ターミナルで次を実行する．

```bash
jupyter lab
```

従来の Jupyter Notebook を起動するには，次を実行する．

```bash
jupyter notebook
```

ただし、Poetry を使っている場合には`poetry run` を手前につける。

起動すると，通常はブラウザが開く．
ブラウザが自動で開かない場合は，ターミナルに表示された `http://localhost:8888/...` のような URL をブラウザに貼り付ける．

Jupyter を終了するには，起動したターミナルで `Ctrl + C` を押す．

## 5. Notebook を作成する

JupyterLab または Jupyter Notebook を開いたら，新しい notebook を作成する．

1. 画面上で **Python 3** などの kernel を選ぶ
2. 新しい `.ipynb` ファイルを作る
3. セルに Python コードを書く
4. セルを実行する

Notebook ファイルの拡張子は `.ipynb` である．

## 6. セルを実行する

Jupyter では，コードをセル単位で実行する．
セルに Python コードを書き，`Shift + Enter` を押すとそのセルが実行される．

例:

```python
print("Hello, world!")
```

実行すると，セルの下に

```text
Hello, world!
```

と表示される．

## 7. Edit mode と Command mode

Jupyter Notebook には，主に二つのモードがある．

### Edit mode

セルの中身を編集するモードである．
セル内にカーソルが表示され，文字を入力できる．

### Command mode

セル全体を操作するモードである．
セルの追加・削除・移動などを行うときに使う．

よく使う切り替えは次の通りである．

* `Enter`: Command mode から Edit mode に入る
* `Esc`: Edit mode から Command mode に戻る
* `Shift + Enter`: セルを実行する

Command mode では，たとえば `b` を押すと下に新しいセルを追加できる．

## 8. Markdown セルを使う

Jupyter では，コードだけでなく文章も書ける．
セルの種類を Markdown に変更すると，説明文や数式を書ける．

たとえば，Markdown セルに次のように書ける．

```markdown
# 見出し

これは説明文である．

数式も書ける：

$$
y = ax + b
$$
```

Markdown セルも `Shift + Enter` で表示結果を確認できる．

## 9. 補完とヘルプ

Jupyter では，Tab キーを使って補完ができる．
たとえば，次のように入力して Tab を押すと，候補が表示される．

```python
import numpy as np
np.random.
```

また，関数名の後ろに `?` を付けて実行すると，簡単なヘルプを確認できる．

```python
np.random.randn?
```

## 10. パッケージをインストールする

Jupyter 上で使いたいパッケージは，原則として **Jupyter を起動している Python 環境** にインストールする必要がある．
ターミナルでインストールする方が分かりやすい．

`venv` の場合:

```bash
python3 -m pip install numpy matplotlib pandas
```

Poetry の場合:

```bash
poetry add numpy matplotlib pandas
```

`conda` の場合:

```bash
conda install numpy matplotlib pandas
```

Notebook 内からインストールすることもできるが，どの環境に入っているかが分かりにくくなることがあるため，最初はターミナルで行う方がよい．

## 11. `.py` ファイルとの違い

Jupyter Notebook は `.ipynb` という形式で保存される．
一方，通常の Python ファイルは `.py` という拡張子を持つテキストファイルである．

* `.ipynb`: セル単位で実行し，説明文や出力も一緒に保存できる
* `.py`: 通常の Python スクリプトとして，ファイル全体を実行する

学習や分析の試行錯誤には `.ipynb` が便利である．
一方，長いプログラムや再利用するコードは `.py` ファイルに分ける方がよい．

## 12. VS Code との関係

VS Code でも Jupyter Notebook を開くことができる．
その場合は，VS Code に Jupyter 拡張機能を入れておく．

ただし，Jupyter を単独で使う場合は，ブラウザ上で `jupyter lab` または `jupyter notebook` を起動して作業すればよい．

Jupyter と VS Code の使い分けは，おおよそ次のように考える．

* Jupyter: 学習，実験，データ分析，結果の整理
* VS Code: 複数ファイルの開発，長いコードの編集，Git との連携

## 13. QuantEcon Lectures

[QuantEcon Lectures](https://quantecon.org/lectures/) の各ノートは，
右上の`Download Notebook`のボタンを押すことで，`.ipynb`をダウンロードできる．
Jupyter を起動してそのファイルを開くことで，レクチャーのコードを実行・編集できる．
