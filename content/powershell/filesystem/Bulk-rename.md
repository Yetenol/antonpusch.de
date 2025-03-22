---
date: "2025-03-22T23:26:27.467+01:00"
title: "Bulk rename"
description: "Rename pictures and videos chronologically and consistently by their capture and creation time"
dg-publish: true
dg-folder: powershell/filesystem
---

# Naming convention

- `yyyyMMdd_HHmmss` for original media
- `yyyyMMdd_HHmmss crop` for cropped media
- `yyyyMMdd_HHmmss edit` for adjusted media

# Standardize file name

Rename **movies** to `yyyyMMdd_HHmmss`

```powershell
$i = 0
gci -Filter "*.MOV" |
% { 
    [string]$newName = ($_.CreationTime).ToString("yyyyMMdd_HHmmss") + " " + $i++ + $_.Extension
    Rename-Item -Path $_ -NewName $newName
}
```

Standardize **pictures** name

```powershell
function Rename-Pictures {
    $index = 1
    $files = Get-ChildItem -File -Filter "*.jpg"
    $files | foreach {
        Rename-Item -Path $_ -NewName "_$($_.Name)"
    }
    Get-ChildItem -File -Filter "*.jpg" | foreach { 
        $ID = "#" + ($index++).ToString().PadLeft(3,  "0")
        $Date = [RegEx]::Match($_.BaseName, @('(?<!\d)' + '20\d{6}' + '(?!\d)')).value
        $Time = [RegEx]::Match($_.BaseName, @('(?<!\d)' + '\d{6}' + '(?!\d)')).value
        $Modifications = [RegEx]::Match($_.BaseName, @('crop|edit')).value
        $NewName = ((@($ID, $Date, $Time, $Modifications) | where {$_}) -join " ") + $_.Extension
        Rename-Item -Path $_ -NewName $NewName
        [PSCustomObject]@{
            "Old Name" = $_.Name
            "New Name" = $NewName
    }}
}
```

Rename **images** to `yyyyMMdd_HHmmss`

