# Buttons

Buttons are used for basic interactions from users. You can add event handlers to buttons to perform actions when they are clicked. 

## Raised

![](./images/raised-button.png)

```powershell
New-UDButton -Text "Button" 
New-UDButton -Text "Button" -Icon cloud -IconAlignment left
New-UDButton -Text "Button" -Icon cloud -IconAlignment right
```

## Floating

![](./images/floating-button.png)

```powershell
New-UDButton -Floating -Icon plus
```

## OnClick Event Handler

A ScriptBlock that is invoked when the button is clicked.

```powershell
$MyVariable = "Some Text"
New-UDButton -Text "Click me!" -OnClick {
    Show-UDToast -Message "Clicked!"
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

