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



## 4. Git / GitHub の基本的な使い方

ここでは，Git と GitHub を使う基本的な流れを確認する．  
操作には，コマンドラインを使う方法と，VS Code の Source Control UI を使う方法がある．  
どちらを使っても，基本的に行っていることは同じである．

### 4.1 GitHub 上のリポジトリを clone する

GitHub 上のリポジトリを自分のコンピュータにコピーする操作を `clone` という．  
clone すると，ファイルだけでなく変更履歴も含めてローカルに保存される．

コマンドラインでは，次のようにする．

```bash
git clone https://github.com/USER/REPOSITORY.git
```

clone したあと，作成されたフォルダに移動する．

```bash
cd REPOSITORY
```

VS Code では，Command Palette を開いて **Git: Clone** を選び，GitHub のリポジトリ URL を入力する．
または，Source Control ビューから **Clone Repository** を選ぶ．

### 4.2 変更を確認する

ファイルを編集したあと，どのファイルが変更されたかを確認する．

コマンドラインでは次を使う．

```bash
git status
```

VS Code では，左側の **Source Control** アイコンを開くと，変更されたファイルが一覧で表示される．
ファイルを選ぶと，変更前と変更後の差分を確認できる．

### 4.3 変更を stage する

Git では，commit する前に，commit に含めたい変更を stage する．

コマンドラインでは次のようにする．

```bash
git add ファイル名
```

すべての変更を stage する場合は次を使う．

```bash
git add .
```

VS Code では，Source Control ビューで各ファイルの横にある `+` を押すと stage できる．
すべてまとめて stage したい場合は，Changes の横にある `+` を押す．

### 4.4 commit する

stage した変更を，履歴として記録する操作を `commit` という．

コマンドラインでは次のようにする．

```bash
git commit -m "変更内容を表すメッセージ"
```

VS Code では，Source Control ビュー上部の入力欄に commit message を書き，**Commit** を押す．
commit message は，何を変更したかが分かるように短く書く．

### 4.5 GitHub に push する

ローカルで作った commit を GitHub 上のリポジトリに送る操作を `push` という．

コマンドラインでは次のようにする．

```bash
git push
```

新しく作った branch を初めて push する場合は，次のようにすることがある．

```bash
git push -u origin ブランチ名
```

VS Code では，Source Control ビューや画面下部の Status Bar から **Push** または **Sync Changes** を実行できる．
リモートにまだ存在しない branch の場合は，**Publish Branch** が表示されることがある．

### 4.6 GitHub 上の変更を pull する

GitHub 上で他の人が加えた変更を，自分のローカル環境に取り込む操作を `pull` という．

コマンドラインでは次のようにする．

```bash
git pull
```

VS Code では，Source Control ビューや Status Bar から **Pull** または **Sync Changes** を実行する．
作業を始める前には，まず `pull` して最新の状態にしておくとよい．
なお，複数人が同じ箇所を編集した場合などには conflict が発生することがある．
conflict の解消方法は状況によって異なるため，ここでは詳しく扱わない．
必要に応じて各自で調べるか，ゼミ内で相談すること．


### 4.7 branch を作る

新しい作業をするときは，`main` や `master` に直接 commit せず，新しい branch を作るのが基本である．

コマンドラインでは次のようにする．

```bash
git switch -c ブランチ名
```

既存の branch に切り替えるには次を使う．

```bash
git switch ブランチ名
```

VS Code では，画面左下の branch 名をクリックし，**Create new branch** を選ぶ．
または Command Palette から **Git: Create Branch** を実行する．

### 4.8 Pull Request を作る

Pull Request は，自分の branch で行った変更を，元の branch に取り込んでもらうための提案である．
共同作業では，直接 `main` や `master` に push するのではなく，branch を作って commit し，Pull Request を出すことが多い．

基本的な流れは次の通りである．

1. 最新の `main` または `master` から新しい branch を作る
2. 変更する
3. stage する
4. commit する
5. GitHub に push する
6. GitHub 上で Pull Request を作る

コマンドラインでは，たとえば次のような流れになる．

```bash
git switch main
git pull
git switch -c fix-typo
# ファイルを編集する
git add .
git commit -m "Fix typo"
git push -u origin fix-typo
```

その後，GitHub 上で **Compare & pull request** を押して Pull Request を作る．
VS Code でも，GitHub Pull Requests 関連の拡張機能を使うと，Pull Request の作成や確認を VS Code 上で行える．

### 4.9 fork したリポジトリから Pull Request を出す場合

自分に直接 push 権限がないリポジトリへ貢献する場合は，まずそのリポジトリを fork する．
fork は，元のリポジトリを自分の GitHub アカウント側にコピーする操作である．

基本的な流れは次の通りである．

1. 元のリポジトリを GitHub 上で fork する
2. 自分の fork を clone する
3. 新しい branch を作る
4. 変更して commit する
5. 自分の fork に push する
6. 元のリポジトリに Pull Request を出す

