---
date: "2025-03-22T07:21:26.988+01:00"
title: "File Meta Data"
description: "Add image dimensions, capture time, extended fields and signature information to file information"
dg-publish: true
---

- [Compare static and dynamic property calculation](./Compare-static-and-dynamic-property-calculation.md)

Access built in version info
- `Comments`, `CompanyName`, `FileBuildPart`, `FileDescription`, `FileMajorPart`, `FileMinorPart`, `FileName`, `FilePrivatePart`, `FileVersion`, `InternalName`, `IsDebug`, `IsPatched`, `IsPreRelease`, `IsPrivateBuild`, `IsSpecialBuild`, `Language`, `LegalCopyright`, `LegalTrademarks`, `OriginalFilename`, `PrivateBuild`, `ProductBuildPart`, `ProductMajorPart`, `ProductMinorPart`, `ProductName`, `ProductPrivatePart`, `ProductVersion`, `SpecialBuild`

Add dimensions of images to their provided `[FileInfo]` object. Added properties are:
- `Width`, `Height`, `Dimension`

```powershell
function Add-PixelDimensions {
    <#
    .SYNOPSIS
        Add dimensions of images to their file information.
    .DESCRIPTION
        Add dimensions of images to their provided [FileInfo] object.
    .PARAMETER File
        File information of pictures to be added with properties. Directories and other files remain unchanged.
    .PARAMETER PassThru
        Returns an object representing the item with which you are working. By default, this cmdlet doesn't generate any output.
    .EXAMPLE
        Get-ChildItem -Filter *.jpg  | Add-PixelDimensions -PassThru | Select-Object Name, Width, Height | Format-Table
    .EXAMPLE
        $Files = Get-ChildItem -Filter *.jpg
        $Files | Add-PixelDimensions
        $Files.Dimension
    #>
    PARAM (
        [Parameter(Mandatory, ValueFromPipeline)] [IO.FileSystemInfo[]] $File,
        [Switch] $PassThru = $false
    )
    BEGIN {
        [Reflection.Assembly]::LoadWithPartialName("System.Drawing") | Out-Null
        New-Variable -Name COMBINE_DIMENSIONS -Value {"" + $this.Width + "x" + $this.Height} -Option ReadOnly 
    }
    PROCESS {
        if ($File.Count -gt 1) {
            return $File | Add-PixelDimensions -PassThru:$PassThru
        }   
        try {
            $ImageData = New-Object System.Drawing.Bitmap($File.FullName)
            $File | Add-Member -NotePropertyName "Width" -NotePropertyValue $ImageData.Width
            $File | Add-Member -NotePropertyName "Height" -NotePropertyValue $ImageData.Height
            $ImageData.Dispose()
            $File | Add-Member -MemberType ScriptProperty -Name "Dimension" -Value $COMBINE_DIMENSIONS
        }
        catch {
        }
        if ($PassThru) {
            $File
        }
    }
}
```

Add the date in the filename to their provided `[FileInfo]` object. The date is a proper `[DateTime]` object. Added properties are:
- `FilenameTime`, `ImageManipulationStatus`

