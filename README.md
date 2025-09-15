# お手伝いクエスト型お小遣いアプリ

## プロジェクト概要
親が子供にお手伝いを「クエスト」として発行し、子供が実行・報告、親が承認して報酬を渡すゲーミフィケーション型お小遣いアプリです。

**開発期間**: 2025/9/16 - 9/29（2週間）  
**技術スタック**: Streamlit + SQLite + SQLAlchemy

## チーム体制
- **Lead Designer**: りすさん
- **Lead Engineer**: けんたさん  
- **PdM**: しゅんすけさん

## ファイル構成
```
team1_3peace/
├── app.py              # メインアプリ（ログイン・画面切替）
├── init_db.py          # DB初期化スクリプト
├── user_utils.py       # ユーザー関連処理（登録・認証）
├── parent_view.py      # 親用画面UI
├── child_view.py       # 子用画面UI
├── requirements.txt    # Python依存関係
├── .env.example        # 環境変数サンプル
├── .gitignore          # Git除外設定
├── data/               # データベースファイル格納用
└── docs/               # ドキュメント
    └── requirements_definition.md  # 要件定義書
```

## 開発環境セットアップ

### 必要な環境
- Python 3.9+
- Git

### セットアップ手順
1. リポジトリをクローン
```bash
git clone [リポジトリURL]
cd team1_3peace
```

2. 仮想環境作成・有効化
```bash
python -m venv venv
# Windows
venv\Scripts\activate
# Mac/Linux  
source venv/bin/activate
```

3. 依存関係インストール
```bash
pip install -r requirements.txt
```

4. 環境変数設定
```bash
cp .env.example .env
# .envファイルを編集
```

5. データベース初期化
```bash
python init_db.py
```

6. アプリ起動
```bash
streamlit run app.py
```

## 開発ルール

### ブランチ戦略
- `main`: 本番用ブランチ（保護済み）
- `feature/[担当者]/[機能名]`: 機能開発用
- 例: `feature/shun/quest-create`, `feature/risu/quest-list`

### コミット規則
- 日本語OK
- 形式: `[種類] 変更内容`
- 例: `[add] クエスト作成画面`, `[fix] ログイン処理のバグ修正`

### PR・レビュー
- PRには必ず1人以上の承認が必要
- コメントはすべて解決してからマージ
- 機能が完成したらすぐPRを出す

## Phase 1 機能・担当分担

### しゅんすけ担当: parent_view.py
- クエスト作成機能
- クエスト管理（一覧・編集・削除）
- 報酬設定

### りす担当: child_view.py  
- クエスト一覧表示
- クエスト実行・完了報告
- 実績確認・グラフ表示

### けんた担当: DB・認証基盤
- init_db.py（データベース設計・初期化）
- user_utils.py（認証処理・パスワードハッシュ化）

## データベース設計
- **User**: ユーザー情報（親・子識別）
- **Quest**: クエスト定義
- **QuestExecution**: クエスト実行ログ
- **Reward**: 報酬記録
- **Achievement**: 実績・バッジ

## 開発進捗
- [GitHub Projects](https://github.com/users/Shun0914/projects/4)
- [要件定義書](./docs/requirements_definition.md)

## 困った時は
- GitHub Issuesで質問・相談
- 緊急時は直接連絡

---
最終更新: 2025/9/16
