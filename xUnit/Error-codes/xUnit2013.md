# xUnit2013


## 問題描述


* Level: Warning

* Error message: Do not use equality check to check for collection size.


## Why：提升可讀性


已有更好的方法，例如：Assert.Empty()、 Assert.NotEmpty()、 Assert.Single() 。


## 範例


```csharp
[Fact]
public void CreateHouseholdChore_ValidHouseholdChoreData_ReturnDataSize()
{
    List<HouseholdChoreInformation> testContainer = new();

    var methodResult = new NewHouseholdChore().CreateHouseholdChore("洗棉被", 60, testContainer);
            
    var resultJsonToObject = new List<HouseholdChoreInformation>();

    if (!string.IsNullOrEmpty(methodResult.jsonString))
    {
        resultJsonToObject = JsonSerializer.Deserialize<List<HouseholdChoreInformation>>
                                                                        (methodResult.jsonString);
    }

    Assert.Single(resultJsonToObject);  // xUnit2013: Assert.Equal(1, resultJsonToObject.Count);
}
```


## 參考資料

* xUnit2013
  * https://xunit.net/xunit.analyzers/rules/xUnit2013