```powershell
function Add-FilenameTime {
    <#
    .SYNOPSIS
        Add the date in the filename to their file information.
    .DESCRIPTION
        Add the date in the filename to their provided [FileInfo] object.
    .PARAMETER File
        File information of pictures to be added with properties. Directories and other files remain unchanged.
    .PARAMETER PassThru
        Returns an object representing the item with which you are working. By default, this cmdlet doesn't generate any output.
    .EXAMPLE
        Get-ChildItem -Filter *.jpg  | Add-FilenameTime -PassThru | Select-Object Name, FilenameTime | Format-Table
    .EXAMPLE
        $Files = Get-ChildItem -Filter *.jpg
        $Files | Add-FilenameTime
        $Files.FilenameTime
    #>
    PARAM (
        [Parameter(Mandatory, ValueFromPipeline)] [IO.FileSystemInfo[]] $File,
        [Switch] $PassThru = $false
    )
    BEGIN {
        New-Variable -Name DATE_PATTERN -Option ReadOnly -Value (
            '(?<year>20\d{2})' + '-?' + '(?<month>\d{2})' + '-?' + '(?<day>\d{2})'
        )
        New-Variable -Name TIME_OF_DAY_PATTERN -Option ReadOnly -Value (
            '(?<hour>\d{2})' + '-?' + '(?<minute>\d{2})' + '-?' + '(?<second>\d{2})'
        )
        New-Variable -Name POSSIBLE_TIME_OF_DAY_PATTERN -Option ReadOnly -Value (
            '(?:' + '[ _]' + $TIME_OF_DAY_PATTERN + ')'
        )
        New-Variable -Name TEMPORAL_PATTERN -Option ReadOnly -Value (
            $DATE_PATTERN + $POSSIBLE_TIME_OF_DAY_PATTERN 
        )
        New-Variable -Name IMAGE_MANIPULATION_STATUS -Value 'crop|edit' -Option ReadOnly
    }
    PROCESS {
        if ($File.Count -gt 1) {
            return $File | Add-FilenameTime -PassThru:$PassThru
        }   
        try {
            [String] $ImageManipulationStatus = [RegEx]::Match($File, $IMAGE_MODIFICATION_SWITCHES).value
            
            $RegExCaptures = [RegEx]::Match($File.BaseName, $TEMPORAL_PATTERN)
            if ($RegExCaptures.Success) {
                [DateTime] $FilenameTime = Get-Date `
                -Year $RegExCaptures.Groups["year"].value `
                -Month $RegExCaptures.Groups["month"].value `
                -Day $RegExCaptures.Groups["day"].value `
                -Hour $RegExCaptures.Groups["hour"].value `
                -Minute $RegExCaptures.Groups["minute"].value `
                -Second $RegExCaptures.Groups["second"].value
            } else {
                $FilenameTime = $null
            }

            $File | Add-Member -NotePropertyName "ImageManipulationStatus" -NotePropertyValue $ImageManipulationStatus
            $File | Add-Member -NotePropertyName "FilenameTime" -NotePropertyValue $FilenameTime
        }
        catch {
        }
        if ($PassThru) {
            $File
        }
    }
}
```

Add the real capture date of images to their provided `[FileInfo]` object. The date is a proper `[DateTime]` object. Added property is:
- `CaptureTime`

