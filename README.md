Git branch 確認テスト

もし main を切ってから別の人が marge して何かしら更新があった場合の挙動を確認します

main branch now

`git checkout -b dev_1`で dev_1 を作成そして初 push する

先に dev_1 が終わりプルリク作成して merge

`git checkout -b dev_2`で dev_2 を作成そして初 push する

次に dev＿2 を merge する

**だが先に dev_1 が main に marge されているため、先に dev_2 に main ブランチを取り込んでから marge する必要がある**

### 理由

その１:コンフリクトの解消

dev_1 が先に main に marge されたとき、その変更が dev_2 の作業と**コンフリクト**を起こす可能性がある

そのような場合、**dev_2 は最新の main ブランチの変更を取り込むことでこれらのコンフリクトを解消できる。**

その２:最新の状態でのテスト

dev_2 が最新の main ブランチの変更を取り込むことで、

main ブランチの最新の状態で自身の変更が機能することを確認できる

やり方

先に main はプルして最新状態にすること

まずは必ず main に marge させたいブランチに移動すること！！(今回は `git checkout dev_2`で dev_2 ブランチに移動)

次に最新の main ブランチをマージする

`git merge main`

これにより、dev_2 ブランチは最新の main ブランチの内容を取り込むことができます。

それでもコンフリクトが生じた場合は、必ず手動で解消してから marge すること！

**競合を起こさない事！** プルリクが面倒になる

### 今回は別々でマージし開発ブランチで最新の main せずに merge してみます

dev_8 でコメントしています

dev_8 を main マージし main を最新状態(dev_8 を取り込んでる状態)にせずにそのまま dev_9 をマージしようとプルリクを出すと。。。

やはりこうなる

**Can’t automatically merge. Don’t worry, you can still create the pull request.**

marge しようとしている dev_9 に main の最新状態(dev_8 を取り込んでる状態)を marge し更新してみる

`git merge main`: 必ず main をマージしたい開発ブランチで行う

dev_9 に main の最新状態を marge し更新した結果

```
git merge main
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

自動マージに失敗手動でコンフリクト解消。今は少ないから簡単だけどコード量が多くなると・・・・

それからコンフリクトが解消したら`git add`コマンドで解決したファイルをステージに上げ、

`git commit`でマージコミットを作成します。

そうすると main の最新状態になる！

そしてプルリクも出せるようになる！！

# confirm ブランチと matome ブランチで理解度を確認

わざと別のブランチでまとめを書いて理解しているか確認します。

1. 同じ main の状態から 2 つのブランチを切ります

2. confirm ブランチで作業(今書いている)します

3. 作業が終わり、今回は先に matome ブランチを main とマージします！なのでここから matome ブランチに移動します

4. 今いるブランチの push 忘れずに！
