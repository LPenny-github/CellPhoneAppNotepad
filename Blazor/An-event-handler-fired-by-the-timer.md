# How to build an event handler fired by the timer


## 目標


把之前 "在 Blazor 頁面上製做一個按鈕，按一下計時，再按一下停止計時並顯示秒數。" 參見：

[How to make a stopwatch triggered by a button](https://github.com/LPenny-github/CellPhoneAppNotepad/blob/main/Blazor/A-stopwatch-triggered-by-a-button.md#how-to-make-a-stopwatch-triggered-by-a-button)

改成每增加一秒鐘即顯示於頁面。


## 準備


閱讀官方文件的範例：
 
* Timer 類別
  * https://docs.microsoft.com/zh-tw/dotnet/api/system.timers.timer?view=net-6.0#examples


## 製作


在原本的程式碼中，增加一個倒數計時器，設定為一秒，時間到時則觸發事件，並通知網頁更新。


```csharp
@page "/kmgtimer"
@using System.Diagnostics
@using System.Timers

<PageTitle>KMGtimer</PageTitle>

<p>時間為： @elapsedTime </p>

<button class="btn btn-primary" @onclick="CheckStatus">@buttonLabel</button>


@code {
    string elapsedTime = "00:00:00";
    Stopwatch stopWatch = new Stopwatch();
    bool hasStarted = false;
    string buttonLabel = "開始計時";

    void CheckStatus()
    {
        if (!hasStarted)
        {
            StartTimer();
            SetEventAlert();
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
        elapsedTime = "00:00:01";
        stopWatch.Restart();
    }
    Timer aTimer;

    void SetEventAlert()
    {
        aTimer = new System.Timers.Timer(1000); 
        aTimer.Elapsed += OnTimedEvent;
        aTimer.AutoReset = true;
        aTimer.Enabled = true;
    }

    void OnTimedEvent(Object source, ElapsedEventArgs e)
    {
        stopWatch.Stop();

        TimeSpan ts = stopWatch.Elapsed.Add(new TimeSpan(0,0,1));

        elapsedTime = String.Format("{0:00}:{1:00}:{2:00}",
        ts.Hours, ts.Minutes, ts.Seconds);

        stopWatch.Start();

        InvokeAsync(StateHasChanged);
    }
    void StopTimer()
    {
        aTimer.Stop();
        aTimer.Dispose();
        stopWatch.Stop();        
    }

}
```


## 驗證


1. `ctrl` + `S` ：存檔

1. `ctrl` + `F5` ：跑出網頁（或使用 PoerShell 指令 `dotnet watch`）
   * 例如：https://localhost:0000

1. 在該網址加上 @page ， 按下 `enter`
   * 例如：https://localhost:0000/kmgtimer

1. 操作按鈕，觀察是否每秒更新時間於頁面
