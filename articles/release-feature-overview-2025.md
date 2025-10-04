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

# Gemの配置場所の判断基準
1. 環境別の分類
メイン部分（グループ外）

本番環境でも使用するGem
アプリケーションの基本機能に必要なGem
group :development, :test

開発・テスト環境でのみ使用
デバッグ、テスト、コード品質チェック用
group :development

開発環境でのみ使用
開発効率を上げるためのツール
group :production

本番環境でのみ使用（稀）

#シェア機能追加
gem "meta-tags"
rails g meta_tags:install
-　シェア機能追加のURLで以下のgemを追加
[![Image from Gyazo](https://i.gyazo.com/9417372f50ffc9a2f8b45501426476bb.png)](https://gyazo.com/9417372f50ffc9a2f8b45501426476bb)

https://zenn.dev/goldsaya/articles/ba945b877daa07#5.-top_image%E3%81%AE%E4%BD%9C%E6%88%90
