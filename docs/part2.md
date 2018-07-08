## git あれこれ

git にはたくさんのコマンドがある。
この章では、たくさんのコマンドのうちローカルで行える基本的なコマンドを紹介しよう。

### 可視化するために (`status`/`log`/`diff`)

GUI を利用している人は何も気にする必要は CLI の git そのものを使う人は、コミットなどの情報を確認するために以下のコマンドを覚えておくと良いだろう。

```
$ git status
$ git log
$ git diff
```

- `git status` は現在のワークツリーやインデックスの状態を確認することができる
- `git log` は積み上げて来たコミットの一覧を確認することができる
- `git diff` はコミット間の差分(変更箇所)を確認することができる

さらに、`git log` にはコミットを綺麗にするオプションがいくつかあってそれを駆使すると次のようなのも表示できる。

```
$ git log --graph --pretty='format:%C(yellow)%h%Creset %s %Cgreen(%an)%Creset %Cred%d%Creset'
```

これを別名として設定しておくと楽に呼び出せる。

```
$ git config --global alias.tr "log --graph --pretty='format:%C(yellow)%h%Creset %s %Cgreen(%an)%Creset %Cred%d%Creset'"
$ git tr
```

### 歴史を重ねる (`add`/`commit`)

まずは前章で既に行なっている、コミットを作る操作をおさらいしよう。

### タイムトラベル (`checkout`)

もし、特定のファイルをひとつ前のバージョンに戻したいとなった時はどうするか。

次のようなコマンドを打つことで現在(`HEAD`)よりひとつ前(`~1` の部分)の `sample.csv` をとってこれる。

```
$ git checkout HEAD~1 sample.csv
```

ファイルを指定しなければ、ひとつ前のコミットにそのままジャンプできる。

```
$ git checkout HEAD~1
```

### パラレルワールド (`checkout -b`/`branch`)

次のコマンドを打ってみよう。

```
$ git branch
```

おそらく `* master` と表示されたはずだ。
これは何を意味するかというと現在の ***ブランチ*** を表示している。
ブランチとは、積み重ねて来たコミット列に名前をつけたものだ。
ブランチを複数用意することで、複数の作業を並行して管理できる。

(ToDo: 例えば)

試しに別のブランチを作って作業をしてみよう。

```
$ git checkout -b update_sample_color
```

適当に `color` の部分を編集してコミットしてみよう。
すると複数のブランチがコミットを平行に積み上げているのがわかるはずだ。

```
$ git tr
```

### 収束する歴史 (`merge`)

分岐したブランチを再度合体させることもできる。
そのような操作を **マージする** という。

試しに、`master` ブランチへ `update_sample_color` ブランチをマージしてみよう。

```
$ git branch
$ git checkout master
$ git merge update_sample_color
```

### まとめ

- git にはコミットなどを可視化するコマンドがいくつかある (`status`/`log`/`diff`)
- git にはコミットを作るためのコマンドがある (`add`/`commit`)
- git には古いコミットに行ったり来たりできるコマンドがある (`checkout`)
- git には複数のコミットを並列に管理するコマンドがある (`checkout -b`/`branch`)
- git にはふたつのコミットを合体させるコマンドがある (`merge`)
