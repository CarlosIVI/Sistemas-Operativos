1. 
   Comando
  
   ```
   PS C:\Users\Desktop> Get-CimInstance win32_networkadapterconfiguration | Select-Object IP
   ```
   
   Resultado
   
   ```
   Description             : Microsoft Kernel Debug Network Adapter
   Index                   : 0
   IPAddress               : 
   IPConnectionMetric      : 
   IPEnabled               : False
   IPFilterSecurityEnabled : 
   ```

2.
   Comandos

   ```
   PS C:\Users\Desktop>  Get-WmiObject win32_quickfixengineering
   ```
   
   Resultado
  
   ```  
   
   Source        Description      HotFixID      InstalledBy          InstalledOn  
   ------        -----------      --------      -----------          -----------  
   DESKTOP-RG... Update           XXXXXXXXX     NT AUTHORITY\SYSTEM  23/02/2020...
   DESKTOP-RG... Security Update  XXXXXXXXX                          1/04/2019 ...
   DESKTOP-RG... Security Update  XXXXXXXXX     NT AUTHORITY\SYSTEM  25/06/2019...
   DESKTOP-RG... Security Update  XXXXXXXXX     NT AUTHORITY\SYSTEM  25/06/2019...
   DESKTOP-RG... Security Update  XXXXXXXXX     NT AUTHORITY\SYSTEM  16/08/2019...
   DESKTOP-RG... Security Update  XXXXXXXXX     NT AUTHORITY\SYSTEM  10/07/2019...
   
   ```
   
   
3. 
   Comando

   ```
   PS C:\Users\Desktop> Get-WmiObject win32_service | Select-Object Status, Startmode, Systemname
   ```
   Resultado
   
   ```
   Status Startmode Systemname     
   ------ --------- ----------     
   OK     Auto      DESKTOP-RGRE5A8
   OK     Manual    DESKTOP-RGRE5A8
   OK     Auto      DESKTOP-RGRE5A8
   OK     Manual    DESKTOP-RGRE5A8
   OK     Manual    DESKTOP-RGRE5A8
   OK     Manual    DESKTOP-RGRE5A8
   
   ```
   
   
4. 
   Comandos

   ```
   PS C:\Users\Desktop> Get-CimClass -Namespace root/SecurityCenter2 | where -Filter {$_.CimClassName -like "*product*"}
   ```
   
   Resultado
   
   ```
   CimClassName                        CimClassMethods      CimClassProperties    
   ------------                        ---------------      ------------------    
   AntiSpywareProduct                  {}                   {displayName, insta...
   AntiVirusProduct                    {}                   {displayName, insta...
   FirewallProduct                     {}                   {displayName, insta...
   
   ```
   
5. 
   Comando sin antivirus
   
   ```
   PS C:\Users\Desktop> Get-CimInstance -Namespace root/SecurityCenter2 -ClassName AntiSpywareProduct | Select-Object DisplayName
   ```
   Comando con antivirus:
   
   ```
   PS C:\Users\Desktop> Get-CimInstance -Namespace root/SecurityCenter2 -ClassName AntiVirusProduct | Select-Object DisplayName
   ```
   
   Resultado
   
   ```
   DisplayName     
   -----------     
   Windows Defender
   Kaspersky Free  
   ```
   
