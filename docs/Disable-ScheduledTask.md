---
external help file: PowerSponse-help.xml
Module Name: PowerSponse
online version: https://github.com/swisscom/PowerSponse/blob/master/docs/Disable-ScheduledTask.md
schema: 2.0.0
---

# Disable-ScheduledTask

## SYNOPSIS
Disable a scheduled task.

## SYNTAX

```
Disable-ScheduledTask [-ComputerName <String[]>] [-ComputerList <String>] [-Method <String>]
 [-BinPath <String>] [-Session <PSSession[]>] [-Credential <PSCredential>] [-NoRemoteRegistry] [-OnlineCheck]
 [-SearchString <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Disable-ScheduledTask** cmdlet lets you disable a Windows scheduled task.

When no target host is supplied, localhost is used.

You have to supply the full task name (when not in root also the path to the
task). Use `Get-ScheduledTask` to find the corresponding taskname.

## EXAMPLES

### Example 1: Disabling task on localhost
```
PS> Disable-ScheduledTask -TaskName "Adobe Flash Player Updater" -UseExternal | ft

Time                Action             ComputerName Arguments                                                  Status Reason
----                ------             ------------ ---------                                                  ------ ------
05.01.2017 20:37:08 Enable-Service     localhost    ServiceName: RemoteRegistry, StartupType: manual           pass   RemoteRegistry enabled.
05.01.2017 20:37:08 Edit-Service       localhost    ServiceName: RemoteRegistry, ServiceState start            pass   Service set to start.
05.01.2017 20:37:09 Stop-Service       localhost    ServiceName: RemoteRegistry                                pass   Service set to stop.
05.01.2017 20:37:10 Disable-Service    localhost    ServiceName: RemoteRegistry                                pass   Service disabled
05.01.2017 20:37:10 Edit-ScheduledTask localhost    TaskName: "Adobe Flash Player Updater", TaskState: disable pass   Task set to disable
```

You can combine the output of this cmdlet with the output of the other cmdlets.

### Example 2: Disabling task on multiple hosts
```
PS> Disable-ScheduledTask -TaskName "Adobe Flash Player Updater" -ComputerName Comp1, Comp2 -UseExternal | ft

Time                Action                ComputerName Arguments                                                  Status Reason
----                ------                ------------ ---------                                                  ------ ------
05.01.2017 20:39:48 Enable-RemoteRegistry Comp1                                                                   fail   offline
05.01.2017 20:39:51 Edit-Service          Comp1        ServiceName: RemoteRegistry, ServiceState start            fail   offline
05.01.2017 20:39:51 Edit-ScheduledTask    Comp1        TaskName: "Adobe Flash Player Updater", TaskState: disable fail   Error while enabling RemoteRegistry
05.01.2017 20:39:53 Enable-RemoteRegistry Comp2                                                                   fail   offline
05.01.2017 20:39:55 Edit-Service          Comp2        ServiceName: RemoteRegistry, ServiceState start            fail   offline
05.01.2017 20:39:55 Edit-ScheduledTask    Comp2        TaskName: "Adobe Flash Player Updater", TaskState: disable fail   Error while enabling RemoteRegistry
```

Disables the tasks on multiple hosts and lists the progress of the whole chain.

## PARAMETERS

### -BinPath
Binary path for using with external tools.

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

### -ComputerList
File with a list of target computers.

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

### -ComputerName
A list of computer names as comma separated list.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
Alternate credentials to use.

```yaml
Type: PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session
Use an existing PSSession to execute the commands.

```yaml
Type: PSSession[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoRemoteRegistry
Do not enable RemoteRegistry. By default, if needed, RemoteRegistry will be enabled before running commands and disabled afterwards.

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

### -Method
Method to use by the function.

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

### -OnlineCheck
Check if the target hosts are online. Disabling it speeds things up.

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

### -SearchString
Search string to search for tasks. Use regex for matching.

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS
