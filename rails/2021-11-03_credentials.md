---
tags:
  - credentials
---

# 編集
```
$ EDITOR="vi" bin/rails credentials:edit
```

# 環境変数：RAILS_MASTER_KEY
/config/master.keyが共有できない環境ではmaster keyを環境変数：RAILS_MASTER_KEYで指定します。
/config/master.keyが存在せず、環境変数：RAILS_MASTER_KEYでmaster keyが設定されてない場合はcredentials.yml.enc内のデータは読み取れません。
/config/master.key`が存在しなくても、環境変数：RAILS_MASTER_KEYでmaster keyを設定した場合はcredentials.yml.enc内のデータが読み取れるようになります。

# config.require_master_key設定
```
# config/environments/production.rb
config.require_master_key = true
```
上記オプションが有効の場合、master keyが指定されてない状態でサーバ起動を実行しようとするとエラーが発生します。

```
$ rails s

=> Booting Puma
=> Rails 5.2.0 application starting in development
=> Run `rails server -h` for more startup options
Missing encryption key to decrypt file with. Ask your team for your master key and write it to /xxx/my-app/config/master.key or put it in the ENV['RAILS_MASTER_KEY'].
Exiting
```
