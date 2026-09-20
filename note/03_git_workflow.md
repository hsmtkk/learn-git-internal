# Gitワークフロー：add と commit

## git add の仕組み

1. ファイル内容を読み込み、SHA-1で blob オブジェクトを生成
2. blob を `.git/objects/` に保存（ロースオブジェクト）
3. インデックス（`.git/index`）に blob ハッシュを登録

## git commit の仕組み

1. インデックスの内容から tree オブジェクトを再帰的に生成
2. commit オブジェクトを生成（treeハッシュ + 親コミット + メッセージ）
3. `.git/refs/heads/<branch>` にコミットハッシュを書き込み
4. `.git/logs/HEAD` に履歴を追加

## 具体例

- `git add a.txt` → `eb34d73c...` blob 生成
- `git ls-files --stage` → `100644 eb34d73c... 0 a.txt`
- `git commit` → `ee79b43` commit オブジェクト生成

## 確認方法

- `git ls-files --stage` — ステージング済みの blob ハッシュ確認
- `git cat-file -t <hash>` — オブジェクトタイプ確認
- `git cat-file -p <hash>` — オブジェクト内容表示