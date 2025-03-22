---
date: "2025-03-22T07:21:26.839+01:00"
title: "Encryption"
description: "Handle sensitive input"
dg-publish: true
---

# Encrypt or input data

Don't save passwords as plain text. Instead save them as a secure string and **encrypt** them **locally**.

**Input sensitive data** into the console

```powershell
$securePassword = Read-Host "Password" -AsSecureString
```

Don't convert _plain text_ into _secure string_  

```powershell
$securePassword = ConvertTo-SecureString $PlainPassword -AsPlainText -Force
```

- as the commands get logged.

# Read and write files

**Encrypt** an existing file

```powershell
$xml = Get-Content -Path ".\temp.xml" -Raw
ConvertTo-SecureString -AsPlainText $xml -Force `
| ConvertFrom-SecureString `
| Out-File secure.bin

Remove-Item -Path ".\temp.xml"
```

**Decrypt** an existing file

```powershell
$secure = Get-Content -Path ".\secure.bin" `
| ConvertTo-SecureString$cred

$bstr = [Runtime.InteropServices.Marshal]::SecureStringToBSTR($secure)
$xml = [Runtime.InteropServices.Marshal]::PtrToStringAuto($bstr)
$xml | Out-File ".\temp.xml"
```

# Credential

Enter credential in GUI
```powershell
$credential = Get-Credential
```

Enter credential in terminal
```powershell
$username = "DOMAIN\username"
$password = Read-Host "Enter password for $username" -AsSecureString
$credential = New-Object System.Management.Automation.PSCredential($username, $password)
```

Save user-encrypted password to file
```powershell
$password = Read-Host "Enter password for $username" -AsSecureString
$password | ConvertFrom-SecureString | Out-File "credential.bin"
```

Save user-encrypted credential to file
```powershell
$credential.Password | ConvertFrom-SecureString | Out-File "credential.bin"
```

# De-obfuscate data locally

Only the **same PowerShell instance** can decrypt. 

**De-obfuscate** a credential

```powershell
$credential.GetNetworkCredential().Password
```

**De-obfuscate** a secure string

```powershell
function Decrypt-SecureString {
    [CmdletBinding()] param(
        [Parameter(Mandatory=$true, ValueFromPipeline=$true)] $SecureObject
    )
    $type = ($SecureObject).getType()
    if ($type -eq [System.Security.SecureString]) {
        [System.Net.NetworkCredential]::new("", $SecureObject).Password
    } elseif ($type -eq [System.Management.Automation.PSCredential]) {
        Decrypt-SecureString -SecureObject $SecureObject.Password
    } else {
        Write-Error ("The parameter is of unknown type [" + [string]$($SecureObject.GetType().FullName) + "]")
    }
}
```

**Decrypt** a secure string or credential

```powershell
function Decrypt-SecureString {
    [CmdletBinding()] param(
        [Parameter(ParameterSetName='secureString', Position=0, ValueFromPipeline=$true)]
        [System.Security.SecureString] $secureString,
        [Parameter(ParameterSetName='credential', Position=0)]
        [System.Management.Automation.PSCredential] $credential
    )
    switch ($PSCmdlet.ParameterSetName) {
        'secureString' {
            Write-Output ([System.Net.NetworkCredential]::new("", $secureString).Password)
        }
        'credential' {
            Decrypt-SecureString -secureString $credential.Password
        }
    }
}
```

---
Sources:

Related:

Tags:
[Operate on file system - Use paths, get meta data, link, download, and encrypt files and folders](./powershell/filesystem/index.md)
[Handle PowerShell data - Handle, Import, Export, Filter and RegEx query objects](./Handle-PowerShell-data.md)
