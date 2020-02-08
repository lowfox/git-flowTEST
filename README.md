# git-flowTEST
git-flowと、git pull ,push,stashの挙動の確認

# ブランチ構成
- master
リリース専用
- develop
masterから派生したブランチ、featureブランチの派生元
- feature/#issueID
developから派生した機能開発全般のブランチ
- hotifix/#issueID
masterから派生したバグ修正用のブランチ
#メッセージの書き方
https://qiita.com/itosho/items/9565c6ad2ffc24c09364

題名↓
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

Add:read.md追加

issue:#1

read.mdの追加

# 使い方  

例：機能追加  

1. issueを作成  

2. ローカルdevelopを最新にする  
`git pull origin develop`  

3. developからfeatブランチを作成  
`git branch feat/#1`  
`git checkout feat/#1`  

4. 開発ーーー開発完了  

5. コミット&　メッセージ  
`git add .`  
`git commit`  

6. 同じブランチ名でリモートにプッシュ  
`git push origin feat/#1`  

7. githubにてリモートのfeat/#1からdevelopにプルリクエスト  
githubにてdevelopにマージ  
developが最新状態になった。  

8. ローカルdevelopを最新状態に更新  
`git pull origin develop`  

9. ローカル、リモートのfeat/#1ブランチを削除



