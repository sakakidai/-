---
tags:
  - overcommit
---

# リポジトリ
https://github.com/brigade/overcommit

# hookの確認
まずは現状のhookの状態を確認。
.git/hooks/以下に*.sample以外のファイルがあるかを見る。
```
$ ls .git/hooks/ | grep -v '.sample'
```

# インストール
gemで管理しようと思ったが、以下のエラーが出たため断念

エラー
```
This repository contains hooks installed by Overcommit, but the `overcommit` gem is not installed.
Install it with `gem install overcommit`.
```

# 使い方
```
$ overcommit -h
```

# hooksのスキップ
```
# 特定のhookをスキップ
$ SKIP=RuboCop git commit

# すべてのhookをスキップ
$ OVERCOMMIT_DISABLE=1 git commit
```

# 参考記事
https://hotatekun.hatenablog.com/entry/2016/06/12/233435
https://techblog.lclco.com/entry/2018/03/27/170000

