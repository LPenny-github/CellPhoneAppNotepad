# `<figure>`


* `<figure>` 可放置圖片、影音或程式碼的標籤。

* `<figcaption>` 在 `<figure>` 中擔任解釋字詞的角色，但在每個 `<figure>` 中只能出現一次 `<figcaption>` 。


以下是 MDN 提供的範例：

```html
<figure>
    <img src="/media/cc0-images/elephant-660-480.jpg"
         alt="Elephant at sunset">
    <figcaption>An elephant at sunset</figcaption>
</figure>
```

```css
figure {
    border: thin #c0c0c0 solid;
    display: flex;
    flex-flow: column;
    padding: 5px;
    max-width: 220px;
    margin: auto;
}

img {
    max-width: 220px;
    max-height: 150px;
}

figcaption {
    background-color: #222;
    color: #fff;
    font: italic smaller sans-serif;
    padding: 3px;
    text-align: center;
}
```


## 參考資料

* `<figure>`: The Figure with Optional Caption element
  * https://developer.mozilla.org/en-US/docs/Web/HTML/Element/figure

* 4.4.12. The figure element
  * https://www.w3.org/TR/2021/SPSD-html52-20210128/grouping-content.html#the-figure-element

* 4.4.13. The figcaption element
  * https://www.w3.org/TR/2021/SPSD-html52-20210128/grouping-content.html#the-figcaption-element