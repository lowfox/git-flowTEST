# git-flowTEST
git-flowと、git pull ,push,stashの挙動の確認

# COMMITメッセージの書き方
https://qiita.com/itosho/items/9565c6ad2ffc24c09364
- fix：バグ修正
- hotfix：クリティカルなバグ修正
- add：新規（ファイル）機能追加
- update：機能修正（バグではない）
- change：仕様変更
- clean：整理（リファクタリング等）
- disable：無効化（コメントアウト等）
- remove：削除（ファイル）
- upgrade：バージョンアップ
- revert：変更取り消し

# 使いかた

例：機能追加
issueの作成

ローカルdevelopにてリモートと合わせる(最新にする)
``` git pull origin develop ```

ローカルdevelopからfeat/issueIDでブランチ作成
``` git branch feat/#1 ```

最新のリモートdevolopにて開発するためpull
```git pull origin develop```

開発ーーー開発完了

同じブランチ名でpush
```git push origin feat/#1```
これでリモートに同じブランチが作成される

githubにてdevelopにマージする
developブランチが新しくなる

ローカルdevelopを最新にする
```git pull origin develop```