```powershell
function Add-CaptureTime {
    <#
    .SYNOPSIS
        Add the real capture date of images to their file information.
    .DESCRIPTION
        Add the real capture date of images to their provided [FileInfo] object. The date is a proper [DateTime] object.
    .PARAMETER File
        File information of pictures to be added with the property. Directories and other files remain unchanged.
    .PARAMETER PassThru
        Returns an object representing the item with which you are working. By default, this cmdlet doesn't generate any output.
    .EXAMPLE
        Get-ChildItem -Filter *.jpg  | Add-CaptureTime -PassThru | Select-Object Name, CaptureTime | Format-Table
    .EXAMPLE
        $Files = Get-ChildItem -Filter *.jpg 
        $Files | Add-CaptureTime
        $Files.CaptureTime
    #>
    PARAM (
        [Parameter(Mandatory, ValueFromPipeline)] [IO.FileSystemInfo[]] $File,
        [Switch] $PassThru = $false
    )
    BEGIN {
        [Reflection.Assembly]::LoadWithPartialName("System.Drawing") | Out-Null
    }
    PROCESS {
        if ($File.Count -gt 1) {
            return $File | Add-CaptureTime -PassThru:$PassThru
        }
        try {
            $ImageData = New-Object System.Drawing.Bitmap($File.FullName)
            $FieldCharacters = $ImageData.GetPropertyItem(36867).Value
            $ImageData.Dispose()
            $StringTime = [System.Text.Encoding]::ASCII.GetString($FieldCharacters) 
            $CaptureTime = [DateTime]::ParseExact($StringTime, "yyyy:MM:dd HH:mm:ss`0", $Null)
            $File | Add-Member -NotePropertyName "CaptureTime" -NotePropertyValue $CaptureTime
        }
        catch {
        }
        if ($PassThru) {
            $File
        }
    }
}
```

Add advanced file fields visible in File Explorer to the file's provided `[FileInfo]` object. The fields are read as plain text and collected in the `TextFields` property. Possible subproperties are:
- `Name`, `Size`, `Item Type`, `Date Modified`, `Date Created`, `Date Accessed`, `Attributes`, `Offline Status`, `Availability`, `Perceived Type`, `Owner`, `Kind`, `Date Taken`, `Contributing Artists`, `Album`, `Year`, `Genre`, `Conductors`, `Tags`, `Rating`, `Authors`, `Title`, `Subject`, `Categories`, `Comments`, `Copyright`, `#`, `Length`, `Bit Rate`, `Protected`, `Camera Model`, `Dimensions`, `Camera Maker`, `Company`, `File Description`, `Masters Keywords`, `Program Name`, `Duration`, `Is Online`, `Is Recurring`, `Location`, `Optional Attendee Addresses`, `Optional Attendees`, `Organizer Address`, `Organizer Name`, `Reminder Time`, `Required Attendee Addresses`, `Required Attendees`, `Resources`, `Meeting Status`, `Free/Busy Status`, `Total Size`, `Account Name`, `Task Status`, `Computer`, `Anniversary`, `Assistant's Name`, `Assistant's Phone`, `Birthday`, `Business Address`, `Business City`, `Business Country/Region`, `Business P.O. Box`, `Business Postal Code`, `Business State Or Province`, `Business Street`, `Business Fax`, `Business Home Page`, `Business Phone`, `Callback Number`, `Car Phone`, `Children`, `Company Main Phone`, `Department`, `E-Mail Address`, `E-Mail2`, `E-Mail3`, `E-Mail List`, `E-Mail Display Name`, `File As`, `First Name`, `Full Name`, `Gender`, `Given Name`, `Hobbies`, `Home Address`, `Home City`, `Home Country/Region`, `Home P.O. Box`, `Home Postal Code`, `Home State Or Province`, `Home Street`, `Home Fax`, `Home Phone`, `IM Addresses`, `Initials`, `Job Title`, `Label`, `Last Name`, `Mailing Address`, `Middle Name`, `Cell Phone`, `Nickname`, `Office Location`, `Other Address`, `Other City`, `Other Country/Region`, `Other P.O. Box`, `Other Postal Code`, `Other State Or Province`, `Other Street`, `Pager`, `Personal Title`, `City`, `Country/Region`, `P.O. Box`, `Postal Code`, `State Or Province`, `Street`, `Primary E-Mail`, `Primary Phone`, `Profession`, `Spouse/Partner`, `Suffix`, `TTY/TTD Phone`, `Telex`, `Webpage`, `Content Status`, `Content Type`, `Date Acquired`, `Date Archived`, `Date Completed`, `Device Category`, `Connected`, `Discovery Method`, `Friendly Name`, `Local Computer`, `Manufacturer`, `Model`, `Paired`, `Classification`, `Status`, `Client ID`, `Contributors`, `Content Created`, `Last Printed`, `Date Last Saved`, `Division`, `Document ID`, `Pages`, `Slides`, `Total Editing Time`, `Word Count`, `Due Date`, `End Date`, `File Count`, `File Extension`, `Filename`, `File Version`, `Flag Color`, `Flag Status`, `Space Free`, `Group`, `Sharing Type`, `Bit Depth`, `Horizontal Resolution`, `Width`, `Vertical Resolution`, `Height`, `Importance`, `Is Attachment`, `Is Deleted`, `Encryption Status`, `Has Flag`, `Is Completed`, `Incomplete`, `Read Status`, `Shared`, `Creators`, `Date`, `Folder Name`, `File Location`, `Folder`, `Participants`, `Path`, `By Location`, `Type`, `Contact Names`, `Entry Type`, `Language`, `Date Visited`, `Description`, `Link Status`, `Link Target`, `URL`, `Media Created`, `Date Released`, `Encoded By`, `Episode Number`, `Producers`, `Publisher`, `Season Number`, `Subtitle`, `User Web URL`, `Writers`, `Attachments`, `Bcc Addresses`, `Bcc`, `Cc Addresses`, `Cc`, `Conversation ID`, `Date Received`, `Date Sent`, `From Addresses`, `From`, `Has Attachments`, `Sender Address`, `Sender Name`, `Store`, `To Addresses`, `To Do Title`, `To`, `Mileage`, `Album Artist`, `Sort Album Artist`, `Album ID`, `Sort Album`, `Sort Contributing Artists`, `Beats-Per-Minute`, `Composers`, `Sort Composer`, `Disc`, `Initial Key`, `Part Of A Compilation`, `Mood`, `Part Of Set`, `Period`, `Color`, `Parental Rating`, `Parental Rating Reason`, `Space Used`, `EXIF Version`, `Event`, `Exposure Bias`, `Exposure Program`, `Exposure Time`, `F-Stop`, `Flash Mode`, `Focal Length`, `35Mm Focal Length`, `ISO Speed`, `Lens Maker`, `Lens Model`, `Light Source`, `Max Aperture`, `Metering Mode`, `Orientation`, `People`, `Program Mode`, `Saturation`, `Subject Distance`, `White Balance`, `Priority`, `Project`, `Channel Number`, `Episode Name`, `Closed Captioning`, `Rerun`, `SAP`, `Broadcast Date`, `Program Description`, `Recording Time`, `Station Call Sign`, `Station Name`, `Summary`, `Snippets`, `Auto Summary`, `Relevance`, `File Ownership`, `Sensitivity`, `Shared With`, `Sharing Status`, `Product Name`, `Product Version`, `Support Link`, `Source`, `Start Date`, `Sharing`, `Availability Status`, `Billing Information`, `Complete`, `Task Owner`, `Sort Title`, `Total File Size`, `Legal Trademarks`, `Video Compression`, `Directors`, `Data Rate`, `Frame Height`, `Frame Rate`, `Frame Width`, `Spherical`, `Stereo`, `Video Orientation`, `Total Bitrate`