コマンドラインでは，たとえば次のようにする．

```bash
git clone https://github.com/YOUR-USER/REPOSITORY.git
cd REPOSITORY
git switch -c fix-typo
# ファイルを編集する
git add .
git commit -m "Fix typo"
git push -u origin fix-typo
```

その後，GitHub 上で base repository に元のリポジトリ，compare branch に自分の fork の branch を選び，Pull Request を作る．

次の作業を始める前には，fork を元のリポジトリと同期してから新しい branch を作るとよい．
古い fork から branch を作ると，前回の変更まで差分に表示されることがある．

### 4.10 review コメントに対応する

Pull Request に review コメントが付いた場合は，同じ branch に追加で commit して push すればよい．
新しい Pull Request を作り直す必要はない．

```bash
# コメントに対応してファイルを編集する
git add .
git commit -m "Address review comments"
git push
```

push すると，既存の Pull Request に追加 commit として反映される．
GitHub 上では，対応したコメントに返信し，必要に応じて **Resolve conversation** を押す．

### 4.11  `.gitignore` を設定する

Git では，仮想環境やキャッシュファイルなど，リポジトリに含める必要のないファイルを除外できる．  
そのために使うのが `.gitignore` である．  
`.gitignore` は，通常リポジトリのルートに置く．

Python プロジェクトでは，たとえば次のように書く．

```gitignore
# Python cache
__pycache__/
*.py[cod]

# Virtual environments
.venv/
venv/
env/
.conda/

# Jupyter
.ipynb_checkpoints/

# VS Code
.vscode/

# macOS
.DS_Store

# Environment variables
.env
```

`venv` や Poetry でプロジェクト直下に `.venv` を作る場合，`.venv/` は Git に含めない．
仮想環境は各自のPCで作り直せるためである．

Poetry を使う場合，`pyproject.toml` と `poetry.lock` は通常 Git に含める．
これらは依存関係とそのバージョンを記録するためのファイルである．

`conda` を使う場合，環境本体は通常リポジトリ外にあるため `.gitignore` に書く必要はない．
ただし，プロジェクト直下に `.conda/` のような環境を作る場合は，`.conda/` を除外する．

`pyenv` を使う場合，プロジェクトに `.python-version` が作られることがある．
チームで Python 版をそろえたい場合は Git に含めてもよいが，個人用の設定として使うだけなら含めない運用もありうる．



## 5. その他の詳細

### 5.1 GUI クライアント

コマンドラインを使わずに Git を操作したい場合は，GUI クライアントを使ってよい．

#### GitHub Desktop

GitHub Desktop は GitHub 公式の GUI クライアントである．ローカルのリポジトリを扱いながら，commit，push，pull request などを行える．GitHub Docs でも，コマンドラインを使わずにローカルで Git を使いたい場合の選択肢として GitHub Desktop が案内されている． 

* [GitHub Desktop](https://desktop.github.com/)

#### SourceTree

SourceTree は Atlassian の無料 Git GUI クライアントである．Mac と Windows の両方に対応している．

* [SourceTree](https://www.sourcetreeapp.com/)

### 5.2 学生向け GitHub Education

学生は GitHub Education に申請すると，学生向け特典を利用できる．申請には，GitHub の個人アカウントが必要であり，学校発行メールアドレスまたは在学を示す書類によって学生資格を確認する．対象は，学位または diploma を授与する課程に在籍する学習者で，13歳以上であることが必要とされている．

申請手順は次の通りである．

1. [GitHub Education](https://education.github.com/) にアクセスする．
2. GitHub の個人アカウントでサインインする．
3. Education benefits のページで **Start an application** を選ぶ．
4. フォームを送信する．
5. 承認後，GitHub Education portal から特典を利用する． 

### 5.3 GitHub Copilot

GitHub Copilot には Free, Student, Pro, Pro+ などの個人向けプランがある．GitHub Docs の現行ページでは，Copilot Free と Copilot Student は別プランとして案内されている． 

学生として Copilot を利用する場合は，まず GitHub Education の学生認証を完了する．その後，Education benefits ページから **Free GitHub developer resources for students and teachers** の項目を開き，案内に従って Copilot Student を有効化する．GitHub は学生資格を毎月再評価すると案内している．


参考:

* [GitHub Education for students](https://docs.github.com/en/education/about-github-education/github-education-for-students)
* [Apply to GitHub Education as a student](https://docs.github.com/en/education/about-github-education/github-education-for-students/apply-to-github-education-as-a-student)
* [Access GitHub Copilot for free as a student](https://docs.github.com/en/copilot/how-tos/copilot-on-github/set-up-copilot/enable-copilot/set-up-for-students)
* [Plans for GitHub Copilot](https://docs.github.com/en/copilot/get-started/plans)


