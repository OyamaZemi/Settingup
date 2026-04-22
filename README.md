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


# 7. Julia

Julia を使う場合の導入手順，パッケージ管理，Jupyter との連携については別ページにまとめる．

* [Julia の導入と設定](docs/julia-setup.md)


# 8. Git / GitHub

バージョン管理と共同作業のために Git と GitHub を使う．
初めて使う人は，まず GitHub アカウントを作成し，そのあと Git の基本操作を確認すること．

* [Git / GitHub の初期設定](docs/git-github.md)





## はじめに

* [ターミナルの基本的な使い方](https://hwb.ecc.u-tokyo.ac.jp/wp/information-2/cui/terminal/)

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
* [Setting up Your Python Environment](https://python-programming.quantecon.org/getting_started.html)

### 自分のコンピュータ

1. https://www.anaconda.com/products/individual#Downloads から自分の OS に合わせてインストラーをダウンロードする．
2. ダウンロードされたファイルをダブルクリックし，あとは指示に従う．

### 大学のコンピュータ

デフォルト状態で「ターミナル」で

```
python
```

と打つと Python が立ち上がるようになっている．

Python を終了させるには

```
quit()
```

と入力する．

#### 自前環境の作成

大学のコンピュータの Python 環境には管理者権限がないと新しいライブラリが追加できないので，以下のように最小限の環境を自分のホームディレクトリに作る．

「ターミナル」で
```
conda create -n py313 python=3.13
```

と打つ．
`py313` は好きな名前にしてよい．

#### 自前環境の起動

作られた `py313` 環境を activate するにはひと工夫必要．

* [pyenvとanacondaを共存させる時のactivate衝突問題の回避策3種類](http://qiita.com/y__sama/items/f732bb7bec2bff355b69)

ひとつのやり方は

```
source activate py313
```

(上で違う名前にした人は `py313` の部分を適切に変える．)
(先述のリンクでは`conda activate`が使えるようになったと書いてあるが,大学のコンピュータでは使えなかったので`source activate`でよい.)

このあと `python` と打つと自前の python 環境が立ち上がる (毎回 activate する必要がある)．

#### 自前環境へのライブラリのインストール

Activate させたあと最低限のライブラリをインストールする：

```
conda install numpy scipy jupyter matplotlib numba pandas sympy sphinx numpydoc requests pytest
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

過去に 3.13 未満をインストールしている人は，

```
conda install python=3.13
```

で Python 3.13 にアップデートする．
「conflict が見つかった」と言われたら，当該パッケージを `conda remove` で消していく．
そのあと `conda update conda`, `conda update anaconda` を実行する．  
いつの間にか `anaconda` を消していると，`conda update anaconda` で「anaconda がない」と言われる．
その場合は `conda install anaconda` で `anaconda` を再度インストールする．


## Julia

自分のコンピュータ，大学のコンピュータ共通．

* [Setting up Your Julia Environment](https://julia.quantecon.org/getting_started_julia/getting_started.html)

1. [julialang.org/downloads](http://julialang.org/downloads/) の "Current stable release" から自分の OS に合ったものをダウンロードする．
2. ダウンロードされたファイルをダブルクリックし，あとは指示に従う．

### パッケージのインストール

[Setting up Your Julia Environment](https://julia.quantecon.org/getting_started_julia/getting_started.html) に従う．

何かうまくいかないことがあったら，`Pkg.rm` でパッケージを remove して再度 add すると解決することもある．
たとえば IJulia を消すには Julia を立ち上げた上で

```
] rm IJulia
```

と入力する．

### パッケージのアップデート

パッケージたちをアップデートするには (Julia を立ち上げた上で)

```
] update
```

と入力する．
毎回ゼミの前に実行しておくようにするとよい．

### Jupyter Notebook

Jupyter notebook を開いたときに Julia の最新版が反映されない場合は (Julia を立ち上げた上で)

```
] build IJulia
```

と入力して `IJulia` をビルドし直す．



## Git
バージョン管理システム.変更履歴が残り,共同作業でも混乱する恐れがなくなるので便利.

QuantEconも世界中の開発者が共同で開発しているので,このシステムを使っている.
[git入門](https://backlog.com/ja/git-tutorial/intro/intro1_1.html)


### GitHub

Gitを扱うサーバー.

1. [github.com](https://github.com) でアカウントを作る．
   (誰だか想像できないようなアカウント名のときは，名前を登録する．)
2. [QuantEcon.py](https://github.com/QuantEcon/QuantEcon.py) を "fork" してみる．

### SourceTree

Gitの操作を簡単にするGUIツール.

1. Git の GUI クライアント SourceTree を www.sourcetreeapp.com からダウンロードしてインストールする．
2. SourceTree を立ち上げて，QuantEcon.py のローカルクローンを作ってみる．  
   リモートレポジトリを設定してみる．

## 学生として GitHub Copilot Pro を無料利用する手続き

1. **学生認証を受ける**  
   * [GitHub Education](https://education.github.com/) に学生として申請する必要がある．
   * 学校ドメインのメールアドレス，または学生証等の在籍証明書類の提出が求められる．
   * 参考リンク内のドキュメントから "Apply" リンクで申請し，承認を待つ．
   * 承認完了後に次の手順（Copilot 有効化）へ進む．
   * なお，学生資格は毎月再評価され，失効すると無料利用も停止する．

2. **Copilot Pro へアクセスする**  
   承認後，GitHub のプロフィール → Settings → Copilot (Your Copilot) で「Get access」をクリック．

3. **設定を保存する**  
   利用規約とデータ利用ポリシーを確認して保存．

4. **注意点**
   * 毎月，学生資格の再評価が行われる
   * 表示されない場合は再ログインや承認状況を確認
   * 既存の有料プランやトライアルがある場合は先に解除が必要

5. **代替手段**  
   資格がない場合は [Copilot Free](https://github.com/features/copilot) または Pro トライアル (30日間) を検討．

参考リンク：
* [Getting free access to GitHub Copilot Pro as a student, teacher, or maintainer](https://docs.github.com/en/copilot/managing-copilot/managing-copilot-as-an-individual-subscriber/managing-your-copilot-subscription/getting-free-access-to-copilot-as-a-student-teacher-or-maintainer)
* [Getting started with a GitHub Copilot plan](https://docs.github.com/en/copilot/about-github-copilot/subscription-plans-for-github-copilot)
