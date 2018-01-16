## Custom Components

Required Version: 1.4.0

The New-UDElement enables you to create custom components for Universal Dashboard. Components can be created with PowerShell or with JavaScript. Custom Components can ship as modules or simple PS1 scripts. 

### PowerShell-Based Components 

The New-UDElement cmdlet can be used to create HTML tags that define the markdown for a custom component. New-UDElements can be nested and attributes can be added. 

A simple custom component may be defined such as this.

```
New-UDElement -Tag "a" -Attributes @{
    href = "https://www.poshud.com"
    target = "_self"
} -Content "Poshud"
```

This custom component would define a React class in JavaScript that would eventually translate into an HTML link with the following markup. 

```
<a href="https://www.poshud.com" target="_self">Poshud</a>
```

The `Content` parameter can define text as well as nested elements. For example, if you wanted to define a [Materialize Preloader](http://materializecss.com/preloader.html), you would need to define the following HTMl.

```
<div class="progress">
   <div class="determinate" style="width: 70%"></div>
</div>
```

To define the same component using `New-UDElement`, you could use the following script. 

```
New-UDElement -Tag "div" -Attributes @{ className = "progress" } -Content {
   New-UDElement -Attributes @{ className = "determinate"; style=@{width = "70%"}
}
```

For some examples of custom components, visit [GitHub](https://github.com/ironmansoftware/ud-material-design/blob/master/UniversalDashboard.MaterialDesign.psm1).

