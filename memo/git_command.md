# gitコマンドメモ


***


## masterブランチを使わずにリポジトリを準備するとき（ボツ）


~~このリポジトリを用意したときのメモ。
「edit」というブランチ名を使用。用途によっては、命名規則を意識した方がいいかもしれない。~~
「edit」ブランチでプルリクなしで反映されてしまったためNG。masterブランチは消すというより使えなくする方が良い？
なのでプッシュしたあとブランチを作ってcheckoutすることに。

以下は当時のボツメモ。

```
echo "# hello-world" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch edit
git remote add origin git@github.com:east-or-est/hello-world.git
git push -u origin edit
```

ローカル側ではmasterブランチのままなので、何かファイルを用意する前にブランチを切り替えてmasterブランチを削除する。

```
git checkout edit
git branch -D master
```

どのブランチを使っているかを確認するとき。

```
git branch -a
```


## これからは~/.config/git/ignoreから、pushするファイル（共通）の対策を張ること

間違えて.DS_Storeを上げてしまうことがよくあるから、最初の環境準備は要注意。