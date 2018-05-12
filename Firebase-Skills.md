Firebase Skills

```c#
private TransactionResult AddScoreTransaction(MutableData mutableData)
{
    var debugMessage = "AddScore(): ";
    var datas = mutableData.Value as List<object>;

    var newPlayer = false;
    var newScoreMap = new Dictionary<string, object>();
    var score = (long) 0;

    if (datas == null)
    {
        // No current player data in the database
        datas = new List<object>();
        newPlayer = true;
        Debug.Log(debugMessage + "This is new user.");
    }
    else
    {
        object temp = null;
        foreach (var data in datas)
        {
            newScoreMap = data as Dictionary<string, object>;
            temp = data;
        }

        datas.Remove(temp);
    }

    // udpate player score

    // if player not existed in database
    score++;
    if (!newPlayer)
    {
        if (newScoreMap != null)
        {
            score += (long) newScoreMap["score"];
            newScoreMap["score"] = score;
        }

        Debug.LogError(debugMessage);
    }
    else
    {
        newScoreMap["email"] = EMAIL;
        newScoreMap["score"] = score;
        newScoreMap["status"] = "online";
    }

    datas.Add(newScoreMap);
    mutableData.Value = datas;
    return TransactionResult.Success(mutableData);
}
```

