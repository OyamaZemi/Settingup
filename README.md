# 0. この資料の目的

この資料は，ゼミで使う Python・Julia・Git などの作業環境を整えるための案内である．ただし，Python の環境設定には複数の方法があり，最初から一つに決めて読むよりも，まず各方法の役割の違いを理解してから選ぶ方がわかりやすい．VS Code は `venv`，Poetry，`conda` など複数の環境を扱うことができる． 

この資料では，Python の設定を次の二つに分けて考える．
第一に，**Python 本体やライブラリをどう管理するか**である．
第二に，**どの画面でコードを書くか・実行するか**である．
前者は `venv`，Poetry，`conda` などの違いに対応し，後者は VS Code，Jupyter Notebook，Google Colab などの違いに対応する．Jupyter はローカル環境の上で使うノートブック環境であり，Colab はセットアップ不要のホスト型 Jupyter Notebook サービスである． 

以降では，まずそれぞれの方法の位置づけを簡単に整理し，そのあと個別の手順を説明する．ここではまだ，どの方法を採用するかを前提にしない． 

# 1. 環境設定の基本的な見取り図

## 1.1 環境管理の違い

`venv` は Python 標準の仮想環境機能であり，軽量で基本的な方法である．ベースとなる Python の上に，プロジェクトごとに分離された環境を作る．

Poetry は，仮想環境そのものに加えて，依存関係やプロジェクト設定も管理するための道具である．仮想環境は既定ではキャッシュ領域に作られるが，設定によりプロジェクト直下の `.venv` として管理することもできる．

`conda` は，Python のライブラリだけでなく，環境全体をまとめて管理する方法である．環境の作成・切替・書き出しができ，Python の版も環境ごとに分けられる．

要するに，`venv` は最も基本的な仮想環境，Poetry は依存関係管理を強めた方法，`conda` は環境管理をより広くまとめて行う方法，と考えるとよい．

## 1.2 インターフェースの違い

VS Code はエディタであり，選んだ Python 環境を使って編集・実行・デバッグを行うための入口である．環境そのものを作る方法ではなく，`venv`，Poetry，`conda` などで作った環境を切り替えて使う場所だと考えるとよい．

Jupyter Notebook / JupyterLab は，ブラウザ上でコード・出力・説明文をまとめて扱うためのノートブック型インターフェースである．これは Python 環境の代わりではなく，ローカルに用意した Python 環境の上で使う実行画面である． 

Google Colab は，ブラウザだけで使えるホスト型の Jupyter Notebook サービスである．ローカル環境の準備なしに始められる点が利点だが，コードは Google 側の仮想マシンで実行されるため，ローカルの環境管理とは別物である．

## 1.3 何を選ぶ場面なのか

したがって，最初に考えるべきことは二つある．
一つは，**Python 環境をどの方法で管理するか**である．
もう一つは，**どのインターフェースで作業するか**である．
たとえば，`venv` で作った環境を VS Code で使ってもよいし，Poetry で管理した環境を Jupyter から使ってもよい．また，Colab を使う場合は，ローカル環境を使わずに始めることもできる．

# 2. 以降の読み方

ここまでで，Python 環境管理の方法と，作業インターフェースの違いを簡単に整理した．
以降の具体的な設定手順は，方法ごとに別ページに分けてある．
自分が使いたい方法だけを選んで読めばよい．

Python を使う場合は，まず **環境管理の方法** を一つ選び，必要に応じて **インターフェース** のページを読むこと．
大学のコンピュータを使う場合は，通常の手順に加えて専用ページも確認すること．


# 3. 共通準備

環境管理の方法によらず，最初に行う共通準備をまとめる．
Mac の初期設定，VS Code の導入などはここで確認する．

* [Mac の初期設定](docs/mac-setup.md)
* [VS Code の導入と基本設定](docs/vscode-setup.md)


# 4. Python 環境の作り方

Python の環境管理には複数の流儀がある．
以下のうち，自分に合うものを一つ選んで読むこと．

## 4.1 `venv` を使う方法

Python 標準の仮想環境を使うもっとも基本的な方法である．
軽量で構造が単純なので，仕組みを理解しやすい．

* [`venv` による Python 環境構築](docs/python-venv.md)

## 4.2 Poetry を使う方法

仮想環境に加えて，依存関係やプロジェクト設定もまとめて管理する方法である．
再現性を重視したい場合に向いている．

* [Poetry による Python 環境構築](docs/python-poetry.md)

## 4.3 `conda` を使う方法

環境全体をまとめて管理する方法である．
すでに `conda` を使っている人や，`conda` 前提の環境に合わせたい場合はこちらを使う．

* [`conda` による Python 環境構築](docs/python-conda.md)


# 5. 作業インターフェース

Python 環境を用意したあと，どの画面でコードを書くか・実行するかを選ぶ．
VS Code は通常の開発向け，Jupyter Notebook はノートブック形式の作業向け，Google Colab はブラウザだけで始めたい場合に向いている．

* [VS Code の使い方](docs/interface-vscode.md)
* [Jupyter Notebook / JupyterLab の使い方](docs/interface-jupyter.md)
* [Google Colab の使い方](docs/interface-colab.md)


# 6. 大学のコンピュータを使う場合

大学のコンピュータでは，権限や既存設定の都合で，自分のコンピュータと同じ手順がそのまま使えないことがある．
大学の計算機環境で作業する人は，このページも確認すること．

* [大学のコンピュータでの設定](docs/university-pc.md)


# 7. Git / GitHub

バージョン管理と共同作業のために Git と GitHub を使う．
初めて使う人は，まず GitHub アカウントを作成し，そのあと Git の基本操作を確認すること．

* [Git / GitHub の初期設定](docs/git-github.md)


# 8. その他の言語

## 8.1 Julia

Julia を使う場合の導入手順，パッケージ管理，Jupyter との連携については別ページにまとめる．

* [Julia の導入と設定](docs/julia-setup.md)





## Python

Anaconda という Python パッケージをインストールする．
* [Setting up Your Python Environment](https://python-programming.quantecon.org/getting_started.html)

### 自分のコンピュータ

1. https://www.anaconda.com/products/individual#Downloads から自分の OS に合わせてインストラーをダウンロードする．
2. ダウンロードされたファイルをダブルクリックし，あとは指示に従う．



### アップデート (自分のコンピュータのみ)

Anaconda をアップデートするには，「ターミナル」で

```
conda update conda
```

```
conda update anaconda
```

と打つ．

過去に 3.13 未満をインストールしている人は，

```
conda install python=3.13
```

で Python 3.13 にアップデートする．
「conflict が見つかった」と言われたら，当該パッケージを `conda remove` で消していく．
そのあと `conda update conda`, `conda update anaconda` を実行する．  
いつの間にか `anaconda` を消していると，`conda update anaconda` で「anaconda がない」と言われる．
その場合は `conda install anaconda` で `anaconda` を再度インストールする．

