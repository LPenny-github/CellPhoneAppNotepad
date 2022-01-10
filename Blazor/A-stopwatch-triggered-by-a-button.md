# How to make a stopwatch triggered by a button


## 目標


在 Blazor 頁面上製做一個按鈕，按一下計時，再按一下停止計時並顯示秒數。


## 準備


參考先前筆記 [Stopwatch 計時](https://github.com/LPenny-github/BeginnerNotepad/blob/main/瞧我這記性/Stopwatch計時.md#stopwatch-計時)


## 製做


* Stopwatch.razor

```csharp
@page "/kmgstopwatch"
@using System.Diagnostics

<PageTitle>KMGstopwatch</PageTitle>

<p>時間為： @elapsedTime </p>

<button class="btn btn-primary" @onclick="CheckStatus">@buttonLabel</button>

@code {
    string elapsedTime ;
    Stopwatch stopWatch = new Stopwatch();
    bool hasStarted = false;
    string buttonLabel = "開始計時";

    void CheckStatus()
    {
        if (!hasStarted)
        {
            StartTimer();
            buttonLabel = "停止計時";
        }
        else
        {
            StopTimer();
            buttonLabel = "開始計時";
        }
        hasStarted = !hasStarted;
    }

    void StartTimer()
    {
        elapsedTime = "";
        stopWatch.Restart();
    }

    void StopTimer()
    {
        stopWatch.Stop(); 

        TimeSpan ts = stopWatch.Elapsed;
        elapsedTime = String.Format("{0:00}:{1:00}:{2:00}",
                                    ts.Hours, ts.Minutes, ts.Seconds);
    }
}
```


## 驗證


1. `ctrl` + `S` ：存檔

1. `ctrl` + `F5` ：跑出網頁（或使用 PoerShell 指令 `dotnet watch`）
   * 例如：https://localhost:0000

1. 在該網址加上 @page ， 按下 `enter`
   * 例如：https://localhost:0000/kmgstopwatch

1. 操作按鈕、手動測試