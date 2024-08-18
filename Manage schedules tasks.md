
```powershell
#Requires -RunAsAdministrator
```

```run-powershell
$is_executed_privileged = ([Security.Principal.WindowsPrincipal][Security.Principal.WindowsIdentity]::GetCurrent()).
    IsInRole([Security.Principal.WindowsBuiltInRole]::"Administrator")
if (-not $is_executed_privileged) {
    if ((Get-Command wt.exe) -ne $null) {
        Start-Process wt "powershell -File $PSCommandPath -ExecutionPolicy Bypass" -Verb RunAs
    }
    else {
        Start-Process powershell "-File $PSCommandPath -ExecutionPolicy Bypass" -Verb RunAs
    }
    exit
}
```

Schedule multiple actions

```powershell
$actions = (New-ScheduledTaskAction -Execute 'foo.ps1'), (New-ScheduledTaskAction -Execute 'bar.ps1')
$trigger = New-ScheduledTaskTrigger -Daily -At '9:15 AM'
$principal = New-ScheduledTaskPrincipal -UserId 'DOMAIN\user' -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -WakeToRun
$task = New-ScheduledTask -Action $actions -Principal $principal -Trigger $trigger -Settings $settings

Register-ScheduledTask 'baz' -InputObject $task
```

Run **hidden** processes with **administrative** privileges regardless of currently logged on user

```powershell
# untested script
$action = New-ScheduledTaskAction -Execute foo.exe -Argument "bar baz"
$trigger = New-ScheduledTaskTrigger -Once -At (Get-Date) -RepetitionInterval (New-TimeSpan -Minutes 1) -RepetitionDuration ([Timespan]::MaxValue)
$principal = New-ScheduledTaskPrincipal -UserID "NT AUTHORITY\SYSTEM" -LogonType ServiceAccount -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -MultipleInstances Parallel

Register-ScheduledTask -TaskName "tasknamehere" -TaskPath "\my\path" -Action $action -Trigger $trigger -Settings $settings -Principal $principal
```


---
Sources:
- [New-ScheduledTask (ScheduledTasks) | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/module/scheduledtasks/new-scheduledtask?view=windowsserver2022-ps&wt.mc_id=ps-gethelp)
- [New-ScheduledTaskPrincipal (ScheduledTasks) | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/module/scheduledtasks/new-scheduledtaskprincipal?view=windowsserver2022-ps&wt.mc_id=ps-gethelp)
- [In a PowerShell script, how can I check if I'm running with administrator privileges? - Server Fault](https://serverfault.com/questions/95431/in-a-powershell-script-how-can-i-check-if-im-running-with-administrator-privil)
- [Powershell: Set a Scheduled Task to run when user isn't logged in - Stack Overflow](https://stackoverflow.com/questions/13965997/powershell-set-a-scheduled-task-to-run-when-user-isnt-logged-in)
- [powershell - List process for current user - Stack Overflow](https://stackoverflow.com/questions/35195221/list-process-for-current-user)
- [c# - Find out whether a Process is a System Process - Stack Overflow](https://stackoverflow.com/questions/53354644/find-out-whether-a-process-is-a-system-process)

Related:


Tags:
[PowerShell](./content/powershell.md)
[Windows](./content/windows.md)