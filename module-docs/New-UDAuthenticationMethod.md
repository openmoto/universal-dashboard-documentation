---
external help file: PowerShellProTools.UniversalDashboard.dll-Help.xml
Module Name: UniversalDashboard
online version: 
schema: 2.0.0
---

# New-UDAuthenticationMethod

## SYNOPSIS
Adds an authentication method to a login page.

## SYNTAX

### Forms
```
New-UDAuthenticationMethod [-Endpoint <ScriptBlock>] [<CommonParameters>]
```

### OAuth
```
New-UDAuthenticationMethod [-AppId <String>] [-AppSecret <String>] [-Provider <OAuthProvider>]
 [<CommonParameters>]
```

## DESCRIPTION
Adds an authentication method to a login page. Use with New-UDLoginPage.

## EXAMPLES

### Example 1
```
PS C:\> New-UDAuthenticationMethod -Endpoint {
                    param([PSCredential]$Credential)
        
                    if ($Credential.UserName -eq "Adam") {
                        New-UDAuthenticationResult -UserName "Adam" -Success
                    } else {
                        New-UDAuthenticationResult -ErrorMessage "You're not Adam!!"
                    }
                }
```

Validates that the user is Adam. If it isn't it returns an error.

### Example 2
```
PS C:\> $AuthenticationMethod = New-UDAuthenticationMethod -AppId 123-444 -AppSecret 'superSecret' -Provider Microsoft
PS C:\> $LoginPage = New-UDLoginPage -AuthenticationMethod $AuthenticationMethod
```

Users Microsoft as a 3rd party authentication provider.

## PARAMETERS

### -AppId
The AppId for OAuth authentication.

```yaml
Type: String
Parameter Sets: OAuth
Aliases: ConsumerKey, ClientId, ApplicationId

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AppSecret
The AppSecret for OAuth authentication.

```yaml
Type: String
Parameter Sets: OAuth
Aliases: ConsumerSecret, ClientSecret, ApplicationPassword

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Endpoint
An endpoint used to validate a user's credentials.

```yaml
Type: ScriptBlock
Parameter Sets: Forms
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Provider
The OAuth provider to use. 

```yaml
Type: OAuthProvider
Parameter Sets: OAuth
Aliases: 
Accepted values: Facebook, Twitter, Google, Microsoft

Required: False
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

