# Buttons

Buttons are used for basic interactions from users. You can add event handlers to buttons to perform actions when they are clicked. 

## Creating a Basic Button 

```powershell
New-UDButton -Text "Click me!" -OnClick {
    Show-UDToast -Message 'You clicked'
}
```

## Passing Variables to a Button OnClick Handler

```powershell
$MyVariable = "Some Text"
New-UDButton -Text "Click me!" -OnClick (
    New-UDEndpoint -Endpoint {
        Show-UDToast -Message $ArgumentList[0]
    } -ArgumentList @($MyVariable)
)
```

