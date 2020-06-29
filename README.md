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
