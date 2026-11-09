# Codespaces と GitHub Copilot が利用できることを確認する

## 全体の流れ

1. 本リポジトリを複製
2. 複製先で Codespaces を起動
3. Codespaces 内の Visual Studio Code で GitHub Copilot が動作するか確認
4. (Copilot CLIを利用する場合) CLI の動作確認
5. issue の自動作成を確認
6. (Issue・PR の演習を行う場合) GitHub MCP と GitHub CLI を確認
7. Codespaces の削除

### 1. 本リポジトリを複製

[ここをクリックしてリポジトリを複製](https://github.com/new?template_owner=apc-k-ida&template_name=pre-operation-check-codespaces&owner=%40me&name=codespaces-copilot-test&visibility=private)

リポジトリ作成画面から下記を確認し、問題なければ最後に **「Create repository」** でリポジトリを複製します。

- Owner がご自身のアカウントであること
- リポジトリの可視性が Private であること

![create-template](./assets/create-template.png)

### 2. 複製先で Codespaces を起動

**「Code の Codespaces タブ」** の **「Create codespace on main」** を選択し、Codespaces を起動します。

![start-codespace](./assets/start-codespace.png)

### 3. (Visual Studio Code の Copilot Chat を利用する場合) Codespaces 内の Visual Studio Code で GitHub Copilot が動作するか確認

Codespaces を起動すると、その環境内で Visual Studio Code が立ち上がります（数分かかる可能性があります）。<br>
右下の Copilot アイコン部分でサインインをした後に、右側のチャットウィンドウに何かを入力し、Copilot から応答があれば動作確認は完了です。

![copilot-chat](./assets/copilot-chat.png)

### 4. (Copilot CLI を利用する場合) CLI の動作確認

このリポジトリでは GitHub Copilot CLI も使えるようにしています。

![copilot-cli](./assets/copilot-cli.png)

1. VS Code のターミナルで `copilot` と入力し Enter を押すと、Copilot CLI が起動します。
2. `/login` で GitHub にサインインする
3. `/model` で `Auto` を選択する
4. `hello` などを入力し、Copilot から応答があれば動作確認は完了です。

＊ login 時に token の保存先に関する警告が表示されますが、「**2. keep in memory only**」を選択してください。

![cli-warning](./assets/cli-warning.png)

### 5. issue の自動作成を確認

提供するハンズオンによっては issue の自動作成を行うものがあるため、issue の自動作成ができることを確認します。
下記のように issue が1件作成されていれば、動作確認は完了です。

![create-issue-auto](./assets/create-issue-auto.png)

### 6. (Issue・PR の演習を行う場合) GitHub MCP と GitHub CLI を確認

当日のハンズオンで GitHub Copilot を使って Issue・PR を作成する場合は、Copilot Chat の Agent モードで次のプロンプトを送信してください。

```text
GitHub MCP のツールが利用できるか確認してください。
利用できる場合は、このリポジトリの Issue 一覧を取得し、
使用した MCP ツールと取得結果を報告してください。
作成や変更は行わず、利用できない場合は理由を説明してください。
認証情報は表示しないでください。
```

Copilot にサインインしていても、GitHub MCP が接続済みとは限りません。ツールの実行履歴と取得結果で確認します。接続を設定する場合は [GitHub MCP の公式手順](https://docs.github.com/en/copilot/how-tos/provide-context/use-mcp/set-up-the-github-mcp-server)と組織の利用ルールに従ってください。

MCP が使えない場合の代替手段である GitHub CLI（`gh`）は、このリポジトリの devcontainer でインストールされます。GitHub Copilot CLI（`copilot`）とは別のツールです。ターミナルで確認してください。

```text
gh --version
gh auth status
```

未認証の場合のみ `gh auth login` でブラウザー認証します。既に認証できている場合は再認証不要です。トークンをチャットやリポジトリに保存しないでください。読み取りの成功だけでは書き込みや push の権限を保証しません。

GitHub.com 上の Copilot code review を体験する場合は、研修案内に従って契約・管理者設定による利用可否も確認してください。MCP や CLI の利用可否とは別です。権限不足や組織ポリシーの禁止は CLI で回避せず、担当者に相談してください。

### 7. Codespaces の削除

Codespaces は時間単位の従量課金のため、不要となった場合は削除を推奨いたします。
詳細は[公式ドキュメント](https://docs.github.com/en/billing/concepts/product-billing/github-codespaces)をご確認ください。

左上のハンバーガーメニューから、**「Codespaces」** を選択。

![delete-codespace-1](./assets/delete-codespace-1.png)

削除したい Codespace の「…」から「Delete」で削除します。

![delete-codespace-2](./assets/delete-codespace-2.png)
