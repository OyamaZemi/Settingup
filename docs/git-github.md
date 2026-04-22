# Git / GitHub

## Git

Git はバージョン管理システムである．
ファイルの変更履歴を記録できるため，過去の状態に戻したり，複数人での作業を整理したりしやすい．
GitHub 上の共同開発も，ローカルでは Git を使って行う．


## GitHub

GitHub は，Git リポジトリをホストし，共同開発を行うためのプラットフォームである．
アカウントを作成すると，リポジトリの作成，fork，issue，pull request などを利用できる．

1. [GitHub](https://github.com) で個人アカウントを作成する．
2. メールアドレスを確認する．
3. 必要に応じて，プロフィールの表示名を設定する．
4. 練習として， [QuantEcon.py](https://github.com/QuantEcon/QuantEcon.py) を fork してみる．

fork は，元のリポジトリを自分のアカウント側にコピーして，変更を加えた後に pull request を送るための仕組みである．
元のリポジトリの更新を取り込むには，upstream リモートを設定して同期する．

## Git の初期設定

コマンドラインで Git を使う場合は，名前とメールアドレスを設定しておく．

```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
````

ここで設定した名前とメールアドレスは，今後のコミットに使われる．
GitHub 上でコミットを自分のアカウントに正しく関連付けたい場合は，設定したメールアドレスを GitHub アカウントにも追加しておくとよい．

## GitHub への接続方法

コマンドラインから GitHub を使うときは，HTTPS または SSH で認証する．
SSH を使うと，毎回トークンを入力せずに認証できる．
必要なら SSH 鍵を作成して GitHub に登録する．

* [GitHub に SSH で接続する方法](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)

## GUI クライアント

コマンドラインを使わずに Git を操作したい場合は，GUI クライアントを使ってよい．

### GitHub Desktop

GitHub Desktop は GitHub 公式の無料オープンソースGUIクライアントである．
GitHub 上のリポジトリを clone / fork して，commit，push，pull request などを行える．

* [GitHub Desktop](https://desktop.github.com/)

### SourceTree

SourceTree は Atlassian の無料 Git GUI クライアントである．
Git の基本操作を画面上で行いたい場合に使える．

1. [SourceTree](https://www.sourcetreeapp.com/) をダウンロードしてインストールする．
2. SourceTree を起動し，リポジトリを clone する．
3. 必要に応じてリモートリポジトリを設定する．

## 学生向け GitHub Education

学生は GitHub Education に申請すると，学生向け特典を利用できる．
申請には，GitHub の個人アカウント，学校発行メールアドレスまたは在学を示す書類，および年齢要件などが必要である．

1. [GitHub Education](https://education.github.com/) にアクセスする．
2. GitHub の個人アカウントでサインインする．
3. Education benefits のページから **Start an application** を選び，申請を行う．
4. 承認後，Education ポータルから各種特典を利用する．

## GitHub Copilot

GitHub Copilot には Free, Student, Pro, Pro+ などの個人向けプランがある．
通常の個人ユーザーは Copilot Free を使い始めることができる．
検証済みの学生は Copilot Student の対象であり，プレミアム機能を無料で利用できる．

### 学生として Copilot を利用する場合

1. まず GitHub Education の学生認証を完了する．
2. 認証後，GitHub の Education benefits ページを開く．
3. **Free GitHub developer resources for students and teachers** の項目から Copilot Student を有効化する．
4. 利用ポリシーを確認し，設定を保存する．

### 注意

* GitHub は学生資格を毎月再評価する．
* 学生向け特典は GitHub Education の認証が前提である．
* 2026年4月20日以降，Copilot Pro / Pro+ / Student の新規登録は一時停止中である．最新状況は公式ドキュメントを確認すること．
* 学生向けプランを使えない場合でも，多くの個人ユーザーは Copilot Free を利用できる．

参考:

* [GitHub Education for students](https://docs.github.com/en/education/about-github-education/github-education-for-students)
* [Apply to GitHub Education as a student](https://docs.github.com/en/education/about-github-education/github-education-for-students/apply-to-github-education-as-a-student)
* [Access GitHub Copilot for free as a student](https://docs.github.com/en/copilot/how-tos/copilot-on-github/set-up-copilot/enable-copilot/set-up-for-students)
* [Plans for GitHub Copilot](https://docs.github.com/en/copilot/get-started/plans)
