# .git ディレクトリ構造

## 主要ファイル

- **HEAD**: 現在のブランチを参照。`ref: refs/heads/main`
- **config**: リポジトリ設定。remote/branch 情報を含む
- **description**: リポジトリ名（未設定）
- **index**: ステージング領域（バイナリ）
- **packed-refs**: パックされた参照（リモートブランチなど）

## ディレクトリ

- **objects/**: オブジェクト（ blobs/trees/commits/tags ）
  - `info/`, `pack/`（.pack, .idx, .rev）
- **refs/**: 参照（ブランチ、タグ、リモート）
  - `heads/main` = fbb6f3c...
  - `remotes/origin/`
- **logs/**: 参照の更新ログ（REFLOG）
  - `HEAD`, `refs/heads/main`, `refs/remotes/origin/HEAD`
- **hooks/**: カスタマイズ可能なフック（.sample が付く）
- **info/exclude**: .gitignore 相当の除外設定

## リポジトリ状態

- クローン直後（clone から）
- HEAD = main ブランチ
- 最新コミット: fbb6f3c70178ed385f2699c9b01b6ba7efa85c93
- リモート: origin (https://github.com/hsmtkk/learn-git-internal.git)

## 現在の状態（2026-09-21 更新）

- `git add a.txt`, `git add d.txt`, `git add new_file.txt` で3ファイルをステージ
- コミット: ee79b43, b24efc7, 19465a0
- `git commit-tree` + `git update-ref` で 9060e29 を追加
- `git gc` でオブジェクト最適化
- 最新HEAD: 9060e295cb03e8cdbebebbe9e896e647824e7c0a