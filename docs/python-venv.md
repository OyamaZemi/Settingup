# Python (`venv` を使う方法)

`venv` は Python 標準ライブラリに含まれる仮想環境機能である．既に入っている Python の上に，プロジェクトごとに分離された軽量な環境を作れる．`conda` のように Python 本体まで環境単位で管理する方法ではなく，まず Python をインストールした上で，その Python に対して仮想環境を作る方法だと考えるとよい．

## 1. Python をインストールする

まず Python 本体をインストールする．
`venv` は Python に付属する機能なので，通常は `venv` 自体を別途インストールする必要はない．Python Packaging User Guide でも，前提として公式の Python をインストールしておくことが案内されている． 

1. Python 公式ダウンロードページを開く．
2. 自分の OS に合ったインストーラをダウンロードする．
3. インストーラの案内に従ってインストールする．
4. インストール後，ターミナルでバージョンを確認する． 

macOS / Linux では通常次を使う．

```bash
python3 --version
```

Windows では通常次を使う．

```bash
py --version
```

## 2. 仮想環境を作る

作業したいプロジェクトのフォルダに移動してから，仮想環境を作る．
Packaging User Guide では，プロジェクト直下に `.venv` という名前で作る方法が案内されている．`.venv` はバージョン管理には含めない方がよい． 

macOS / Linux:

```bash
python3 -m venv .venv
```

Windows:

```bash
py -m venv .venv
```

## 3. 仮想環境を有効化する

仮想環境を使う前に activate する．
activate すると，その環境専用の `python` や `pip` が使われるようになる． 

macOS / Linux:

```bash
source .venv/bin/activate
```

Windows (cmd.exe):

```bash
.venv\Scripts\activate.bat
```

Windows (PowerShell):

```powershell
.venv\Scripts\Activate.ps1
```

PowerShell で activate できない場合は，実行ポリシーの設定が必要なことがある．その場合は Python 公式 docs を参照すること．

## 4. 有効化できていることを確認する

仮想環境が有効化されているかどうかは，現在使っている Python の場所を確認すると分かる．
有効化されていれば，表示されるパスの中に `.venv` が含まれる．

macOS / Linux:

```bash
which python
```

Windows:

```bash
where python
```

## 5. `pip` を更新する

`pip` は Python パッケージをインストールするための標準的なツールである．
公式ガイドでも，仮想環境を作ったあと最初に `pip` を更新する手順が案内されている．なお，`venv` は通常 `pip` を一緒に用意する． 

macOS / Linux:

```bash
python3 -m pip install --upgrade pip
```

Windows:

```bash
py -m pip install --upgrade pip
```

## 6. ライブラリをインストールする

仮想環境を有効化したあとで，必要なライブラリを入れる．
パッケージのインストールは `pip install` で行う．ドキュメントとしては，どの Python に対して実行するかが明確になる `python -m pip` の形で書くと分かりやすい． 

例:

macOS / Linux:

```bash
python3 -m pip install numpy scipy matplotlib pandas jupyter
```

Windows:

```bash
py -m pip install numpy scipy matplotlib pandas jupyter
```

`quantecon` を入れる場合は，たとえば次のようにする．

macOS / Linux:

```bash
python3 -m pip install quantecon
```

Windows:

```bash
py -m pip install quantecon
```

## 7. `requirements.txt` を使う

既に `requirements.txt` があるプロジェクトでは，その内容をまとめてインストールできる．
Packaging User Guide でも，requirements file の利用が案内されている．

macOS / Linux:

```bash
python3 -m pip install -r requirements.txt
```

Windows:

```bash
py -m pip install -r requirements.txt
```

現在の環境に入っているライブラリを記録したい場合は，次を使う．

macOS / Linux:

```bash
python3 -m pip freeze > requirements.txt
```

Windows:

```bash
py -m pip freeze > requirements.txt
```

## 8. 仮想環境を終了する

仮想環境を抜けるには，次を実行する．
シェルを閉じても仮想環境は終了する．再び使うときは，同じ activate コマンドを実行すればよい．

```bash
deactivate
```

## 9. VS Code で使う場合

VS Code を使う場合は，この `.venv` を Python interpreter として選ぶ．
VS Code 側の設定方法は `vscode-setup.md` を参照すること．

