# 開発フロー・運用ルール

## 概要
お手伝いクエスト型お小遣いアプリの開発におけるGit運用、Issue管理、チーム連携のルールを定義します。

## チーム体制・担当分担

### 担当ファイル
- **しゅんすけ（PdM）**: `parent_view.py` - 親画面関連機能
- **りす（Lead Designer）**: `child_view.py` - 子画面関連機能  
- **けんた（Lead Engineer）**: `init_db.py`, `user_utils.py` - DB・認証基盤

### Epic（大分類）
1. **親画面機能実装**（しゅんすけ担当）
2. **子画面機能実装**（りす担当）
3. **DB・認証基盤実装**（けんた担当）

## Issue管理

### Issue階層構造
```
Epic: 親画面機能実装
├── Issue: ログイン画面実装
├── Issue: クエスト作成フォーム実装
├── Issue: 発行済みクエスト一覧表示
├── Issue: クエスト編集・削除機能
└── Issue: 完了報告確認・承認機能
```

### カラム（ステータス）管理
- **Backlog**: 詳細未確定、将来実装予定
- **Todo**: 要件明確、すぐ着手可能
- **In Progress**: 実際に作業中（1人1〜2個まで）
- **Review**: PRレビュー中・修正中
- **Done**: マージ済み・完了

### Issue作業の基本フロー
1. TodoからIssueを選択
2. 自分をAssignee設定
3. In Progressに移動
4. 作業開始

## Git運用ルール

### ブランチ戦略
- **main**: 本番用ブランチ（保護済み）
- **feature/[Issue番号]-[機能名]**: 機能開発用

### ブランチ命名規則
```bash
feature/6-quest-create-form
feature/12-quest-execution-ui
feature/3-user-authentication
```

### 開発フロー詳細

#### 1. 作業開始
```bash
# 最新のmainブランチに更新
git checkout main
git pull origin main

# 新しいブランチを作成（GitHubのIssueページから推奨）
# または手動で：
git checkout -b feature/6-quest-create-form
```

#### 2. 開発作業
```bash
# ファイルを編集
# 例：parent_view.py にフォーム機能を追加

# 変更をコミット
git add .
git commit -m "[add] クエスト作成フォーム基本機能"
```

#### 3. プッシュ・PR作成
```bash
# リモートにプッシュ
git push origin feature/6-quest-create-form

# GitHubでPull Request作成
# PR説明欄に以下を記載：
# - Closes #6
# - 実装内容の説明
# - 確認方法
```

#### 4. レビュー・マージ
- チームメンバーが24時間以内にレビュー
- 修正が必要な場合は追加コミット
- 承認後にマージ
- Issueが自動クローズ

## コミットメッセージ規則

### 形式
```
[種類] 変更内容
```

### 種類の例
- `[add]` - 新機能追加
- `[fix]` - バグ修正
- `[update]` - 既存機能の更新
- `[refactor]` - リファクタリング
- `[docs]` - ドキュメント更新

### 例
```bash
git commit -m "[add] クエスト作成フォーム基本機能"
git commit -m "[fix] ログイン認証のバグ修正"
git commit -m "[update] UI レスポンシブ対応"
```

## PR・レビュールール

### PR作成時
- タイトルはIssueと対応させる
- 説明欄に `Closes #Issue番号` を記載
- 実装内容と確認方法を明記
- スクリーンショット等があれば添付

### レビュー観点
- 機能が正しく動作するか
- コードの可読性
- ワイヤーフレーム通りのUI
- セキュリティ観点（認証周り）

### レビュー対応
- 24時間以内にレビュー実施
- コメントはすべて解決してからマージ
- 修正後は再レビュー依頼

## 競合回避・解決

### 競合回避策
1. **作業前の更新**: `git pull origin main`
2. **小さなPR**: 機能完成したらすぐPR
3. **事前相談**: 共通ファイル（app.py等）を触る時はSlack連絡
4. **作業宣言**: 「今日はここやります」をSlackで共有

### 担当ファイル分担による競合最小化
- 基本的に異なるファイルを編集するため競合は稀
- 共通ファイル編集時のみ注意が必要

## 日常的なコミュニケーション

### 進捗報告
- Issueコメントで定期的な進捗更新
- 困った時はIssueで質問・相談
- 緊急時はSlackで直接連絡

### 定例確認
- GitHub Projectsボードで全体進捗を可視化
- 必要に応じてMTGで調整

## トラブルシューティング

### よくある問題と対処法

#### PRマージ後にIssueがクローズされない
- PR説明欄に `Closes #Issue番号` が記載されているか確認
- 手動でIssueをクローズ

#### ブランチの切り替えができない
```bash
# 未コミットの変更がある場合
git stash
git checkout main
git stash pop
```

#### 間違ったブランチにコミットしてしまった
```bash
# まずは慌てずにSlackで相談
# 基本的には新しいブランチを作り直し
```

---
最終更新: 2025/9/16  
作成者: PdM（しゅんすけ）
