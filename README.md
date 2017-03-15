# graphql-net-client
Very simple GraphQL client for .NET/C#

## Typed result
```cs
class GqlObj
{
    public string name { get; set; }
    public string id { get; set; }
}

var client = new GraphQLClient("https://mygraphql.endpoint");
var query = @"
    query($id: String) { 
        someObject(id: $id) {
            id
            name
        }
    }
";
var obj = client.Query(query, new { id = "123" }).Get<GqlObj>("someObject");
if (obj != null)
{
    Console.WriteLine(obj.name);
}
else
{
    Console.WriteLine("Null :(");
}
```

## Dynamic result
```cs
var client = new GraphQLClient("https://mygraphql.endpoint");
var query = @"
    query($id: String) { 
        someObject(id: $id) {
            id
            name
        }
    }
";
var obj = client.Query(query, new { id = "123" }).Get("someObject");
if (obj != null)
{
    Console.WriteLine((string)obj.name);
}
else
{
    Console.WriteLine("Null :(");
}
```