```powershell
function Add-AdvancedFields {
    <#
    .SYNOPSIS
        Add advanced file fields visible in File Explorer to their file information.
    .DESCRIPTION
        Add advanced file fields visible in File Explorer to the file's provided `[FileInfo]` object. 
        The fields are read as plain text and collected in the `TextFields` property.
    .PARAMETER File
        File information of files to be added with properties. Directories remain unchanged.
    .PARAMETER PassThru
        Returns an object representing the item with which you are working. By default, this cmdlet doesn't generate any output.
    .EXAMPLE
        Get-ChildItem -File | Add-AdvancedFields -PassThru | Select-Object Name -ExpandProperty TextFields | 
            Select-Object Name, Kind, Dimensions, "ISO Speed"
    .EXAMPLE
        $Files = Get-ChildItem -File
        $Files | Add-AdvancedFields
        $Files.TextFields."Item Type"
    #>
    PARAM (
        [Parameter(Mandatory, ValueFromPipeline)] [IO.FileSystemInfo[]] $File,
        [Switch] $PassThru = $false
    )
    BEGIN {
        New-Variable -Name VISIALIZE_OBJECT_AS_STRING -Value {($this | Format-List | Out-String).Trim()} -Option ReadOnly
        New-Variable -Name IGNORE_CONFLICTING_FIELDS -Option ReadOnly -Value (
            [IO.FileSystemInfo].GetProperties().Name +
            @('Space Free', 'Total Size', 'Space Used')
        )
    }
    PROCESS {
        if ($File.Count -gt 1) {
            return $File | Add-AdvancedFields -PassThru:$PassThru
        }
        try {
            $EmptyObject = [PSCustomObject]@{}
            $File | Add-Member -NotePropertyName "TextFields" -NotePropertyValue $EmptyObject
            $File.TextFields | Add-Member -MemberType ScriptMethod -Name "ToString" -Value $VISIALIZE_OBJECT_AS_STRING -Force

            $ShellApplication = New-Object -ComObject Shell.Application
            $ShellFolder = $ShellApplication.Namespace($File.Directory.FullName)
            $ShellFile = $ShellFolder.ParseName($File.Name)
            0..400 | ForEach-Object -Process {
                $DataValue = $ShellFolder.GetDetailsOf($null, $_)
                $DataValue = $DataValue.Trim()
                [PSCustomObject]@{
                    FieldIndex = $_
                    FieldName  = (Get-Culture).TextInfo.ToTitleCase($DataValue)
                    FieldValue = $ShellFolder.GetDetailsOf($ShellFile, $_)
                }
            } | Where-Object {
                $_.FieldName -and $_.FieldValue -and
                ($_.FieldName -notin $IGNORE_DUPLICATE_FIELDS)
            } | ForEach-Object {
                $File.TextFields | Add-Member -NotePropertyName $_.FieldName -NotePropertyValue $_.FieldValue
            }
        }
        catch {
        }
        if ($PassThru) {
            $File
        }
    }
}
```

