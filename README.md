# 環境設定いろいろ
ゼミの初回にやること


## Python

Anaconda という Python パッケージをインストールする．
* [Setting up Your Python Environment](http://quant-econ.net/py/getting_started.html)

### 自分のコンピュータ

1. www.continuum.io/downloads から自分の OS に合わせて Python 3.6 version (GRAPHICAL INSTALLER あるいは 64-BIT GRAPHICAL INSTALLER) をダウンロードする．
2. ダウンロードされたファイルをダブルクリックし，あとは指示に従う．

### 大学のコンピュータ

デフォルト状態で「ターミナル」で

```
python
```

と打つと Python 3.5 が立ち上がるようになっている．

Python を終了させるには

```
quit()
```

と入力する．

#### 自前環境の作成

大学のコンピュータの Python 環境には管理者権限がないと新しいライブラリが追加できないので，以下のように最小限の環境を自分のホームディレクトリに作る．

「ターミナル」で
```
conda create -n py36 python=3.6
```

と打つ．
`py36` は好きな名前にしてよい．

#### 自前環境の起動

作られた `py36` 環境を activate するにはひと工夫必要．

* [pyenvとanacondaを共存させる時のactivate衝突問題の回避策3種類](http://qiita.com/y__sama/items/f732bb7bec2bff355b69)

ひとつのやり方は

```
source ~/.conda/envs/py36/bin/activate py36
```

(上で違う名前にした人は `py36` の部分を適切に変える．)

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

### アップデート

Anaconda をアップデートするには，「ターミナル」で

```
conda update conda
```

```
conda update anaconda
```

と打つ．

過去に 3.6 未満をインストールしている人は，

```
conda install python=3.6
```

で Python 3.6 にアップデートする．
「conflict が見つかった」と言われたら，当該パッケージを `conda remove` で消していく．
そのあと `conda update conda`, `conda update anaconda` を実行する．  
いつの間にか `anaconda` を消していると，`conda update anaconda` で「anaconda がない」と言われる．
その場合は `conda install anaconda` で `anaconda` を再度インストールする．


## Julia

自分のコンピュータ，大学のコンピュータ共通．

* [Setting up Your Julia Environment](http://quant-econ.net/jl/getting_started.html)

1. [julialang.org/downloads](http://julialang.org/downloads/) の "Julia (command line version)" から自分の OS に合ったものをダウンロードする．
2. ダウンロードされたファイルをダブルクリックし，あとは指示に従う．

### パッケージのインストール

[Setting up Your Julia Environment](http://quant-econ.net/jl/getting_started.html) に従う．

何かうまくいかないことがあったら，`Pkg.rm` でパッケージを remove して再度 add すると解決することもある．
たとえば IJulia を消すには Julia を立ち上げた上で

```
Pkg.rm("IJulia")
```

と入力する．


## GitHub

1. [github.com](https://github.com) でアカウントを作る．
   (誰だか想像できないようなアカウント名のときは，名前を登録する．)
2. [OyamaZemi/exercises2016](https://github.com/OyamaZemi/exercises2016) の "Watch" ボタンを押す．
   ("Watchers" のページがゼミ生アカウント一覧になる．)
3. [QuantEcon.jl](https://github.com/QuantEcon/QuantEcon.jl) を "fork" してみる．

### SourceTree

1. Git の GUI クライアント SourceTree を www.sourcetreeapp.com からダウンロードしてインストールする．
2. SourceTree を立ち上げて，QuantEcon.jl のローカルクローンを作ってみる．  
   リモートレポジトリを設定してみる．
   * [SourceTreeでリモートリポジトリを設定](http://blog.shinji.asia/sourcetree_git/#rem_repo)
