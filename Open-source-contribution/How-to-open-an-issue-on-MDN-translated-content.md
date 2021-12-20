# How to open an issue on MDN translated-content


## 問題

在 MDN <a href="https://developer.mozilla.org/zh-TW/docs/Web/Guide/HTML/Content_categories#%E6%A8%99%E9%A1%8C%E5%9E%8B%E5%85%A7%E5%AE%B9%EF%BC%88heading_content%EF%BC%89">標題型內容（Heading content）</a> 的文件上，發現有重複並且為簡體中文的翻譯，希望可以去除掉重複的部分。


## 準備

* 閱讀 MDN 在 GitHub 上對於翻譯中文的說明（必讀）
  * https://github.com/mdn/translated-content/blob/main/docs/zh-tw/translation-guide.md#針對mdn翻譯內容的一般指導原則

* 如何正確的參與開放原始碼專案協作（Will保哥 直播影片）
  * https://www.facebook.com/watch/live/?ref=watch_permalink&v=134512168711909

* 如何為開源做貢獻？
  * https://opensource.guide/zh-hant/how-to-contribute/#提交貢獻前應做的檢查清單


## 決定參與方式

因為是第一次，保險起見，決定開 issue。

## 執行

1. 登入 GitHub 。
1. 開 issue，選擇 `Content bug` 或是 `New content suggestion` 。
   * 我選擇 `Content bug` ，按 `Get started`。

1. 按照提示填入標題與內容。
   * 如果不知道怎麼填寫，可以參考他人。
     * 在 issue 首頁，使用 label 下拉選單，選擇 `|10n-zh` 。

   ```markdown
   Content bug: <TITLE OF PROBLEM>


   ## What page(s) did you find the problem on?

   <!-- include the URL or URLs where you found the problem. If it is a widespread problem over many pages, just give us a couple of example URLs rather than the whole lot  -->

   ## Specific page section or heading?

   <!-- include the specific heading underneath which the problem can be found, if relevant, to help us locate the problem more easily  -->

   ## What is the problem?

   <!-- include a description of the problem — is some text misspelt, or inaccurate? Does an example not work? Is the document missing some information? Is something just weird?  -->

   ## What did you expect to see?

   <!-- If you have an idea of what the solution to your problem is, please provide details here. If you don't know, then that's OK   -->

   ## Did you test this? If so, how?

   <!-- Please provide any steps you took to test the problem, if appropriate  -->

   ```


1. 填寫第一版


    ```markdown

    Issue with "Heading content": repetitive contents (zh-TW)


    ## What page(s) did you find the problem on?

    MDN URL: https://developer.mozilla.org/zh-TW/docs/Web/Guide/HTML/Content_categories#流內容（flow_content）

    ## Specific page section or heading?

    標題型內容（Heading content）

    ## What is the problem?

    多了一行重複的簡體中文翻譯內文。

    > 標題型內容（Heading content）
    >
    > 标题内容 定义了分节的标题，而这个分节可能由一个明确的分节内容元素直接标记，也可能由标题本身隐式地定义。
    >
    > 標題型內容定義了章節的標題，不論該章節由明確的章節型內容元素標記、抑或由標題本身隱式定義。

    ## What did you expect to see?

    > 標題型內容（Heading content）
    >
    > 標題型內容定義了章節的標題，不論該章節由明確的章節型內容元素標記、抑或由標題本身隱式定義。

    ## Did you test this? If so, how?

    No.
    ```


1. 修改後第二版

    * 詢問 Mentor/有經驗者/英文好的人 自己的表達是否清楚，修正後產生第二版。
        * repetitive --> duplicated
        * 增加英文敘述（本以為是懂中文的人來審核 issue，卻忘記分派的人可能看不懂中文）


    ```markdown
    Issue with "標題型內容（Heading content）": duplicated contents (zh-TW)


    ## What page(s) did you find the problem on?

    MDN URL: https://developer.mozilla.org/zh-TW/docs/Web/Guide/HTML/Content_categories#流內容（flow_content）

    ## Specific page section or heading?

    [標題型內容（Heading content）](https://developer.mozilla.org/zh-TW/docs/Web/Guide/HTML/Content_categories#%E6%A8%99%E9%A1%8C%E5%9E%8B%E5%85%A7%E5%AE%B9%EF%BC%88heading_content%EF%BC%89)

    ## What is the problem?

    多了一行重複的簡體中文翻譯內文。

    The first paragraph under “標題型內容（Heading content）” is unnecessarily duplicated in both simplified Chinese and traditional Chinese.

    > 標題型內容（Heading content）
    >
    > 标题内容 定义了分节的标题，而这个分节可能由一个明确的分节内容元素直接标记，也可能由标题本身隐式地定义。
    > 
    > 標題型內容定義了章節的標題，不論該章節由明確的章節型內容元素標記、抑或由標題本身隱式定義。

    ## What did you expect to see?

    Remove the paragraph in simplified Chinese; keep the paragraph in traditional Chinese (zh-TW).

    > 標題型內容（Heading content）
    >
    > 標題型內容定義了章節的標題，不論該章節由明確的章節型內容元素標記、抑或由標題本身隱式定義。

    ## Did you test this? If so, how?
 
    No.

    ```


## 靜候結果


😆


## 參考資料


* 閱讀 MDN 在 GitHub 上對於翻譯中文的說明（必讀）
  * https://github.com/mdn/translated-content/blob/main/docs/zh-tw/translation-guide.md#針對mdn翻譯內容的一般指導原則

* 如何正確的參與開放原始碼專案協作（Will保哥 直播影片）
  * https://www.facebook.com/watch/live/?ref=watch_permalink&v=134512168711909

* 如何為開源做貢獻？
  * https://opensource.guide/zh-hant/how-to-contribute/#提交貢獻前應做的檢查清單

* 標題型內容（Heading content）
  * https://developer.mozilla.org/zh-TW/docs/Web/Guide/HTML/Content_categories#%E6%A8%99%E9%A1%8C%E5%9E%8B%E5%85%A7%E5%AE%B9%EF%BC%88heading_content%EF%BC%89