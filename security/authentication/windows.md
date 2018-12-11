# Windows

{% hint style="info" %}
Not available in Community Edition.
{% endhint %}

To use Windows Authentication, you will need to [host Universal Dashboard in IIS](https://github.com/adamdriscoll/universal-dashboard-documentation/tree/15ca122d89e54271ad0661a8e75dd3cf33c0520c/security/running-dashboards/iis.md).

After configuring UD to run in IIS, you will need to [enable Windows Authentication on your site](https://docs.microsoft.com/en-us/aspnet/core/security/authentication/windowsauth?view=aspnetcore-2.2#iis-configuration).

Next, you need to ensure that your `web.config` file has `forwardWindowsAuthToken` set to true.

```text
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <!--
    Configure your application settings in appsettings.json. Learn more at http://go.microsoft.com/fwlink/?LinkId=786380
  -->
  <system.webServer>
    <handlers>
      <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />
    </handlers>
    <aspNetCore processPath=".\net472\universaldashboard.server.exe" arguments="" stdoutLogEnabled="true" stdoutLogFile="\\?\%home%\LogFiles\stdout" forwardWindowsAuthToken="true"  />
  </system.webServer>
</configuration>
```

The last step is to configure your dashboard to use Windows authentication. Specify a new authentication method with the `-Windows` switch parameter and pass it to `New-UDLoginPage`. Include the `-PassThru` parameter to avoid having the login page shown. You should now be able to login to your UD site as the current user.

```text
Start-UDDashboard -Content {
    $Auth = New-UDAuthenticationMethod -Windows
    $LoginPage = New-UDLoginPage -AuthenticationMethod @($Auth) -PassThru

    New-UDDashboard -Title "Line" -Content { 
        New-UDRow -Columns {
            New-UDColumn -Size 12 -Endpoint  {
                New-UDHeading -Text "Logged in as $user"
            }
        }
    } -LoginPage $LoginPage 
} -Wait -AllowHttpForLogin
```

