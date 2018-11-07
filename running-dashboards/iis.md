# IIS

To run a dashboard in IIS, you will need to configure an application pool and website just as you would with any other IIS web application. IIS requires that the [.NET Core Runtime and Hosting Bundle ](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-2.1.5-windows-hosting-bundle-installer)is installed to run Universal Dashboard. Once installed, you will have to configure your website for Universal Dashboard.

Note: You will need to enable the WebSocket Protocol feature of IIS in order to use features of Universal Dashboard. Event handlers, such as OnClick, require this feature. The following cmdlets take advantage of WebSockets. 

* Add-UDElement
* Sync-UDElement
* Clear-UDElement
* Remove-UDElement
* Invoke-UDRedirect
* Show-UDModal
* Hide-UDModal
* AutoRefresh on Start-UDDashboard

## Configuring a site for Universal Dashboard

For this example we will look at the Default Web Site. In IIS Manager, right click on your Web Site and click Explore.

![](../.gitbook/assets/explore-iis.png)

Copy the entire contents of the UniversalDashboard module to the wwwroot of the Default Web Site.

![](../.gitbook/assets/copy-iis.png)

Create a `dashboard.ps1` file and place it in the `wwwroot` folder. The dashboard should contain a dashboard definition and a call to `Start-UDDashboard` with the `-Wait` parameter specified.

```text
 Start-UDDashboard -Wait -Dashboard (
    New-UDDashboard -Title "Hello, IIS" -Content {
        New-UDCard -Title "Hello, IIS"
    }
)
```

Navigate to the IIS website in your browser and you should see Universal Dashboard running.

![](../.gitbook/assets/iis-running.png)

## Licensing

The license should be named license.lic and placed in the `net451` folder within `wwwroot`. This will ensure that the license is persistent throughout restarts.

![](../.gitbook/assets/iis-license.bin)

