# pull-request-test

プルルクエストの使用を試す。
参考:[サル先生のGit入門](https://backlog.com/ja/git-tutorial/pull-request/04/)


## リポジトリの準備

- 新しいリポジトリを作成する（pull-request-test）
- リポジトリの中に以下のjsファイル（sort.js）を作成する
```javascript
var number = [19, 3, 81, 1, 24, 21];
console.log(number);
```
- リモートブランチにプッシュする


## 開発ブランチで修正

- 作業ブランチの作成
```
$ git check out -b add-sort-func
```
- ファイルを変更
```javascript
var sortNumber = function (number) {
  number.sort(function (a,b) {
    if (a == b) {
      return 0;
    }
    return a < b ? -1 : 1;
  });
};

var number = [19, 3, 81, 1, 24, 21];
sortNumber(number);
console.log(number);
```
- コミット
```
$ git add sort.js
$ git commit -m "Add function list sort"
```
- 変更したブランチをプッシュ
```
$ git push origin add-sort-function
```

## プルリクエストの作成

- githubページの対象リポジトリで「Compare & pull request」をクリック
![スクリーンショット 2020-06-29 22 02 45](https://user-images.githubusercontent.com/67271461/86009707-7e2baf00-ba55-11ea-928f-80cf1a1add7a.png)
- base:master → ターゲットブランチ（プルリクエストをマージする対象のブランチ）
- compare:add-sort-func → プルリクエストブランチ（マージしてもらうブランチ）
- Writeにリクエストの内容を入力し「Create pull request」をクリックしたら、プルリクエストが作成できる。
![スクリーンショット 2020-06-29 22 03 13](https://user-images.githubusercontent.com/67271461/86011338-8553bc80-ba57-11ea-8a8e-5b534dbdd4e4.png)

## レビューとマージ

- レビュー担当者は「Files chaged」タブから変更内容を確認
- 修正を望む箇所でプラスボタンをクリックし、修正の依頼ができる
![スクリーンショット 2020-06-29 22 06 11](https://user-images.githubusercontent.com/67271461/86011626-e4193600-ba57-11ea-8691-0469dbd5efa2.png)

- 修正の依頼は「Conversation」タブでも確認することができる

- レビュー内容に従い、ソースコードを修正する（==を===に）
- 再度コミットとプッシュを行う
```
$ git add sort.js
$ git commit -m "(==)fix to(===)"
$ git push origin add-sort-func
```
- github上で、プルリクエストに修正した旨を伝える
