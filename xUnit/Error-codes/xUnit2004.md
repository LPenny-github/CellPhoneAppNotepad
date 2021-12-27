# xUnit2004


## 問題描述


* Level: Warning

* Error message: Do not use equality check to test for boolean conditions.


## Why：提升可讀性


已有更好的方法，例如：Assert.True()、Assert.False() 。


## 範例


```csharp
[Fact]
public void CreateHouseholdChore_ValidHouseholdChoreData_ReturnTrue()
{
    List<HouseholdChoreInformation> testContainer = new();

    var result = new NewHouseholdChore().CreateHouseholdChore("洗棉被", 60, testContainer);

    Assert.True(result.valid); // xUnit2004: Assert.Equal(true, result.valid);
}
```


## 參考資料

* xUnit2004
  * https://xunit.net/xunit.analyzers/rules/xUnit2004