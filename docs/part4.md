## おまけ

### git 史

- git を作った人 : リーナス・トーバルズ
- Linux のバージョン管理に使っていたツールがイロイロあって使えなくなった
- 代替えになりそうなものが無いから **自分で作った**
- ひと月に満たないうちに概ね作り終えた
- `Initial revision of "git", the information manager from hell`

### Tips

- `git stash`
- `git rebase`
- `git rebase -i`
- `git log -S`

### Git Flow

![](http://justinhileman.info/article/changing-history/git-flow.png)

(since http://justinhileman.info/article/changing-history/)

### Git LFS

巨大なバイナリファイルなどを git で管理するのは厳しい。
現に GitHub にはリポジトリのサイズ上限がある。

これを解決しようとしているのが Git LFS (Large File System) だ。
ザックリ言えば、でかいファイルは S3 のような外部のストレージサービスを用いて、git としてはラベルの様なもだけを管理する。

- [git-lfs/git-lfs: Git extension for versioning large files - GitHub](https://github.com/git-lfs/git-lfs)
