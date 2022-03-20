---
tags:
  - 基本使用方法
---

# リポジトリ
### rspec-rails
https://github.com/rspec/rspec-rails
### factory_bot_rails
https://github.com/thoughtbot/factory_bot_rails

# factory_botスタートガイド
https://github.com/thoughtbot/factory_bot/blob/master/GETTING_STARTED.md

# 参考
https://na-ginnan.com/rails-rspec/
https://qiita.com/Ushinji/items/522ed01c9c14b680222c
https://qiita.com/morrr/items/f1d3ac46b029ccddd017

# インストール
```
$ bundle exec rails generate rspec:install
```

# ファイル生成の設定
```
# config/application.rb

config.generators do |g|
      g.factory_bot false
      g.test_framework :rspec,
        view_specs: false,
        helper_specs: false,
        controller_specs: false,
        routing_specs: false
    end
  end
end
```
# rails_helperの設定
```
# spec/rails_helper.rb

# コメントアウトを外す
Dir[Rails.root.join('spec/support/**/*.rb')].each { |f| require f }

RSpec.configure do |config|
  # 追記する
  config.include FactoryBot::Syntax::Methods
end
```

# .rspecの変更
```
--require spec_helper
--format documentation #追記
```

# binstubでテスト実行
gemのspring-commands-rspecを追加
binstubからrspecを実行するとSpringの恩恵を得ることができ、実行開始時間を早めることができ便利です。
以下のコマンドでrspecのbinstubをインストールします。
```
$ bundle exec spring binstub rspec
```

# 「bundle exec rspec」 と 「bin/rspec」の使い分け
## 立ち上がりの速いbin/rspec
１つのテストファイルを実行する場合は、断然bin/rspecの方が実行が速いです。
新規機能に対して、新しくテストファイルを作成している際は、何度もテスト実行を繰り返すので、立ち上がりが速いbin/rspecを多用しますね。
## 立ち上がり後の実行スピードの速いbundle exec rspec
一方で、新規機能追加等で、既存の全てのテストが落ちていないか確認する際は、bundle exec rspecの方が起動後の実行スピードが速いので効率的です。テスト項目が100を超える場合は、その効果をより実感できると思います。

# モデルRspecの生成
```
$ bundle exec rails g rspec:model message
```

# テストの実行
```
$ bundle exec rspec

```

