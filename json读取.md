```c#
public static string Readjson(string key)
{
    string jsonfile = "D:\\1.vscode\\c#\\temp\\name test.json";//JSON文件路径
    System.IO.StreamReader file = System.IO.File.OpenText(jsonfile);
    JsonTextReader reader = new JsonTextReader(file);
    JObject o = (JObject)JToken.ReadFrom(reader);
    var value = o[key].ToString();
    return value;
}
```

