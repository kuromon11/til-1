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