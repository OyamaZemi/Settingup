この情報は古い可能性があります。加筆修正を募集しています。

# Julia

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
