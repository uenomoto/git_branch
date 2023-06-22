Git branch 確認テスト

もし main を切ってから別の人が marge して何かしら更新があった場合の挙動を確認します

main branch now

`git checkout -b dev_1`で dev_1 を作成そして初 push する

先に dev_1 が終わりプルリク作成して merge

`git checkout -b dev_2`で dev_2 を作成そして初 push する

次に dev＿2 を merge する

**だが先に dev_1 が main に marge されているため、先に main ブランチを取り込んでから marge する必要がある**

### 理由

その１:コンフリクトの解消

dev_1 が先に main に marge されたとき、その変更が dev_2 の作業と**コンフリクト**を起こす可能性がある

そのような場合、**dev_2 は最新の main ブランチの変更を取り込むことでこれらのコンフリクトを解消できる。**

その２:最新の状態でのテスト

dev_2 が最新の main ブランチの変更を取り込むことで、

main ブランチの最新の状態で自身の変更が機能することを確認できる

やり方

まずは必ず main に marge させたいブランチに移動すること！！(今回は `git checkout dev_2`で dev_2 ブランチに移動)

次に最新の main ブランチをプルする

`git pull origin main`

これにより、dev_2 ブランチは最新の main ブランチの内容を取り込むことができます。

それでもコンフリクトが生じた場合は、必ず手動で解消してから marge すること！

---

今私は dev_3 にいます。

---

今私は dev_4 にいます。
今私は dev_5 にいます。
