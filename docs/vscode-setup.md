# VS Code の導入と拡張機能

## 1. このページの目的

このページでは，Visual Studio Code のインストール方法と，最初に入れておくと便利な拡張機能をまとめる．  
Python 環境の作成や，VS Code の詳しい使い方は別ページを参照すること．

## 2. VS Code をインストールする

1. [Visual Studio Code の公式ダウンロードページ](https://code.visualstudio.com/download) を開く．
2. 自分の OS に合ったインストーラをダウンロードする．
3. インストーラの案内に従ってインストールする．

## 3. GitHub アカウントにログインする

GitHub Copilot や GitHub 連携機能を使うには，VS Code 上で GitHub アカウントにログインしておくと便利である．

1. VS Code を起動する．
2. 左下または右上の Accounts アイコンを開く．
3. **Sign in with GitHub** を選ぶ．
4. ブラウザが開いたら，GitHub アカウントでログインして認証を完了する．

GitHub Copilot を使う場合は，このときログインした GitHub アカウントに紐づく Copilot プランや利用権限が使われる．

## 4. 拡張機能の入れ方

VS Code を起動し，左側の Extensions アイコンから拡張機能を検索してインストールする．  
拡張機能は Marketplace から追加できる．

### 4.1. 最初に入れておく拡張機能

#### GitHub Copilot
コード補完やチャット機能を使うための拡張機能．  
Visual Studio Code では，GitHub Copilot 拡張を入れると Copilot Chat も利用できる．


#### Japanese Language Pack for VS Code
VS Code の画面表示を日本語化するための拡張機能．


#### テキスト校正くん
日本語の文章や Markdown の校正に便利な拡張機能．  
レポートや README を書くときに役立つ．


### 4.2. Python で役立つ拡張機能

#### Python
Python ファイルの実行や補完，インタープリタ選択などの基本機能を提供する．

#### Pylance
Python の補完や型情報表示を強化する拡張機能．  
Python 拡張と一緒に使う．

#### Python Extension Pack
Python 関連の拡張機能をまとめて導入したい場合に便利な拡張パックである．
下記のJupyterも含まれる。

#### Jupyter
`.ipynb` ファイルを VS Code 上で扱うときに使う．  
Notebook を使う予定がある人は入れておくとよい．
