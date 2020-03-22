1.

Comando

```
PS C:\Users\Desktop> Get-Process | Select-Object Name, ID, Responding | Format-Table -AutoSize
```

Resultado

```
Name                                                             Id Responding
----                                                             -- ----------
aips                                                           2536       True
ApplicationFrameHost                                           8644       True
armsvc                                                         2432       True
audiodg                                                        8312       True
avp                                                            3028       True

```

2. 

Comando

```
PS C:\Users\Desktop> Get-Process | Format-Table Name, Id, @{Name='VM (MB)';Expression={$_.VM / 1MB -as [int]}}, @{Name='PM (MB)'; Expression={$_.PM / 1MB -as [int]}}
```
Resultado

```
Name                                                             Id VM (MB) PM (MB)                                                      
----                                                             -- ------- -----
aips                                                           2536      81    5
ApplicationFrameHost                                           8644 2101483   14
armsvc                                                         2432      42    1
audiodg                                                        8312 2101356   18
avp                                                            3028     629  195
avpui                                                          6428     341   59
CompPkgSrv                                                     3992 2101339    2
csrss                                                           704 2101338    2
```

3. 
  
Comando 
 
```
PS C:\Users\Desktop> Get-EventLog -List | Format-Table @{Name='LogName';Expression={$_.LogDisplayName}}, @{Name='Periodo de Retencion';Expression={$_.minimumRetentionDays}}
```
Resultado

```
LogName                              Periodo de Retencion
-------                              --------------------
Aplicación                                              0
Eventos de hardware                                     0
Internet Explorer                                       7
Servicio de administración de claves                    0
Microsoft Office Alerts                                 0
                                                         
Sistema                                                 0
Windows PowerShell                                      0
```

4.

Comando
 
```   
PS C:\Users\Desktop> Get-Service | Sort-by Status | Format-List -GroupBy status
```

Resultado


```
 Status: Stopped


Name                : AarSvc_1207df
DisplayName         : Agent Activation 
Status              : Stopped
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : False
ServiceType         : 224

 Status: Running

Name                : BthAvctpSvc
DisplayName         : Servicio 
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {rpcss}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess, Win32ShareProcess
```

5.
   
Comando

``` 
PS C:\Users\Desktop> ls -Path C:\ | Format-Wide -Column 4
```
Resultado

```
Android             Intel               PerfLogs            powershellpruebas  
Program Files       Program Files (x86) Riot Games          Users              
Windows             workspace                                                  
```

6. 

Comando

```
PS C:\Users\Desktop> Get-ChildItem -Path C:\Windows | where -filter {$_.Name -like "*.exe"} | Format-List -Property Name, VersionInfo, @{Name='Size';Expression={$_.length}}
```

Resultado

```
Name        : bfsvc.exe
VersionInfo : File:             C:\Windows\bfsvc.exe
              InternalName:     bfsvc.exe
              OriginalFilename: bfsvc.exe.mui
              FileVersion:      xxxxxxxxxxxxxxxxxx
              FileDescription:  Utilidad de servicio de actualización del 
              archivo de arranque
              Product:          Sistema operativo Microsoft® Windows®
              ProductVersion:   xxxxxxxxx
              Debug:            False
              Patched:          False
              PreRelease:       False
              PrivateBuild:     False
              SpecialBuild:     False
              Language:         Español (España, internacional)
              
Size        : 73216
```


7. 

Comando

```
PS C:\Users\Desktop> Import-Module NetAdapter

PS C:\Users\Desktop> Get-NetAdapter | where -filter {$_.Virtual -eq $false} | Format-List
```

Resultado

```
Name                       : Npcap Loopback Adapter
InterfaceDescription       : Npcap Loopback Adapter
InterfaceIndex             : 15
MacAddress                 : xxxxxxxxxxxxxxxxxxxx
MediaType                  : 802.3
PhysicalMediaType          : Unspecified
InterfaceOperationalStatus : Up
AdminStatus                : Up
LinkSpeed(Gbps)            : 1.2
MediaConnectionState       : Connected
ConnectorPresent           : True
DriverInformation          : Driver Date xxxx-xx-xx Version xx.xx.xxx
                           

Name                       : Ethernet
InterfaceDescription       : Realtek PCIe GbE Family Controller
InterfaceIndex             : 12
MacAddress                 : xxxxxxxxxxxxxxxxxx
MediaType                  : 802.3
PhysicalMediaType          : 802.3
InterfaceOperationalStatus : Up
AdminStatus                : Up
LinkSpeed(Gbps)            : 1
MediaConnectionState       : Connected
ConnectorPresent           : True
DriverInformation          : Driver Date 0000-00-00 Version x.x.xxx.xxx 
                             6.40
```

8.  

Comando

```
PS C:\Users\Desktop> Import-Module DnsClient

PS C:\Users\Desktop> Get-DnsClientCache | where -filter {$_.Type -eq (28) -or $_.Type -eq (1)} | Format-Table
```

Resultado

```
Entry      : xxxxxxxxxxxxxxxx
RecordName : xxxxxxxxxxxxxxxx
RecordType : A
Status     : Success
Section    : Answer
TimeToLive : xxx
DataLength : xxx
Data       : xxxxxxxxxxxxxx
```

9.

Comando

```
PS C:\Users\Desktop> Get-ChildItem -Path C:\Windows\System32 | where -filter {$_.Name -like "*.exe" -and $_.length/1MB -gt 5} | Format-Table
```

Resultado

```
Mode                LastWriteTime         Length Name                          
----                -------------         ------ ----                          
-a----     14/03/2020  3:26 p. m.            xx  xxx.exe                       
-a----     18/03/2020  7:54 p. m.            xx  xxxxx.exe 
```

10. 

Comando

```
Get-HotFix | where -filter {$_.description -like "*security*"} | Format-List
```

11.

Comando

```
Get-HotFix | where -filter {$_.installedBy -like "*SYSTEM*"} |Format-List
```

12.

Comando

```
Get-Process | where -filter {$_.Name -eq "Conhost" -or $_.Name -eq "Svchost"} | Format-List
```
