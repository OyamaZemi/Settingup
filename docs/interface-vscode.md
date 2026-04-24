# VS Code の使い方

## 1. このページの目的

このページでは，VS Code を使って作業を始めるときの基本操作をまとめる．
VS Code のインストールや拡張機能の導入は `vscode-setup.md` を参照し，Python 環境の作成は
`python-venv.md`，`python-poetry.md`，`python-conda.md` を参照すること．VS Code では，
フォルダを開いて作業し，必要に応じて統合ターミナルや Source Control を使うのが基本である．

## 2. VS Code の画面

VS Code の画面で最初に覚えておくとよいのは，次の部分である。
**Activity Bar** は左端にあり，Explorer や Source Control などの表示を切り替える。
**Side Bar** には Explorer などの各種ビューが表示される。**Editor** はファイルを編集する場所で，
複数のファイルを横や縦に並べて開ける。**Panel** には統合ターミナルや出力，エラー表示などが出る。
**Status Bar** には開いているプロジェクトや編集中のファイルに関する情報が表示される。


## 3. Python を使う前に最初にやること

Python を VS Code で使うときは，まず **Python 環境を用意し，VS Code にその環境を選ばせる**．  
やることは，どの流儀でも次の 3 段階である．

1. メニューから **File > Open Folder...** を選び，作業したいフォルダを開く。 
2. Python 環境を用意する  
3. **Python: Select Interpreter** でその環境を選ぶ  

環境ごとの最初の手順は次の通りである．

### 3.1 `venv` を使う場合

作業フォルダを開き，統合ターミナルで仮想環境を作る．

macOS / Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
````

Windows:

```powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
```

その後，Command Palette を開いて **Python: Select Interpreter** を実行し，`.venv` を選ぶ．
Comand Palette は macOS では `⇧⌘P`，Windows / Linux では `Ctrl+Shift+P` で開ける。
通常は，ワークスペース直下の `.venv` が候補に表示される．

なおこの `.venv` は，`-m venv` の前に指定した Python を土台にして作られる．  
たとえば macOS / Linux で

```bash
python3.12 -m venv .venv
```
と実行すれば Python 3.12 の環境が作られる．
Windows では

```bash
py -3.12 -m venv .venv
```

のように版を指定できる．

### 3.2 Poetry を使う場合

作業フォルダを開き，統合ターミナルで必要な設定と依存関係の準備を行う．

まだ `pyproject.toml` がない場合は，先に

```bash
poetry init
```
を実行する。

そのうえで、以下を実行する。

```bash
poetry config virtualenvs.in-project true --local
poetry install
```


Poetry は現在のシェルで使える Python を使って環境を作ることがあるが，必要なら次のように明示的に指定できる．
これは `poetry install` の前に行う。

```bash
poetry env use python3.12
```


その後，**Python: Select Interpreter** を実行し，Poetry が作った `.venv` を選ぶ．
`.venv` をプロジェクト直下に作る設定にしていれば，`venv` の場合と同様に見つけやすい．

### 3.3 `conda` を使う場合

作業フォルダを開き，統合ターミナルで必要な設定を行う。
`conda` では，環境ごとに Python の版を直接指定できる．

```bash
conda create -n py313 python=3.13
conda activate py313
```

その後，**Python: Select Interpreter** を実行し，`conda` 環境 `py313` を選ぶ．


### 3.4 動作確認

interpreter を選んだあと，新しいファイル `hello.py` を作り，次を書く．

```python
print("Hello, world!")
```

保存したあと，右上の **Run Python File in Terminal** を押す．
下のターミナルに

```text
Hello, world!
```

と表示されれば成功である．

補足:

* Python 拡張を入れていれば，**Run Python File in Terminal** が使える．
* Python 拡張を入れていない場合は，統合ターミナルで直接 `python hello.py` または `python3 hello.py` を実行する．
* コードの一部だけ試したい場合は，行や選択範囲に対して `Shift+Enter` でも実行できる．(拡張機能)


### 3.5 パッケージをインストールする

Python 環境を用意して interpreter を選んだあと，必要なパッケージをその環境に入れる．  
インストールは VS Code の**統合ターミナル**で行うと分かりやすい．

#### `venv` を使う場合

`venv` では， `pip` を使う．  
`pip` は仮想環境の中にパッケージを入れるので，他のプロジェクトの環境に影響しにくい．

macOS / Linux:

```bash
python3 -m pip install --upgrade pip
python3 -m pip install numpy scipy matplotlib pandas jupyter quantecon
```

Windows:

```powershell
py -m pip install --upgrade pip
py -m pip install numpy scipy matplotlib pandas jupyter quantecon
```

#### Poetry を使う場合

Poetry では，パッケージ追加は `poetry add` を使う．
`poetry add` は依存関係をインストールするだけでなく，`pyproject.toml` と `poetry.lock` も更新する．
既に `pyproject.toml` があり，そこに書かれた依存関係をまとめて入れたいだけなら `poetry install` を使う．

```bash
poetry add numpy scipy matplotlib pandas jupyter quantecon
```

既存プロジェクトの依存関係を入れるだけなら：

```bash
poetry install
```

#### `conda` を使う場合

`conda` では， `conda install` を使う．
環境名を指定しなければ，現在の環境にインストールされる．

```bash
conda install numpy scipy matplotlib pandas jupyter
```

`conda` で見つからないパッケージは，まず `conda-forge` を試し，それでもなければ環境内の `pip` を使う．

```bash
conda install -c conda-forge quantecon
```

または：

```bash
conda install pip
pip install quantecon
```

#### 補足

* `venv` では `pip` が基本である．
* Poetry では `poetry add` と `poetry install` を使う．
* `conda` では `conda install` が基本であり，必要に応じて `conda-forge` や `pip` を使う．
* どの場合も，**今選んでいる環境に対してインストールしているか**を意識することが重要である．


## 4. 統合ターミナルを使う

VS Code には **統合ターミナル** があり，通常のターミナルと同じようにコマンドを実行できる。
メニューの **Terminal > New Terminal** や **View > Terminal** から開ける。
Command Palette の **View: Toggle Terminal** でも開ける。ショートカットは 
macOS では `⌃\``，Windows / Linux では `Ctrl+`` である。新しいターミナルを作るショートカットも用意されている。
Explorer 上のフォルダを右クリックして **Open in Integrated Terminal** を使うこともできる。 

Python や Git の操作で困ったら，まずこの統合ターミナルでコマンドを打つとよい。`venv` や `conda` の activate もここで行う。 

## 5. Source Control を使う

開いているフォルダが Git 管理されている場合，VS Code の **Source Control** ビューから変更確認，stage，commit，同期などを行える。
Source Control ビューは Git 操作の中心であり，差分表示や履歴表示，ブランチ関係の確認にも対応している。
コミットメッセージを入力して commit でき，リモートとつながっていれば push / pull / sync も行える。
Git の詳しい使い方は `git-github.md` を参照すること。

## 6. 設定

VS Code の設定は，大きく **User Settings** と **Workspace Settings** に分かれる。
全体に共通で使いたい設定は User Settings，そのフォルダだけに適用したい設定は Workspace Settings に書く。
Python の interpreter や表示方法をプロジェクトごとに変えたい場合は，Workspace Settings を使うと管理しやすい。設定画面は `⌘,` / `Ctrl+,` で開ける。 
