# Python (Poetry を使う方法)

Poetry は，Python プロジェクトの依存関係管理とパッケージ管理のためのツールである．  
`venv` が「環境を分ける」こと自体を中心とするのに対し，Poetry は **仮想環境・依存関係・lockfile をまとめて管理できる** 点が利点である．  
そのため，後から同じ環境を再現したり，他の人と共有したりしやすい．

## 1. 前提: Python をインストールする

Poetry は Python 本体を自動ではインストールしない．  
そのため，まず自分のコンピュータに Python を入れておく必要がある．

1. Python 公式ダウンロードページを開く．
2. 自分の OS に合ったインストーラをダウンロードする．
3. インストーラの案内に従ってインストールする．
4. ターミナルで Python が使えることを確認する．

macOS / Linux:

```bash
python3 --version
```

Windows:

```bash
py --version
```

## 2. Poetry をインストールする

Poetry 自体は，プロジェクトの仮想環境とは別にインストールする．
公式インストーラを使う方法が簡単である．（詳細は公式サイトを確認）

macOS / Linux:

```bash
curl -sSL https://install.python-poetry.org | python3 -
```

Windows (PowerShell):

```powershell
(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | py -
```

インストール後，次で確認する．

```bash
poetry --version
```

## 3. `.venv` を使う設定

Poetry は既定では仮想環境をキャッシュ領域に作るが，設定によりプロジェクト直下の `.venv` を使える．
この資料では，`.venv` を使う形にそろえる．

新しいプロジェクトで次を実行する．

```bash
poetry config virtualenvs.in-project true --local
```

## 4. プロジェクトを作る

新しくプロジェクトを作るには，たとえば次を使う．

```bash
poetry init
```

案内に従って project 名や依存関係を設定すると，`pyproject.toml` が作られる．

## 5. ライブラリを追加する

ライブラリを追加するには `poetry add` を使う．
追加した内容は `pyproject.toml` と `poetry.lock` に記録される．

例:

```bash
poetry add numpy scipy matplotlib pandas jupyter quantecon
```

開発用の依存関係として追加したい場合は，必要に応じて group を使う．
たとえば `pytest` を開発用として追加するには次のようにする．

```bash
poetry add --group dev pytest
```

## 6. 依存関係をインストールする

既に `pyproject.toml` があるプロジェクトでは，次を実行して依存関係を入れる．

```bash
poetry install
```

`poetry.lock` がある場合は，その中に記録された版が使われる．
`poetry.lock` がない場合は，依存関係を解決して新しく作成される．

## 7. コマンドを実行する

Poetry 管理下の環境で Python や他のコマンドを実行するには，`poetry run` を使う．

例:

```bash
poetry run python
```

```bash
poetry run python script.py
```

```bash
poetry run pytest
```

## 8. 仮想環境の場所を確認する

現在のプロジェクトで使われている仮想環境の場所を確認するには，次を実行する．

```bash
poetry env info --path
```

`.venv` を使う設定が有効であれば，通常はプロジェクト直下の `.venv` が表示される．

## 9. 更新する

依存関係を更新したい場合は，次を実行する．

```bash
poetry update
```

これは `pyproject.toml` の制約の範囲内で依存関係を更新し，`poetry.lock` を更新する．

## 10. VS Code で使う場合

VS Code を使う場合は，このプロジェクトの `.venv` を Python interpreter として選ぶ．
設定方法は `vscode-setup.md` を参照すること．

## 11. 補足

* `pyproject.toml` は，依存関係やプロジェクト設定を記録するファイルである．
* `poetry.lock` は，実際に使う依存関係の正確な版を記録するファイルである．
* `poetry.lock` は，環境を再現しやすくするため，通常はリポジトリに含める．

