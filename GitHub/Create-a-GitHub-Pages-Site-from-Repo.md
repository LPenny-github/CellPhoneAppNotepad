# Create a GitHub Pages Site from Repo


## 開啟

1. 登入 GitHub 。
1. 找到該 repo 。
1. `Settings` > 左側欄 `Pages` 。
1. 在 `Source` 選擇分支 與 目標資料夾或檔案（我選 `root` ），按下 `Save` 。
1. 非必要： 在 `Theme Chooser` 選擇 網頁主題。
   * 若有選則 網頁主題，系統會自動幫你在該 repo 中加入 .yml 檔案，並且幫你自動 commit， commit message 如：
     ```txt
     Set theme jekyll-theme-midnight
     ```

* 成功開啟 GitHub Pages 後上方會出現該 repo 的網址，例如：

  ```txt
   Your site is published at https: //{your github account}.github.io/{your repo name}/
  ```


## 瀏覽

從 (1)網址登入 或 (2)設定頁面獲取網址 或 (3)：

1. 登入 GitHub 。
1. 找到該 repo 。
1. 點擊 右側欄 `Environments` 或是 `github-pages` 。
   * 如果從來沒有開啟 Pages 功能，不會顯示此區塊。
   * 如果有開過 Pages 功能，就會顯示此區塊。
1. 點擊 右側欄 `View deployment` 可瀏覽網頁。
   * 若開過 Pages 功能但後來關閉，點擊 `View deployment` 後會出現 404。


## 關閉

在 `Source` 選擇分支 `None`，按下 `Save` 。
