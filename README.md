# 環境設定いろいろ
ゼミの初回にやること(2019 ver)

## はじめに

* [ターミナルの基本的な使い方](http://hwb.ecc.u-tokyo.ac.jp/current/information/cui/terminal/)

### Mac ユーザ

Mac 所有者は「コマンドライン・ツール」をインストールしておく．

「ターミナル」を開いて

```
xcode-select --install
```

と打つ (すでにインストールしている人は "command line tools are already installed" と出るはず)．
出てきたウィンドウにしたがって「コマンドライン・ツール」をインストールする．
すぐには終わらないので先に進んでおく．


## Python

Anaconda という Python パッケージをインストールする．
* [Setting up Your Python Environment](http://quant-econ.net/py/getting_started.html)

### 自分のコンピュータ

1. www.anaconda.com/download から自分の OS に合わせて Python 3.7 version をダウンロードする．
2. ダウンロードされたファイルをダブルクリックし，あとは指示に従う．

### 大学のコンピュータ

デフォルト状態で「ターミナル」で

```
python
```

と打つと Python 3.6.1 が立ち上がるようになっている．

Python を終了させるには

```
quit()
```

と入力する．

#### 自前環境の作成

大学のコンピュータの Python 環境には管理者権限がないと新しいライブラリが追加できないので，以下のように最小限の環境を自分のホームディレクトリに作る．

「ターミナル」で
```
conda create -n py37 python=3.7
```

と打つ．
`py37` は好きな名前にしてよい．

#### 自前環境の起動

作られた `py37` 環境を activate するにはひと工夫必要．

* [pyenvとanacondaを共存させる時のactivate衝突問題の回避策3種類](http://qiita.com/y__sama/items/f732bb7bec2bff355b69)

ひとつのやり方は

```
source activate py37
```

(上で違う名前にした人は `py37` の部分を適切に変える．)
(先述のリンクでは`conda activate`が使えるようになったと書いてあるが,大学のコンピュータでは使えなかったので`source activate`でよい.)

このあと `python` と打つと自前の python 環境が立ち上がる (毎回 activate する必要がある)．

#### 自前環境へのライブラリのインストール

Activate させたあと最低限のライブラリをインストールする：

```
conda install numpy scipy jupyter matplotlib numba pandas statsmodels sympy sphinx numpydoc requests nose
```

### ライブラリを追加する

`quantecon` ライブラリをインストールしてみる (`conda` には登録されていないので `pip` を使う)．  
「ターミナル」で

```
pip install quantecon
```

と打つ．  
(すでにインストールしていて，アップデートするときは

```
pip install quantecon -U
```

と `-U` オプションを加える．)

### アップデート (自分のコンピュータのみ)

Anaconda をアップデートするには，「ターミナル」で

```
conda update conda
```

```
conda update anaconda
```

と打つ．

過去に 3.7 未満をインストールしている人は，

```
conda install python=3.7
```

で Python 3.7 にアップデートする．
「conflict が見つかった」と言われたら，当該パッケージを `conda remove` で消していく．
そのあと `conda update conda`, `conda update anaconda` を実行する．  
いつの間にか `anaconda` を消していると，`conda update anaconda` で「anaconda がない」と言われる．
その場合は `conda install anaconda` で `anaconda` を再度インストールする．


## Julia

自分のコンピュータ，大学のコンピュータ共通．

* [Setting up Your Julia Environment](http://quant-econ.net/jl/getting_started.html)

1. [julialang.org/downloads](http://julialang.org/downloads/) の "Julia (command line version)" から自分の OS に合ったものをダウンロードする．
2. ダウンロードされたファイルをダブルクリックし，あとは指示に従う．

* [Julia 0.7と1.0の関係](https://qiita.com/bicycle1885/items/9f9297d34d5f2ad56358)

### パッケージのインストール

[Setting up Your Julia Environment](http://quant-econ.net/jl/getting_started.html) に従う．

何かうまくいかないことがあったら，`Pkg.rm` でパッケージを remove して再度 add すると解決することもある．
たとえば IJulia を消すには Julia を立ち上げた上で

```
Pkg.rm("IJulia")
```

と入力する．

### パッケージのアップデート

パッケージたちをアップデートするには (Julia を立ち上げた上で)

```
Pkg.update()
```

と入力する．
毎回ゼミの前に実行しておくようにするとよい．

### Jupyter Notebook

Jupyter notebook を開いたときに Julia の最新版が反映されない場合は (Julia を立ち上げた上で)

```
Pkg.build("IJulia")
```

と入力して `IJulia` をビルドし直す．


## GitHub

1. [github.com](https://github.com) でアカウントを作る．
   (誰だか想像できないようなアカウント名のときは，名前を登録する．)
2. [QuantEcon.py](https://github.com/QuantEcon/QuantEcon.py) を "fork" してみる．

### SourceTree

1. Git の GUI クライアント SourceTree を www.sourcetreeapp.com からダウンロードしてインストールする．
2. SourceTree を立ち上げて，QuantEcon.py のローカルクローンを作ってみる．  
   リモートレポジトリを設定してみる．
   * [SourceTreeでリモートリポジトリを設定](http://blog.shinji.asia/sourcetree_git/#rem_repo)
