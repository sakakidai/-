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

↓　以下で解決

```
# .overcommit.yml

CommitMsg:
  ALL:
    enabled: false
PreCommit:
 RuboCop:
   enabled: true
   command: ['bundle', 'exec', 'rubocop']
   on_warn: fail # Treat all warnings as failures
gemfile: Gemfile ←　これが抜けてました.
```

# 使い方
```
$ bundle exec overcommit -h
```

# commitの実行結果
```
rails@app:/app$ git commit -m 'corrected overcommit config'
Running pre-commit hooks
Analyze with RuboCop........................................[RuboCop] OK

✓ All pre-commit hooks passed

[main 5c612a4] corrected overcommit config
 3 files changed, 14 insertions(+), 1 deletion(-)

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

