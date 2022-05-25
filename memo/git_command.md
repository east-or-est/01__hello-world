# Git・GitHubメモ


***

## アクセストークン

「Settings＞Developer settings」から「Personal access tokens」を選択し、アクセストークンを発行する。
今回は試しに7日間＆とりあえずrepoだけ選択した。

トークンを早く削除したい場合は管理画面から削除する。

### プライベートリポジトリをcloneするとき

```
git clone https://ghp_＜トークン＞@github.com/east-or-est/＜プライベートリポジトリ名＞
```

### pushするとき

```
Username for 'https://github.com':east-or-est
Password for 'https://east-or-est@github.com':＜ここでアクセストークンを入力＞
```

## メモ

SourcetreeとVSCodeの設定を見直す。
Sourcetreeはなぜかコンクリフトしてしまう。

## アクセストークン

「Settings＞Developer settings」から「Personal access tokens」を選択し、アクセストークンを発行する。
今回は試しに7日間＆とりあえずrepoだけ選択した。

トークンを早く削除したい場合は管理画面から削除する。

### プライベートリポジトリをcloneするとき

```
git clone https://ghp_＜トークン＞@github.com/east-or-est/＜プライベートリポジトリ名＞
```

### pushするとき

```
Username for 'https://github.com':east-or-est
Password for 'https://east-or-est@github.com':＜ここでアクセストークンを入力＞
```

## .gitignoreのメモ

Next.jsはデフォルトで用意されている。

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


## （確認中）これからは~/.config/git/ignoreから、pushするファイル（共通）の対策を張ること

~/.config/git/ignoreが動かない。

~/.gitignore_globalかと思い調べてもこちらも効かない。

https://docs.github.com/ja/get-started/getting-started-with-git/ignoring-files

キャッシュが原因というのもあるらしいが、ここは調べておく。



間違えて.DS_Storeを上げてしまうことがよくあるから、最初の環境準備は要注意。

削除するときはコマンドから。そのあとaddと同様の手順で。

```
git rm .DS_Store
```