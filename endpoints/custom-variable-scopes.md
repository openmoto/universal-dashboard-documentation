# Custom Variable Scopes

Required Version: 1.6.0 or later

Universal Dashboard exposes two custom variable scopes using custom providers. These providers allow you to store your variables in scopes that make sense for a web application. The cache scope is used to store variables that can be used within any endpoint inside a dashboard. The session scope is used to store variables that can be used for a single user's session of the dashboard. 

## Cache Scope 

Cache scope is used to store a variable that will be available in any endpoint. Cache scope is useful for storing data that make be shown in more than one control or may be time consuming to look up. This could be helpful for querying machine performance counters, Active Directory or Azure. 

### Defining Cache Variables 

Just like any other scope, cache variables are defined with a prefix and a colon separator. 

```powershell
$Cache:Computers = Get-ADComputer
```

