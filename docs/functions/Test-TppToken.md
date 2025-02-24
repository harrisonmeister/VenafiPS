# Test-TppToken

## SYNOPSIS
Test if a Tpp token is valid

## SYNTAX

### Session (Default)
```
Test-TppToken [-GrantDetail] [-VenafiSession <VenafiSession>] [<CommonParameters>]
```

### AccessToken
```
Test-TppToken -AuthServer <String> -AccessToken <PSCredential> [-GrantDetail] [<CommonParameters>]
```

### TppToken
```
Test-TppToken -TppToken <PSObject> [-GrantDetail] [<CommonParameters>]
```

## DESCRIPTION
Use the TPP API call 'Authorize/Verify' to test if the current token is valid.

## EXAMPLES

### EXAMPLE 1
```
Test-TppToken
```

Verify that accesstoken stored in $VenafiSession object is valid.

### EXAMPLE 2
```
$TppToken | Test-TppToken
```

Verify that token object from pipeline is valid.
Can be used to validate directly object from New-TppToken.

### EXAMPLE 3
```
Test-TppToken -AuthServer 'mytppserver.example.com' -AccessToken $cred
```

Verify that PsCredential object containing accesstoken is valid.

### EXAMPLE 4
```
Test-TppToken -GrantDetail
```

Verify that accesstoken stored in $VenafiSession object is valid and return PsCustomObject as output with details.

## PARAMETERS

### -AuthServer
Auth server or url, venafi.company.com or https://venafi.company.com.
If just the server name is provided, https:// will be appended.

```yaml
Type: String
Parameter Sets: AccessToken
Aliases: Server

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AccessToken
Access token retrieved outside this module. 
Provide a credential object with the access token as the password.

```yaml
Type: PSCredential
Parameter Sets: AccessToken
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -TppToken
Token object obtained from New-TppToken

```yaml
Type: PSObject
Parameter Sets: TppToken
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -GrantDetail
Provides detailed info about the token object from the TPP server response as an output.
PSCustomObject with the following properties:
    AuthUrl
    AccessToken
    RefreshToken
    Scope
    Identity
    TokenType
    ClientId
    Expires

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -VenafiSession
Session object created from New-VenafiSession method. 
The value defaults to the script session object $VenafiSession.

```yaml
Type: VenafiSession
Parameter Sets: Session
Aliases:

Required: False
Position: Named
Default value: $script:VenafiSession
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### Accesstoken
## OUTPUTS

### Boolean (default). PSCustomObject (GrantDetail). Throws error if a 400 status is returned.
## NOTES

## RELATED LINKS

[http://VenafiPS.readthedocs.io/en/latest/functions/Test-TppToken/](http://VenafiPS.readthedocs.io/en/latest/functions/Test-TppToken/)

[https://github.com/gdbarron/VenafiPS/blob/main/VenafiPS/Code/Public/Test-TppToken.ps1](https://github.com/gdbarron/VenafiPS/blob/main/VenafiPS/Code/Public/Test-TppToken.ps1)

[https://docs.venafi.com/Docs/20.4SDK/TopNav/Content/SDK/AuthSDK/r-SDKa-GET-Authorize-Verify.php?tocpath=Auth%20SDK%20reference%20for%20token%20management%7C_____13](https://docs.venafi.com/Docs/20.4SDK/TopNav/Content/SDK/AuthSDK/r-SDKa-GET-Authorize-Verify.php?tocpath=Auth%20SDK%20reference%20for%20token%20management%7C_____13)

