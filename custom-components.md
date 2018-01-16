## Custom Components

Required Version: 1.4.0

The New-UDElement enables you to create custom components for Universal Dashboard. Components can be created with PowerShell or with JavaScript. Custom Components can ship as modules or simple PS1 scripts. 

### PowerShell-Based Components 

The New-UDElement cmdlet can be used to create HTML tags that define the markdown for a custom component. New-UDElements can be nested and attributes can be added. 

A simple custom component may be defined such as this.

```
New-UDElement -Tag "a" -Attributes @{
    href = ""
    target = "_self"
} -Content "A link"
```

This custom component would define a React class in JavaScript that would eventually translate into an HTML link with the following markup. 

```
<a href="
```


