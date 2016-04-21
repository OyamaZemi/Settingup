# 環境設定いろいろ
ゼミの初回にやること


## Python

Anaconda という Python パッケージをインストールする．
* [Setting up Your Python Environment](http://quant-econ.net/py/getting_started.html)

### 自分のコンピュータ

1. www.continuum.io/downloads から自分の OS に合わせて PYTHON 3.5 (64-BIT GRAPHICAL INSTALLER) をダウンロードする．
2. ダウンロードされたファイルをダブルクリックし，あとは指示に従う．

### 大学のコンピュータ

大学のコンピュータの Python 環境には管理者権限がないと新しいライブラリが追加できないので，以下のように最小限の環境を自分のホームディレクトリに作る．

「ターミナル」で
```
conda create -n py35 python=3.5
```

と打つ．
`py35` は好きな名前にしてよい．

作られた `py35` 環境を activate するにはひと工夫必要．

* [pyenvとanacondaを共存させる時のactivate衝突問題の回避策3種類](http://qiita.com/y__sama/items/f732bb7bec2bff355b69)

Activate させたあと最低限のライブラリをインストールする：


## Julia

自分のコンピュータ，大学のコンピュータ共通．

* [Setting up Your Julia Environment](http://quant-econ.net/jl/getting_started.html)

1. julialang.org/downloads の "Julia (command line version)" から自分の OS に合ったものをダウンロードする．
2. ダウンロードされたファイルをダブルクリックし，あとは指示に従う．

### パッケージのインストール

[Setting up Your Julia Environment](http://quant-econ.net/jl/getting_started.html) に従う．


## GitHub

1. github.com でアカウントを作る．
   (誰だか想像できないようなアカウント名のときは，名前を登録する．)
2. アカウント名を教員にメールで知らせる．
3. [QuantEcon.jl](https://github.com/QuantEcon/QuantEcon.jl) を "fork" してみる．

### SourceTree

1. Git の GUI クライアント SourceTree を www.sourcetreeapp.com からダウンロードしてインストールする．
2. SourceTree を立ち上げて，QuantEcon.jl のローカルクローンを作ってみる．  
   リモートレポジトリを設定してみる．
   * [SourceTreeでリモートリポジトリを設定](http://blog.shinji.asia/sourcetree_git/#rem_repo)
