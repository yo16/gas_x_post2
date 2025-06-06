# ユーザー向けREADME
- 開発者でなく、使う人向け

## 初期設定
- スプレッドシートを作成
- スプレッドシートの名前を `Contents` にする
    - 変えたい場合は、`s00_initialize.js` の `SHEET_NAME` を変更する
- スプレッドシートの1行目に、以下のように列を作成

| 任意 | 任意 | 日時 | ポストメッセージ | 投稿済み |

- X Developer Portalの準備
    - (割愛)
    - CLIENT_IDと、CLIENT_SECRETを取得する
    - (後で、Callback URI / Redirect URL を設定する)
- スクリプトの準備
    1. 機能拡張＞Apps Scriptを起動
    2. `コード.gs`に最初から入っているコードを全部消す
    3. `code.js`のコードをコピーして、`コード.gs`に貼り付ける
    4. コードの上の方にある、設定の`SHEET_NAME`、`INITIAL_CLIENT_ID`、`INITIAL_CLIENT_SECRET`を入力する
    5. メニュー上の関数のプルダウンで、`initialize`を選択し、実行ボタンを押す
       1. ログに"initliazed"と出力されればOK
    6. デプロイする
       1. メニューのデプロイ＞新しいデプロイを選択
       2. 左ペインの上の方にある歯車アイコンを押す
       3. ウェブアプリを選択
       4. 変更する必要はなく、そのままデプロイボタンを押す
       5. データへのアクセスを許可する必要があるので、アクセスを承認ボタンを押す
       6. Spread Sheetを使うGoogle アカウントを選択
       7. "Google hasn’t verified this app"というメッセージが出るが、その下の"Advanced"を選択
       8. "Go to ○○ (unsafe)"というメッセージが出るので、それを選択
       9. Allowボタンを押す
       10. ウェブアプリのURLをコピーするリンクをクリックし、コピーする
       11. X Developer PortalのCallback URL / Redirect URLに、コピーしたURLを設定する
    1.  `code.js`のコードの上の方にある、設定の`REDIRECT_URL`に、コピーしたURLを設定する
    2.  OAuth2.0の設定
        1.  メニュー上の関数のプルダウンで、`main`を選択し、実行ボタンを押す
        2.  ログにURLが出力されるので、それをコピーしてブラウザで開く
        3.  GASが使用するXアカウントを選択し、許可する
        4.  "準備完了!!"と出力されたらOK
    3.  スクリプトの設定値の確認
        1.  メニュー上の関数のプルダウンで、`checkProperties`を選択し、実行ボタンを押す
        2.  6行表示されるが、4行だけ表示されればOK. 下の2行は空でOK
- 動作の確認
    1.  スクリプトの、メニュー上の関数のプルダウンで、`main`を選択し、実行ボタンを押す
    2.  XにポストされればOK

- トリガーの設定
    1. スプレッドシートの左のメニューから、`トリガー`（時計のアイコン）を選択
    2. 右下の"トリガーを追加"ボタンを押す
    3. 各種項目を設定
        1. 関数: `main`
        2. 実行するデプロイを選択: Head（変更なし）
        3. イベントのソースを選択: 時間主導型
            - 任意に設定する
        4. 右下の保存ボタンを押す

