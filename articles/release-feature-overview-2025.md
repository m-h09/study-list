---
title: "本リリース機能について"
emoji: "✍️"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["rails", "github"]
published: false
---
履歴機能:
シェア機能:https://zenn.dev/yukimura_n/articles/1007c5dbedebc1

gem 'sorcery', '~> 0.18.0'を利用

実装時のポイント
既存アプリへの影響を最小化

# 既存のルーティングを保護
class ApplicationController < ActionController::Base
  before_action :require_login, except: [:index, :show]  # 必要に応じて調整
end

テスト環境での確認
本番環境に影響しないよう、開発環境で十分テスト
既存機能が正常動作することを確認

docker exec -it lingo_emoji-db-1 /bin/bash
