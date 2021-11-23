---
tags:
  - solargraph
---

# 概要
solargraph language serverが起動し、コードの補完、gem内へのメソッドジャンプが出来るようになる。

# リポジトリ
https://github.com/castwide/solargraph

# 参考
https://zenn.dev/massu_devix/articles/e400308d55011d
https://qiita.com/hideki0145/items/d6a18095f95d57eebe96

# 設定ファイル生成
```
$ bundle exec solargraph config
```

# .solargraph.yml
```
---
include:
- "**/*.rb"
exclude:
- spec/**/*
- test/**/*
- vendor/**/*
- ".bundle/**/*"
require:
- actioncable
- actionmailer
- actionpack
- actionview
- activejob
- activemodel
- activerecord
- activestorage
- activesupport
domains: []
reporters:
- rubocop
- require_not_found
formatter:
  rubocop:
    cops: safe
    except: []
    only: []
    extra_args: []
require_paths: []
plugins: []
max_files: 5000
```