```powershell
Function Rename-Pictures
{    
    Param ( 
        [Parameter(Mandatory=$FALSE)][string]$Path = (Get-Location), 
        [Parameter(Mandatory=$FALSE)][string]$BackupFileName = '_backupdata.csv'
    ) 
    
    Begin 
    { 
        [reflection.assembly]::LoadFile("C:\Windows\Microsoft.NET\Framework\v4.0.30319\System.Drawing.dll") 
        $Script:ErrorLogMsg = $Null
        $Script:CorrectPath = $Null
    } 
    
    Process 
    { 
        # Workaround for correct path from user 
        if ($Path.EndsWith('\\')) 
        { 
            $ImgsFound = Get-ChildItem ($Path + '*') -Include *.jpeg, *.png, *.gif, *.jpg, *.bmp, *.png | Select-Object -Property FullName, Name, BaseName, Extension 
        } 
        else
        { 
            $ImgsFound = Get-ChildItem ($Path + '\\*') -Include *.jpeg, *.png, *.gif, *.jpg, *.bmp, *.png | Select-Object -Property FullName, Name, BaseName, Extension 
        } 
            
        # If any file was found 
        If ($ImgsFound.Count -gt 0) {         
            # Print the number of images found to the user 
            Write-Host -Object ("# of pictures suitable for renaming in " + $Path + ": " + $ImgsFound.Count + "`n") 
    
            # Array that takes in the old- and the new filename. This is used for saving a backup to .csv 
            $BackupData = @() 
    
            $i = 0
            # Loops through the images found 
            foreach ($Img in $ImgsFound)  
            { 
                $i++
                # Gets image data 
                $ImgData = New-Object System.Drawing.Bitmap($Img.FullName) 
    
    
                $ImgDimensions =  $ImgData.Width.ToString() + $("x") + $ImgData.Height.ToString()
    
    
                try  
                { 
                    # Gets 'Date Taken' in bytes 
                    [byte[]]$ImgBytes = $ImgData.GetPropertyItem(36867).Value 
                } 
                catch [System.Exception], [System.IO.IOException]
                { 
                    [string]$ErrorMessage = ( 
                        (Get-Date).ToString('yyyyMMdd HH:mm:ss') + "`tERROR`tDid not change name for " + $Img.Name + ". Reason: " + $Error
                    ) 
                    $Script:ErrorLogMsg += $ErrorMessage + "`r`n"
                    Write-Host -ForegroundColor Red -Object $ErrorMessage
    
                    # Clears any error messages 
                    $Error.Clear() 
    
                    # No reason to continue. Move on to the next file 
                    continue
                } 
    
                # Gets the date and time from bytes 
                [string]$dateString = [System.Text.Encoding]::ASCII.GetString($ImgBytes) 
                # Formats the date to the desired format 
                [string]$dateTaken = [datetime]::ParseExact($dateString,"yyyy:MM:dd HH:mm:ss`0",$Null).ToString('yyyyMMdd_HHmmss') 
                # The new file name for the image 
                #  [string]$NewFileName = $dateTaken + '-' + $Img.Name 
                [string]$NewFileName = $dateTaken + " " + $i + [System.IO.Path]::GetExtension($Img.Name)
                    
                $ImgData.Dispose() 
                try 
                {  
                    Rename-Item -NewName $NewFileName -Path $Img.FullName -ErrorAction Stop 
                    Write-Host -Object ("Renamed " + $Img.Name + " to " + $NewFileName) 
                } 
                catch 
                { 
                    [string]$ErrorMessage = ( 
                        (Get-Date).ToString('yyyyMMdd HH:mm:ss') + "`tERROR`tDid not change name for "  + $Img.Name + ". Reason: " + $Error
                    ) 
                    $Script:ErrorLogMsg += $ErrorMessage + "`r`n"
                    Write-Host -ForegroundColor Red -Object $ErrorMessage
    
                    # Clears any previous error messages 
                    $Error.Clear() 
    
                    # No reason to continue. Move on to the next file 
                    continue
                } 
                    
                # Collect data to be added to the backup file 
                $BUData = New-Object -TypeName System.Object 
                $BUData | Add-Member -MemberType NoteProperty -Name "OldName" -Value $Img.Name 
                $BUData | Add-Member -MemberType NoteProperty -Name "NewName" -Value $NewFileName
    
                # Add data to backup collection 
                $BackupData += $BUData
            } # foreach 
    
            try  
            { 
                $BackupData | Export-Csv -NoTypeInformation -Path ($Path + $BackupFileName) 
            } 
            catch [System.Exception] 
            { 
                [string]$ErrorMessage = ( 
                    (Get-Date).ToString('yyyyMMdd HH:mm:ss') + "`tERROR`tCould not create "  + ($Path + $BackupFileName) + ". Reason: " + $Error
                ) 
                    $Script:ErrorLogMsg += $ErrorMessage + "`r`n"
    
                # Clears any error messages 
                $Error.Clear() 
            } 
        } # if imgcount > 0 
        else { 
            Write-Host -Object ("Found 0 image files at " + $Path) 
        } 
    
        # If there was a problem during the run: 
        # Print to file, and let user know 
        if ($Script:ErrorLogMsg -ne $Null) { 
            Out-File -FilePath ($Path + '_errors.log') -InputObject $ErrorLogMsg
            Write-Host -ForegroundColor Red -Object ( 
                "Errors were found. Please check " + $Path + "_errors.log"
            ) 
        } 
    } 
    
    End{} 
}
```

Rename images without _date taken_ property to `yyyyMMdd_HHmmss`

---
Sources:

Related:

Tags:
[File system operations - Use paths, get meta data, link, download, and encrypt files and folders](./index.md)
