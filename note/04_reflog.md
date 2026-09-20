# Git Reflog

## 概要

- `.git/logs/HEAD` にHEADの更新履歴を記録
- `git reflog` で読みやすい形式で表示
- ローカルのみで保持（リモートに同期されない）

## 書式

```
<commit_hash> HEAD@{<index>}: <action>: <message>
```

## 具体例

```
ee79b43 HEAD@{0}: commit: first greeting
fbb6f3c HEAD@{1}: clone: from https://github.com/hsmtkk/learn-git-internal.git
```

## 使い道

- 間違ったコミットを取り消す（reset）
- 紛失したコミットを復元
- HEADがどう移動したかを追跡

## 注意点

- reflogは一定期間（通常90日）で期限切れ
- gc（garbage collection）で古いエントリが削除される