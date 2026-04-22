# Git / GitHub

## 1. Git と GitHub とは？

Git は，ファイルの変更履歴を記録・管理するためのバージョン管理システムである．複数人で同じファイルを編集するときにも，変更を整理しやすい．GitHub Docs でも，Git はファイルの変更を追跡する version control system と説明されている． 

GitHub は，Git リポジトリをクラウド上に保存し，共同作業を行うためのプラットフォームである．コードの保存，共有，レビュー，pull request を使った共同開発などを行える．また，GitHub 上ではブラウザだけでも一部の Git 関連操作を行える．


## 2. GitHub の利用手順

GitHub を使い始めるには，まず個人アカウントを作成する．

1. [GitHub](https://github.com) にアクセスして個人アカウントを作成する．
2. 登録したメールアドレスを確認する．
3. 必要に応じて，プロフィールの表示名を設定する．
4. GitHub Education に登録する（後述）


## 3. Git の利用手順

### 3.1 Git をインストールする

Git をコマンドラインで使うには，まず Git 本体をインストールする必要がある．GitHub Docs でも，Git を使うには download, install, configure が必要と案内している． 

#### Mac

Mac では Command Line Tools をインストールする際に git もインストールされる。
詳細は[Mac の初期設定](docs/mac-setup.md)を参照。

#### Windows

Windows では Git for Windows の公式インストーラを使う．

* [https://git-scm.com/download/win](https://git-scm.com/download/win)

インストール後，次で確認する．

```bash
git --version
```

Git for Windows の公式サイトでは Windows 用インストーラが案内されている． 

### 3.2 名前とメールアドレスを設定する

Git を使い始める前に，コミットに記録される名前とメールアドレスを設定する．

```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
```

ここで設定した名前とメールアドレスは，今後のコミットに使われる．GitHub 上でコミットを自分のアカウントに正しく関連付けたい場合は，設定したメールアドレスを GitHub アカウントにも追加しておくとよい．GitHub Docs でも，Git のセットアップ手順の一部として username と commit email address の設定を案内している． 



## 4. その他の詳細

### 4.1 GUI クライアント

コマンドラインを使わずに Git を操作したい場合は，GUI クライアントを使ってよい．

#### GitHub Desktop

GitHub Desktop は GitHub 公式の GUI クライアントである．ローカルのリポジトリを扱いながら，commit，push，pull request などを行える．GitHub Docs でも，コマンドラインを使わずにローカルで Git を使いたい場合の選択肢として GitHub Desktop が案内されている． 

* [GitHub Desktop](https://desktop.github.com/)

#### SourceTree

SourceTree は Atlassian の無料 Git GUI クライアントである．Mac と Windows の両方に対応している．

* [SourceTree](https://www.sourcetreeapp.com/)

### 4.2 学生向け GitHub Education

学生は GitHub Education に申請すると，学生向け特典を利用できる．申請には，GitHub の個人アカウントが必要であり，学校発行メールアドレスまたは在学を示す書類によって学生資格を確認する．対象は，学位または diploma を授与する課程に在籍する学習者で，13歳以上であることが必要とされている．

申請手順は次の通りである．

1. [GitHub Education](https://education.github.com/) にアクセスする．
2. GitHub の個人アカウントでサインインする．
3. Education benefits のページで **Start an application** を選ぶ．
4. フォームを送信する．
5. 承認後，GitHub Education portal から特典を利用する． 

### 4.3 GitHub Copilot

GitHub Copilot には Free, Student, Pro, Pro+ などの個人向けプランがある．GitHub Docs の現行ページでは，Copilot Free と Copilot Student は別プランとして案内されている． 

学生として Copilot を利用する場合は，まず GitHub Education の学生認証を完了する．その後，Education benefits ページから **Free GitHub developer resources for students and teachers** の項目を開き，案内に従って Copilot Student を有効化する．GitHub は学生資格を毎月再評価すると案内している．


参考:

* [GitHub Education for students](https://docs.github.com/en/education/about-github-education/github-education-for-students)
* [Apply to GitHub Education as a student](https://docs.github.com/en/education/about-github-education/github-education-for-students/apply-to-github-education-as-a-student)
* [Access GitHub Copilot for free as a student](https://docs.github.com/en/copilot/how-tos/copilot-on-github/set-up-copilot/enable-copilot/set-up-for-students)
* [Plans for GitHub Copilot](https://docs.github.com/en/copilot/get-started/plans)


