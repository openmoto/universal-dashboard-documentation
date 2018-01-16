# Themes

Required Version: 1.4.0 or later

Themes are used to define colors for a dashboard without having to pass colors to each component. Themes can easily be defined as a hashtable and passed into `New-UDTheme`. Component and property names can be defined in a theme as well as CSS classes and attributes. 

## Creating a basic theme

To create a basic theme, use `New-UDTheme`. Values for any of the attributes can be any valid CSS definition. 

```
$Theme = New-UDTheme -Name "Basic" -Definition @{
  UDDashboard = @{
      BackgroundColor = "rgb(255,255,255)"
      FontColor = "rgb(0, 0, 0)"
  }
}
```
Themes can then be passed into the `-Theme` parameter of `New-UDDashboard`. 

## Finding pre-defined themes

Universal Dashboard includes pre-defined themes. These themes can be found using the `Get-UDTheme` cmdlet. You can use these themes as parents to other themes. 

## Creating child themes

You can create child themes of pre-existing themes returned by `Get-UDTheme`. To create a child theme, pass the name of the parent theme to the `Parent` parameter of `New-UDTheme`. 

```
$Theme = New-UDTheme -Name "Basic" -Definition @{
  UDDashboard = @{
      BackgroundColor = "rgb(255,255,255)"
      FontColor = "rgb(0, 0, 0)"
  }
} -Parent "Azure" 
```

When defining a child theme, any properties that are defined in the child will override the parent. Any properties that are not overriden, will remain the same as the parent. 

## Available Properties

Themes support a basic set of defined properties. These properties are translated to CSS classes and attributes for you. 



## Using Raw CSS 

Themes can use raw CCS



