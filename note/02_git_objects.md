# Gitオブジェクトの仕組み

## 3種類のオブジェクト

- **blob**: ファイルの内容（バイナリ）
- **tree**: ディレクトリ構造（ファイル名 + blob/treeへの参照）
- **commit**: スナップショット（treeのハッシュ、親コミット、著者情報、メッセージ）

## オブジェクトのハッシュ

- SHA-1で計算: `cat-file -t <hash>` でタイプ確認
- `cat-file -p <hash>` で内容を表示

## 階層構造

```
commit ee79b43  →  tree 868c3cbd  →  blob b63544d (README.md)
commit ee79b43  →  tree ...       →  blob eb34d73c (a.txt)
```

## 学習した具体例

- `ee79b43` — commit オブジェクト（first greeting）
- `868c3cbd` — tree オブジェクト（初期コミットのルートディレクトリ）
- `b63544d` — blob オブジェクト（README.md の内容）
- `eb34d73c` — blob オブジェクト（a.txt の内容）
- `196e1df5` — tree オブジェクト（new_file.txt ステージ後のツリー）
- `9060e295` — commit オブジェクト（commit test）

## オブジェクトの保存場所

- `.git/objects/` 以下、2桁ハッシュ/残りでディレクトリ構成
- `.git/objects/pack/` にパック化されたオブジェクトも存在
- `git gc` でロースオブジェクトがパック化される

## オブジェクトのサイズ

- `git cat-file -s <hash>` — オブジェクトのサイズ（バイト数）を確認