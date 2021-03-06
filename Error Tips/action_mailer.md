2019/1/10
> Booksharing: config/environments/production.rb
```ruby
  config.action_mailer.raise_delivery_errors = true
  config.action_mailer.delivery_method = :smtp
- host = 'https://booksharing2019.herokuapp.com/'
+ host = 'https://booksharing2020.herokuapp.com/'
  config.action_mailer.default_url_options = { host: host }
  ActionMailer::Base.smtp_settings = {:address        => 'smtp.sendgrid.net',
````

## 発生した問題
- 本番環境でユーザーの新規登録ができなかった（ログインはできた）

## 原因の特定
1. 「heroku logs -t」コマンドを打って、本番環境（Heroku）のログを確認した
2. アカウント有効化メールの送信でハマったことが判明
3. Railsチュートリアル11.4を参照し、本番環境でSendGridの設定をしていないことが判明
4. ベータ版（booksharing2019）のコードをコピペしたことによって発生したエラーだった

## 問題の解決
1. 完成版（booksharing2020）の本番環境を整えた
2. SendGridのユーザーネーム、パスワードの取得
3. ホスト名をbooksharing2019からbooksharing2020に変更
4. 改めてHerokuにプッシュして、DBのリセット/マイグレーションで解決
