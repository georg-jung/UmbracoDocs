---
versionFrom: 10.0.0
meta.Title: "Umbraco Connection Strings Settings"
meta.Description: "Information on the connection strings settings section"
---

# Connection strings settings

The connection strings settings section contains the connection string to the database Umbraco will connect to. This section is similar to what is used by default in .NET Core. The important thing is that the key for the connection string Umbraco will use is `"umbracoDbDSN"`. It is also important to know that this section is outside the `Umbraco.CMS` section, and is therefore in the root of the config.

An connection strings config can look like this:

```json
{
  "ConnectionStrings": {
    "umbracoDbDSN": "Data Source=|DataDirectory|/Umbraco.sqlite.db;Cache=Private;Foreign Keys=True;Pooling=True",
    "umbracoDbDSN_ProviderName": "Microsoft.Data.SQLite"
  }
}
```

:::note
We recommend using private cache for SQLite. You can read more on why shared cache is discouraged in [the official SQLite documentation](https://sqlite.org/sharedcache.html). 
:::

The connection string used here is an SQLite connection string, that will connect to a data in the file `Umbraco.sqlite.db`  located in `/umbraco/Data` .

Umbraco currently supports using either a Microsoft SQL Server, or a SQLite database, both of these will look different for more information about the specific connection strings see:

* [SQL Server 2019 connection strings](https://www.connectionstrings.com/sql-server-2019/)
* [SQLite connection strings](https://www.connectionstrings.com/sqlite/)

## Provider name
Because Umbraco cannot determine the provider name from the connection string in all cases. To get the provider name Umbraco use the [convention suggested by Microsoft](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-5.0#connection-string-prefixes-1) to specify the provider name as a post fix of the connection string name.

