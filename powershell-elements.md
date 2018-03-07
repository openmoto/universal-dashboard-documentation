# PowerShell Elements

## Static Elements

The `New-UDElement` cmdlet can be used to create HTML tags that define the markdown for a custom component. `New-UDElement` can be nested and attributes can be added.

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
New-UDElement -Tag "div" -Attributes @{ className = "determinate"; style=@{width = "70%"}
}
```

For some examples of custom components, visit [GitHub](https://github.com/ironmansoftware/ud-material-design/blob/master/UniversalDashboard.MaterialDesign.psm1).

## Dynamic Elements

All elements created with `New-UDElement` can be managed within any endpoint or event handler. In order to manage a component you need to specify an Id. 

```
New-UDElement -Tag span -Id "targetSpan" -Content { "My Span" }
```

The above span could now be managed within any endpoint. You can use the following cmdlets to get data, update elements, add children or remove the element entirely. 

### Getting data from an element 

To get data from an element, use the `Get-UDElement` cmdlet to return the state of the element. You will receive the attributes and content of that element. The content may be another element or a string. 

In any endpoint, simply call `Get-UDElement` with the `-Id` parameter. 

```
New-UDCounter -Title "Value of text box" -AutoRefresh -Endpoint {
    (Get-UDElement -Id txtNumber).Attributes["value"]
}
```

### Setting data on an element 

From any endpoint, you can call `Set-UDElement` to update the attributes and content of an element. You need to specify the Id and the values you would like to update. 

```
Set-UDElement -Id "txtName" -Attributes @{
    width = '100px'
}
```

The above call sets the width of the txtName to 100 pixels. 