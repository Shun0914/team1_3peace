# お手伝いクエスト型お小遣いアプリ

## プロジェクト概要
親が子供にお手伝いを「クエスト」として発行し、子供が実行・報告、親が承認して報酬を渡すゲーミフィケーション型お小遣いアプリです。

**開発期間**: 2025/9/16 - 9/29（2週間）  
**技術スタック**: Streamlit + Python + RDB

## チーム体制
- **Lead Designer**: りすさん
- **Lead Engineer**: けんたさん  
- **PdM**: しゅんすけさん

## 開発環境セットアップ

### 必要な環境
- Python 3.9+
- Git

### セットアップ手順
1. リポジトリをクローン
```bash
git clone [リポジトリURL]
cd [プロジェクト名]
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

5. アプリ起動
```bash
streamlit run app.py
```

## 開発ルール

### ブランチ戦略
- `main`: 本番用ブランチ（保護済み）
- `feature/[担当者]/[機能名]`: 機能開発用
- 例: `feature/design/login-page`, `feature/backend/quest-api`

### コミット規則
- 日本語OK
- 形式: `[種類] 変更内容`
- 例: `[add] ログイン画面の基本レイアウト`, `[fix] クエスト一覧の表示バグ修正`

### PR・レビュー
- PRには必ず1人以上の承認が必要
- コメントはすべて解決してからマージ
- 機能が完成したらすぐPRを出す

## プロジェクト構成
```
├── README.md
├── requirements.txt      # Python依存関係
├── .env.example         # 環境変数サンプル
├── .gitignore
├── app.py              # Streamlitメインファイル
├── src/                # ソースコード
│   ├── components/     # UIコンポーネント
│   ├── models/         # データモデル
│   ├── services/       # ビジネスロジック
│   └── utils/          # ユーティリティ
├── data/               # データベースファイル等
├── tests/              # テストコード
└── docs/               # ドキュメント
```

## Phase 1 機能一覧
- [ ] 親：クエスト発行
- [ ] 子：クエスト受注・実行
- [ ] 子：完了報告
- [ ] 親：承認・却下
- [ ] 報酬記録
- [ ] 履歴表示

## 開発進捗
- [GitHub Projects]()
- [要件定義書]()

## 困った時は
- GitHub Issuesで質問・相談
- 緊急時は直接連絡

---
最終更新: 2025/9/16
