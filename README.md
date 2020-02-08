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
# メッセージの書き方
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

4. 開発ーーー開発完了ーーデバッグ・テスト  

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
ローカル：削除するブランチ以外のブランチで  
`git branch --delete foo`  
リモート：  
`git push --delete origin foo`  
https://qiita.com/iorionda/items/c7e0aca399371068a9b8

# 基本思想
feature同士が依存しない単位でブランチ・イシューを切る。  
ブランチAがブランチBを依存してしまうことが開発途中で分かった場合、  
1. ブランチBを一旦developにマージする
2. developをブランチAにマージする
3. ブランチAで開発再開。

# git stash
あるブランチの開発中に、別のブランチの手直しをしたくなった時には、git stashコマンドを使ってcommit前の変更を退避させる必要がある。そうしないと、他のブランチに切り替えた時に変更が失われることがあるから。    

例えば、feature/Aブランチの開発中にfeature/Bブランチに手を加えたくなったときは、  

`git stash save -u  # feature/Aブランチのcommit前の変更を退避する`  
`git checkout feature/B  # feature/Bブランチに入る`  
`...                     # feature/Bブランチで作業をする`  
`git checkout feature/A  # feature/Aブランチに戻る`  
`git stash pop      # feature/Aブランチの状態を復元する`  
というようにする。

>ここで、git stashコマンドに-uオプションをつけるのを忘れないこと。このオプションで、indexに登録前の(ie. untrackedな)変更も退避することを支持している。オプションをつけ忘れると、indexに登録されていない変更は失われるかもしれない。そして、そうやって失った変更は復元することができないので、もう一度書き直すしかなくなる。