Add information about the [digital certificate](https://learn.microsoft.com/en-us/windows-hardware/drivers/install/authenticode) of Authenticode-signed software, mainly PowerShell scripts, to the file's provided `[FileInfo]` object. The information is collected in the `SignatureInfo` property. Possible subproperties are:
- `Status`, `IsOSBinary`, `Archived`, `Extensions`, `FriendlyName`, `IssuerName`, `NotAfter`, `NotBefore`, `HasPrivateKey`, `PrivateKey`, `PublicKey`, `RawData`, `SerialNumber`, `SubjectName`, `SignatureAlgorithm`, `Thumbprint`, `Version`, `Handle`, `Issuer`, `Subject`

```powershell
function Add-SignatureInfo {
    <#
    .SYNOPSIS
        Add information about the digital certificate to their file information.
    .DESCRIPTION
        Add information about the digital certificate of Authenticode-signed software, mainly PowerShell scripts, to the file's provided [FileInfo] object. 
        The information is collected in the `SignatureInfo` property.
    .PARAMETER File
        File information of a files. Directories remain unchanged.
    .PARAMETER PassThru
        Returns an object representing the item with which you are working. By default, this cmdlet doesn't generate any output.
    .EXAMPLE
        Get-ChildItem -Filter *.ps1 | Add-SignatureInfo -PassThru | Select-Object Name -ExpandProperty SignatureInfo | 
            Select-Object Name, Status, IsOSBinary, Subject | Format-Table
    .EXAMPLE
        $Files = Get-ChildItem -Filter *.ps1
        $Files | Add-SignatureInfo
        $Files.SignatureInfo.Status
    #>
    PARAM (
        [Parameter(Mandatory, ValueFromPipeline)] [IO.FileSystemInfo[]] $File,
        [Switch] $PassThru = $false
    )
    BEGIN {
        New-Variable -Name VISIALIZE_OBJECT_AS_STRING -Value {($this | Format-List | Out-String).Trim()} -Option ReadOnly
    }
    PROCESS {
        if ($File.Count -gt 1) {
            return $File | Add-SignatureInfo -PassThru:$PassThru
        }
        try {
            $DigitalSignature = $File | Get-AuthenticodeSignature
            $SignerCertificate = [Management.Automation.Signature] $DigitalSignature.SignerCertificate
            if ($null -eq $DigitalSignature.SignerCertificate) {
                $SignerCertificate = [PSCustomObject]@{}
            }
            $File | Add-Member -NotePropertyName "SignatureInfo" -NotePropertyValue $SignerCertificate
            $File.SignatureInfo | Add-Member -MemberType ScriptMethod -Name "ToString" -Value $VISIALIZE_OBJECT_AS_STRING -Force
            $File.SignatureInfo | Add-Member -NotePropertyName 'Status' -NotePropertyValue $DigitalSignature.Status
            $File.SignatureInfo | Add-Member -NotePropertyName 'IsOSBinary' -NotePropertyValue $DigitalSignature.IsOSBinary
        }
        catch {
        }
        if ($PassThru) {
            $File
        }
    }
}
```

---
Sources:
- 2022-12-17: [Getting file metadata with PowerShell similar to what Windows Explorer provides - Evotec](https://evotec.xyz/getting-file-metadata-with-powershell-similar-to-what-windows-explorer-provides/)

Related:

Tags:
[Operate on file system - Use paths, get meta data, link, download, and encrypt files and folders](./powershell/filesystem/index.md)
