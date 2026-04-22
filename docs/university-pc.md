この情報は古い可能性があります。加筆修正を募集しています。

# 大学のコンピュータ

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
