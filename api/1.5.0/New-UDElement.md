---
external help file: PowerShellProTools.UniversalDashboard.dll-Help.xml
Module Name: UniversalDashboard
online version: 
schema: 2.0.0
---

# New-UDElement

## SYNOPSIS
{{Fill in the Synopsis}}

## SYNTAX

### HTML
```
New-UDElement -Tag <String> [-Attributes <Hashtable>] [-Content <ScriptBlock>] [-Endpoint <ScriptBlock>]
 [-AutoRefresh] [-RefreshInterval <Int32>] [-DebugEndpoint] [-Id <String>] [<CommonParameters>]
```

### JS
```
New-UDElement -JavaScriptPath <String> [-ComponentName <String>] -ModuleName <String> [-Properties <Hashtable>]
 [-Endpoint <ScriptBlock>] [-AutoRefresh] [-RefreshInterval <Int32>] [-DebugEndpoint] [-Id <String>]
 [<CommonParameters>]
```

## DESCRIPTION
{{Fill in the Description}}

## EXAMPLES

### Example 1
```
PS C:\> {{ Add example code here }}
```

{{ Add example description here }}

## PARAMETERS

### -Attributes
{{Fill Attributes Description}}

```yaml
Type: Hashtable
Parameter Sets: HTML
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AutoRefresh
{{Fill AutoRefresh Description}}

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComponentName
{{Fill ComponentName Description}}

```yaml
Type: String
Parameter Sets: JS
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Content
{{Fill Content Description}}

```yaml
Type: ScriptBlock
Parameter Sets: HTML
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DebugEndpoint
{{Fill DebugEndpoint Description}}

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Endpoint
{{Fill Endpoint Description}}

```yaml
Type: ScriptBlock
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id
{{Fill Id Description}}

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -JavaScriptPath
{{Fill JavaScriptPath Description}}

```yaml
Type: String
Parameter Sets: JS
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModuleName
{{Fill ModuleName Description}}

```yaml
Type: String
Parameter Sets: JS
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Properties
{{Fill Properties Description}}

```yaml
Type: Hashtable
Parameter Sets: JS
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RefreshInterval
{{Fill RefreshInterval Description}}

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Tag
{{Fill Tag Description}}

```yaml
Type: String
Parameter Sets: HTML
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

