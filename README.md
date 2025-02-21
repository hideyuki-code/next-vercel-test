# Next.js Vercel Test Project

このプロジェクトは、Next.jsアプリケーションをVercelにデプロイし、GitHub Actionsを使用して継続的デプロイメントを実現するテストプロジェクトです。

## デプロイメントフロー

### 目的
- チームメンバー全員がVercelアカウントを持つことなく、デプロイプロセスに参加できるようにする
- GitHubのプルリクエストとマージフローを通じて、安全かつ効率的なデプロイを実現する

### 仕組み
1. 開発フロー
   - `feature/*` ブランチで機能開発
   - `develop` ブランチで開発版の統合
   - `main` ブランチで本番環境のデプロイ

2. デプロイメント
   - GitHub Actionsを使用
   - `develop` から `main` へのマージをトリガーとして自動デプロイ
   - Vercelのデプロイトークンを使用（GitHub Secretsで管理）

### メリット
- チームメンバーは個別のVercelアカウントが不要
- 通常のGitHub操作だけでデプロイが可能
- デプロイプロセスの一元管理が可能

## 開発環境

- Node.js
- Next.js
- Bun (パッケージマネージャー)
- TypeScript

## セットアップ

```bash
# 依存関係のインストール
bun install

# 開発サーバーの起動
bun dev
```

## ブランチ戦略

1. 機能開発
   ```bash
   git checkout -b feature/新機能名
   # 開発作業
   git push origin feature/新機能名
   ```

2. 開発版への統合
   - `feature/新機能名` から `develop` へプルリクエスト
   - レビュー後、マージ

3. 本番環境へのデプロイ
   - `develop` から `main` へプルリクエスト
   - レビュー後、マージ
   - GitHub Actionsが自動的にVercelへデプロイ
