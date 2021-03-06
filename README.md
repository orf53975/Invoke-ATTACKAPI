# Invoke-ATTACKAPI
A PowerShell script to interact with the MITRE ATT&amp;CK Framework via its own API in order to gather information about techniques, 
tactics, groups, software and references provided by the MITRE ATT&CK Team @MITREattack. **THIS SCRIPT IS STILL USING THE DEPRECATED MEEDIAWIKI API. IT HAS NOT BEEN UPDATED YET TO USE THE PUBLIC TAXII SERVERS API**

# Goals
* Provide an easy way to interact with the MITRE ATT&CK Framework via its own API and PowerShell to the community.
* Expedite the acquisition of data from ATT&CK when preparing for a Hunting Campaign.
* Learn PowerShell Dynamic Parameters :) 

# Resources
* [MITRE ATT&CK API](https://attack.mitre.org/wiki/Using_the_API)
* [Semantic MediaWiki API](https://www.semantic-mediawiki.org/wiki/Help:API)
* [Get-ATTack](https://github.com/SadProcessor/SomeStuff/blob/master/Get-ATTaCK.ps1)
  * Walter Legowski [@SadProcessor](https://twitter.com/SadProcessor) 

# Getting Started

## Requirements
* PowerShell version 3+

## Installing /Importing
```
git clone https://github.com/Cyb3rWard0g/Invoke-ATTACKAPI.git
cd Invoke-ATTACKAPI
Import-Module .\Invoke-ATTACKAPI.ps1

  /$$$$$$  /$$$$$$$$ /$$$$$$$$ /$$$      /$$$$$$  /$$   /$$        /$$$$$$  /$$$$$$$  /$$$$$$
 /$$__  $$|__  $$__/|__  $$__//$$ $$    /$$__  $$| $$  /$$/       /$$__  $$| $$__  $$|_  $$_/
| $$  \ $$   | $$      | $$  |  $$$    | $$  \__/| $$ /$$/       | $$  \ $$| $$  \ $$  | $$
| $$$$$$$$   | $$      | $$   /$$ $$/$$| $$      | $$$$$/        | $$$$$$$$| $$$$$$$/  | $$
| $$__  $$   | $$      | $$  | $$  $$_/| $$      | $$  $$        | $$__  $$| $$____/   | $$
| $$  | $$   | $$      | $$  | $$\  $$ | $$    $$| $$\  $$       | $$  | $$| $$        | $$
| $$  | $$   | $$      | $$  |  $$$$/$$|  $$$$$$/| $$ \  $$      | $$  | $$| $$       /$$$$$$
|__/  |__/   |__/      |__/   \____/\_/ \______/ |__/  \__/      |__/  |__/|__/      |______/ V.0.9[BETA]

            Adversarial Tactics, Techniques & Common Knowledge API

[*] Author: Roberto Rodriguez @Cyb3rWard0g

[++] Pulling MITRE ATT&CK Data

```

## Examples
### This query matches all techniques
```
Invoke-ATTACKAPI -Category -Technique

ID                  : {T1001}
Bypass              : {}
Contributor         : {}
Requires System     : {}
Data Source         : {Packet capture, Process use of network, Process monitoring, Network protocol analysis}
Description         : {Command and control (C2) communications are hidden (but not necessarily encrypted) in an
                      attempt to make the content more difficult to discover or decipher and to make the
                      communication less conspicuous and hide commands from being seen. This encompasses many
                      methods, such as adding junk data to protocol traffic, using steganography, commingling
                      legitimate traffic with C2 communications traffic, or using a non-standard data encoding
                      system, such as a modified Base64 encoding for the message body of an HTTP request.}
Mitigation          : {Network intrusion detection and prevention systems that use network signatures to
                      identify traffic for specific adversary malware can be used to mitigate activity at the
                      network level. Signatures are often for unique indicators within protocols and may be
                      based on the specific obfuscation technique used by a particular adversary or tool, and
                      will likely be different across various malware families and versions. Adversaries will
                      likely change tool C2 signatures over time or construct protocols in such a way as to
                      avoid detection by common defensive tools.[[CiteRef::University of Birmingham C2]]}
Tactic              : Command and Control
Analytic Details    : {Analyze network data for uncommon data flows (e.g., a client sending significantly more
                      data than it receives from a server). Processes utilizing the network that do not normally

                      have network communication or have never been seen before are suspicious. Analyze packet
                      contents to detect communications that do not follow the expected protocol behavior for
                      the port that is being used.[[CiteRef::University of Birmingham C2]]}
TechniqueName       : {Data Obfuscation}
FullText            : Technique/T1001
Link Text           : {[[Technique/T1001|Data Obfuscation]]}
Reference           : {University of Birmingham C2, FireEye APT28, Axiom, FireEye APT30...}
Platform            : {Windows Server 2003, Windows Server 2008, Windows Server 2012, Windows XP...}
Name                : {Data Obfuscation}
CAPEC ID            : {}
Requires Permission : {}
URL                 : https://attack.mitre.org/wiki/Technique/T1001
.............
..................

ID                  : {T1068}
Bypass              : {Anti-virus, System access controls}
Contributor         : {John Lambert, Microsoft Threat Intelligence Center}
Requires System     : {Unpatched software or otherwise vulnerable target. Depending on the target and goal, the
                      system and exploitable service may need to be remotely accessible from the internal
                      network. In the case of privilege escalation, the adversary likely already has user
                      permissions on the target system.}
Data Source         : {Windows Error Reporting, File monitoring, Process monitoring}
Description         : {Exploitation of a software vulnerability occurs when an adversary takes advantage of a
                      programming error in a program, service, or within the operating system software or
                      kernel itself to execute adversary-controlled code. Exploiting software vulnerabilities
                      may allow adversaries to run a command or binary on a remote system for lateral movement,
                      escalate a current process to a higher privilege level, or bypass security mechanisms.
                      Exploits may also allow an adversary access to privileged accounts and credentials. One
                      example of this is MS14-068, which can be used to forge Kerberos tickets using domain
                      user permissions.[[CiteRef::Technet MS14-068]][[CiteRef::ADSecurity Detecting Forged
                      Tickets]]}
Mitigation          : {Update software regularly by employing patch management for internal enterprise
                      endpoints and servers. Develop a robust cyber threat intelligence capability to determine
                      what types and levels of threat may use software exploits and 0-days against a particular
                      organization. Make it difficult for adversaries to advance their operation through
                      exploitation of undiscovered or unpatched vulnerabilities by using sandboxing,
                      virtualization, and exploit prevention tools such as the Microsoft Enhanced Mitigation
                      Experience Toolkit.[[CiteRef::SRD EMET]]}
Tactic              : {Credential Access, Defense Evasion, Lateral Movement, Privilege Escalation}
Analytic Details    : {Software exploits may not always succeed or may cause the exploited process to become
                      unstable or crash. Software and operating system crash reports may contain useful
                      contextual information about attempted exploits that correlate with other malicious
                      activity. Exploited processes may exhibit behavior that is unusual for the specific
                      process, such as spawning additional processes or reading and writing to files.}
TechniqueName       : {Exploitation of Vulnerability}
FullText            : Technique/T1068
Link Text           : {[[Technique/T1068|Exploitation of Vulnerability]]}
Reference           : {ADSecurity Detecting Forged Tickets, Bitdefender APT28 Dec 2015, ESET Sednit July 2015,
                      ESET Sednit Part 1...}
Platform            : {Windows Server 2003, Windows Server 2008, Windows Server 2012, Windows XP...}
Name                : {Exploitation of Vulnerability}
CAPEC ID            : {69}
Requires Permission : {User, Administrator, SYSTEM}
URL                 : https://attack.mitre.org/wiki/Technique/T1068
```

### This query matches the page Technique with ID T1014
```
Invoke-ATTACKAPI -Category -Technique -ID T1014

ID                  : {T1014}
Bypass              : {Anti-virus, File monitoring, Host intrusion prevention systems, Process whitelisting...}
Contributor         : {}
Requires System     : {}
Data Source         : {BIOS, MBR, System calls}
Description         : {Rootkits are programs that hide the existence of malware by intercepting and modifying
                      operating system API calls that supply system information. Rootkits or rootkit enabling
                      functionality may reside at the user or kernel level in the operating system or lower, to
                      include a [[Technique/T1062|Hypervisor]], Master Boot Record, or the
                      [[Technique/T1019|System Firmware]].[[CiteRef::Wikipedia Rootkit]]

                      Adversaries may use rootkits to hide the presence of programs, files, network
                      connections, services, drivers, and other system components.}
Mitigation          : {Identify potentially malicious software that may contain rootkit functionality, and
                      audit and/or block it by using whitelisting[[CiteRef::Beechey 2010]] tools, like
                      AppLocker,[[CiteRef::Windows Commands JPCERT]][[CiteRef::NSA MS AppLocker]] or Software
                      Restriction Policies[[CiteRef::Corio 2008]] where appropriate.[[CiteRef::TechNet
                      Applocker vs SRP]]}
Tactic              : Defense Evasion
Analytic Details    : {Some rootkit protections may be built into anti-virus or operating system software.
                      There are dedicated rootkit detection tools that look for specific types of rootkit
                      behavior. Monitor for the existence of unrecognized DLLs, devices, services, and changes
                      to the MBR.[[CiteRef::Wikipedia Rootkit]]}
TechniqueName       : {Rootkit}
FullText            : Technique/T1014
Link Text           : {[[Technique/T1014|Rootkit]]}
Reference           : {Wikipedia Rootkit, Beechey 2010, Windows Commands JPCERT, NSA MS AppLocker...}
Platform            : {Windows Server 2003, Windows Server 2008, Windows Server 2012, Windows XP...}
Name                : {Rootkit}
CAPEC ID            : {}
Requires Permission : {Administrator, SYSTEM}
URL                 : https://attack.mitre.org/wiki/Technique/T1014
```

### This query matches against all the group that use a specific software (in this case Cobalt Strike). SYNTAX: "Software: \<tool name>"
```
Invoke-ATTACKAPI -Category -Group -Tool 'Software: Cobalt Strike'

Tool          : {Software: Cobalt Strike, Software: KOMPROGO, Software: WINDSHIELD, Software: SOUNDBITE...}
Alias         : {APT32, OceanLotus Group}
ID            : {G0050}
URL           : https://attack.mitre.org/wiki/Group/G0050
TechniqueName : {Scheduled Task, Regsvr32, PowerShell, Custom Command and Control Protocol...}
FullText      : Group/G0050
Reference     : {FireEye APT32 May 2017, GitHub Malleable C2, GitHub Invoke-Obfuscation}
Link Text     : {[[Group/G0050|APT32]]}
Name          : {APT32}
Description   : {[[Group/G0050|APT32]] is a threat group that has been active since at least 2014. The group
                has targeted multiple private sector industries as well as with foreign governments,
                dissidents, and journalists. The group's operations are aligned with Vietnamese state
                interests.[[CiteRef::FireEye APT32 May 2017]]}
TechniqueID   : {Technique/T1053, Technique/T1117, Technique/T1086, Technique/T1094...}
Display Title : Group: APT32, OceanLotus Group
```

### [BETA] Exporting custom results to a CSV
```
Invoke-ATTACKAPI -Category -Technique | where-object -Property ID -GE "T1134" | 
select @{Name="Name"; Expression={$_.Name -join ","}}, @{Name="Tactic"; Expression={$_.Tactic -join ","}}, 
@{Name ="ID"; Expression={$_.ID -join ","}}, @{Name="Description"; Expression={$_.Description -join ","}}, 
@{Name="Analytic details"; Expression={$_.'Analytic Details' -join ","}}, @{Name="Data Source";
Expression={$_.'Data Source' -join ","}}  | export-csv F:\wardog\scripts\demo6.csv -NoTypeInformation
```

### Showing an up to date ATT&CK Matrix for Enterprise
```
Invoke-ATTACKAPI -Matrix | select Persistence, 'Privilege Escalation', 'Defense Evasion','Credential Access', Discovery, 'Lateral Movement', Execution, Collection, Exfiltration, 'Command and Control' | ft

Persistence                                           Privilege Escalation                  Defense Evasion                         Credential Access                      Discovery                              Lateral Movement                    Execution
-----------                                           --------------------                  ---------------                         -----------------                      ---------                              ----------------                    ---------
.bash_profile and .bashrc                             Access Token Manipulation             Access Token Manipulation               Account Manipulation                   Account Discovery                      AppleScript                         AppleScript
Accessibility Features                                Accessibility Features                Binary Padding                          Bash History                           Application Window Discovery           Application Deployment Software     Application Shimming
AppInit DLLs                                          AppInit DLLs                          Bypass User Account Control             Brute Force                            File and Directory Discovery           Exploitation of Vulnerability       Command-Line Interface
Application Shimming                                  Application Shimming                  Clear Command History                   Create Account                         Network Service Scanning               Logon Scripts                       Execution through API
Authentication Package                                Bypass User Account Control           Code Signing                            Credential Dumping                     Network Share Discovery                Pass the Hash                       Execution through Mod...
Bootkit                                               DLL Injection                         Component Firmware                      Credentials in Files                   Peripheral Device Discovery            Pass the Ticket                     Graphical User Interface
Change Default File Association                       DLL Search Order Hijacking            Component Object Model Hijacking        Exploitation of Vulnerability          Permission Groups Discovery            Remote Desktop Protocol             InstallUtil
Component Firmware                                    Dylib Hijacking                       Deobfuscate/Decode Files or Information Input Capture                          Process Discovery                      Remote File Copy                    Launchctl
Component Object Model Hijacking                      Exploitation of Vulnerability         Disabling Security Tools                Input Prompt                           Query Registry                         Remote Services                     PowerShell
Cron Job                                              File System Permissions Weakness      DLL Injection                           Keychain                               Remote System Discovery                Replication Through Removable Media Process Hollowing
DLL Search Order Hijacking                            Launch Daemon                         DLL Search Order Hijacking              Network Sniffing                       Security Software Discovery            Shared Webroot                      Regsvcs/Regasm
Dylib Hijacking                                       Local Port Monitor                    DLL Side-Loading                        Private Keys                           System Information Discovery           Taint Shared Content                Regsvr32
External Remote Services                              New Service                           Exploitation of Vulnerability           Securityd Memory                       System Network Configuration Discovery Third-party Software                Rundll32
File System Permissions Weakness                      Path Interception                     File Deletion                           Two-Factor Authentication Interception System Network Connections Discovery   Windows Admin Shares                Scheduled Task
Hidden Files and Directories                          Plist Modification                    File System Logical Offsets                                                    System Owner/User Discovery            Windows Remote Management           Scripting
Hypervisor                                            Scheduled Task                        Gatekeeper Bypass                                                              System Service Discovery                                                   Service Execution
Launch Agent                                          Service Registry Permissions Weakness Hidden Files and Directories                                                   System Time Discovery                                                      Source
Launch Daemon                                         Setuid and Setgid                     Hidden Users                                                                                                                                              Space after Filename
Launchctl                                             Startup Items                         Hidden Window                                                                                                                                             Third-party Software
LC_LOAD_DYLIB Addition                                Sudo                                  HISTCONTROL                                                                                                                                               Trap
Local Port Monitor                                    Valid Accounts                        Indicator Blocking                                                                                                                                        Trusted Developer Uti...
Login Item                                            Web Shell                             Indicator Removal from Tools                                                                                                                              Windows Management In...
Logon Scripts                                                                               Indicator Removal on Host                                                                                                                                 Windows Remote Manage...
Modify Existing Service                                                                     Install Root Certificate
Netsh Helper DLL                                                                            InstallUtil
New Service                                                                                 Launchctl
Office Application Startup                                                                  LC_MAIN Hijacking
Path Interception                                                                           Masquerading
Plist Modification                                                                          Modify Registry
Rc.common                                                                                   Network Share Connection Removal
Redundant Access                                                                            NTFS Extended Attributes
Registry Run Keys / Start Folder                                                            Obfuscated Files or Information
Re-opened Applications                                                                      Plist Modification
Scheduled Task                                                                              Process Hollowing
Security Support Provider                                                                   Redundant Access
Service Registry Permissions Weakness                                                       Regsvcs/Regasm
Shortcut Modification                                                                       Regsvr32
Startup Items                                                                               Rootkit
System Firmware                                                                             Rundll32
Trap                                                                                        Scripting
Valid Accounts                                                                              Software Packing
Web Shell                                                                                   Space after Filename
Windows Management Instrumentation Event Subscription                                       Timestomp
Winlogon Helper DLL                                                                         Trusted Developer Utilities
                                                                                            Valid Accounts
```

### Getting an up to date ATT&CK Matrix for Enterprise and exporting it to a csv file
```
Invoke-ATTACKAPI -Matrix | select Persistence, 'Privilege Escalation', 'Defense Evasion','Credential Access',
Discovery, 'Lateral Movement', Execution, Collection, Exfiltration, 'Command and Control' | 
Export-Csv C:\wardog\scripts\matrix.csv -NoTypeInformation
```

### Showing an up to date table of Groups/APTs with the techniques and tools attributed to them
```
Invoke-ATTACKAPI -Attribution | ft

Group     Group Alias                                        Group ID Tactic                                  TechniqueName                           TechniqueID     Tool
-----     -----------                                        -------- ------                                  -------------                           -----------     ----
admin@338 admin@338                                          G0018    Discovery                               System Time Discovery                   Technique/T1124 Software: Net, net.exe
admin@338 admin@338                                          G0018    Defense Evasion                         Network Share Connection Removal        Technique/T1126 Software: Net, net.exe
admin@338 admin@338                                          G0018    Command and Control                     Commonly Used Port                      Technique/T1043 Software: LOWBALL
admin@338 admin@338                                          G0018    {Command and Control, Lateral Movement} Remote File Copy                        Technique/T1105 Software: LOWBALL
admin@338 admin@338                                          G0018    Discovery                               System Network Connections Discovery    Technique/T1049 Software: netstat, netstat.exe
admin@338 admin@338                                          G0018    Discovery                               System Information Discovery            Technique/T1082 Software: BUBBLEWRAP, Backdoor.APT...
admin@338 admin@338                                          G0018    Discovery                               Account Discovery                       Technique/T1087
admin@338 admin@338                                          G0018    Execution                               Command-Line Interface                  Technique/T1059
admin@338 admin@338                                          G0018    Discovery                               System Service Discovery                Technique/T1007
admin@338 admin@338                                          G0018    Defense Evasion                         Masquerading                            Technique/T1036
admin@338 admin@338                                          G0018    Discovery                               Remote System Discovery                 Technique/T1018 Software: Net, net.exe
admin@338 admin@338                                          G0018    Discovery                               System Network Connections Discovery    Technique/T1049 Software: Net, net.exe
admin@338 admin@338                                          G0018    Lateral Movement                        Windows Admin Shares                    Technique/T1077 Software: Net, net.exe
admin@338 admin@338                                          G0018    {Defense Evasion, Privilege Escalation} DLL Injection                           Technique/T1055 Software: PoisonIvy, Poison Ivy
admin@338 admin@338                                          G0018    Discovery                               System Service Discovery                Technique/T1007 Software: Net, net.exe
admin@338 admin@338                                          G0018    Discovery                               Account Discovery                       Technique/T1087 Software: Net, net.exe
admin@338 admin@338                                          G0018    Command and Control                     Standard Non-Application Layer Protocol Technique/T1095 Software: BUBBLEWRAP, Backdoor.APT...
admin@338 admin@338                                          G0018    Discovery                               System Information Discovery            Technique/T1082 Software: Systeminfo, systeminfo.exe
admin@338 admin@338                                          G0018    Credential Access                       Create Account                          Technique/T1136 Software: Net, net.exe
admin@338 admin@338                                          G0018    Discovery                               Permission Groups Discovery             Technique/T1069
admin@338 admin@338                                          G0018    Discovery                               Network Share Discovery                 Technique/T1135 Software: Net, net.exe
admin@338 admin@338                                          G0018    Command and Control                     Web Service                             Technique/T1102 Software: LOWBALL
admin@338 admin@338                                          G0018    Execution                               Service Execution                       Technique/T1035 Software: Net, net.exe
admin@338 admin@338                                          G0018    Discovery                               File and Directory Discovery            Technique/T1083
admin@338 admin@338                                          G0018    Discovery                               Permission Groups Discovery             Technique/T1069 Software: Net, net.exe
admin@338 admin@338                                          G0018    Discovery                               System Network Connections Discovery    Technique/T1049
admin@338 admin@338                                          G0018    Discovery                               System Information Discovery            Technique/T1082
admin@338 admin@338                                          G0018    Command and Control                     Standard Application Layer Protocol     Technique/T1071 Software: LOWBALL
admin@338 admin@338                                          G0018    Command and Control                     Standard Cryptographic Protocol         Technique/T1032 Software: PoisonIvy, Poison Ivy
admin@338 admin@338                                          G0018    {Collection, Credential Access}         Input Capture                           Technique/T1056 Software: PoisonIvy, Poison Ivy
admin@338 admin@338                                          G0018    Command and Control                     Standard Application Layer Protocol     Technique/T1071 Software: BUBBLEWRAP, Backdoor.APT...
admin@338 admin@338                                          G0018    Discovery                               System Network Configuration Discovery  Technique/T1016 Software: ipconfig, ipconfig.exe
admin@338 admin@338                                          G0018    Discovery                               System Network Configuration Discovery  Technique/T1016
APT1      {APT1, Comment Crew, Comment Group, Comment Panda} G0006    Collection                              Data from Local System                  Technique/T1005
APT1      {APT1, Comment Crew, Comment Group, Comment Panda} G0006    Execution                               Service Execution                       Technique/T1035 Software: xCmd
APT1      {APT1, Comment Crew, Comment Group, Comment Panda} G0006    Lateral Movement                        Pass the Hash                           Technique/T1075 Software: Pass-The-Hash Toolkit
APT1      {APT1, Comment Crew, Comment Group, Comment Panda} G0006    Execution                               Service Execution                       Technique/T1035 Software: Net, net.exe
APT1      {APT1, Comment Crew, Comment Group, Comment Panda} G0006    Discovery                               Remote System Discovery                 Technique/T1018 Software: Net, net.exe
APT1      {APT1, Comment Crew, Comment Group, Comment Panda} G0006    Collection                              Email Collection                        Technique/T1114
APT1      {APT1, Comment Crew, Comment Group, Comment Panda} G0006    Lateral Movement                        Pass the Hash                           Technique/T1075
```

### Showing an up to date table of the techniques and tools attributed to a Group/APT with Group ID G0051 (FIN7)
```
Invoke-ATTACKAPI -Attribution | Where-Object -Property 'Group ID' -EQ 'G0046' | ft

Group Group Alias Group ID Tactic                                         TechniqueName                       TechniqueID     Tool                                Description
----- ----------- -------- ------                                         -------------                       -----------     ----                                -----------
FIN7  FIN7        G0046    Discovery                                      Process Discovery                   Technique/T1057 Software: HALFBAKED                 {[[Software/S0151|HALFBAKED]] can obtain information about running processes on the victim.[[CiteRef::Fir...
FIN7  FIN7        G0046    Persistence                                    Registry Run Keys / Start Folder    Technique/T1060                                     {[[Group/G0046|FIN7]] malware has created a Registry Run key pointing to its malicious LNK file to establ...
FIN7  FIN7        G0046    Discovery                                      Query Registry                      Technique/T1012 Software: POWERSOURCE, DNSMessenger {[[Software/S0145|POWERSOURCE]] queries Registry keys in preparation for setting Run keys to achieve pers...
FIN7  FIN7        G0046    Persistence                                    Registry Run Keys / Start Folder    Technique/T1060 Software: POWERSOURCE, DNSMessenger {[[Software/S0145|POWERSOURCE]] achieves persistence by setting a Registry Run key, with the path dependi...
FIN7  FIN7        G0046    {Command and Control, Lateral Movement}        Remote File Copy                    Technique/T1105 Software: POWERSOURCE, DNSMessenger {[[Software/S0145|POWERSOURCE]] has been observed being used to download [[Software/S0146|TEXTMATE]] and ...
FIN7  FIN7        G0046    {Execution, Persistence, Privilege Escalation} Application Shimming                Technique/T1138                                     {[[Group/G0046|FIN7]] has used application shim databases for persistence.[[CiteRef::FireEye FIN7 Shim Da...
FIN7  FIN7        G0046    {Execution, Persistence, Privilege Escalation} Scheduled Task                      Technique/T1053                                     {[[Group/G0046|FIN7]] malware has created scheduled tasks to establish persistence.[[CiteRef::FireEye FIN...
FIN7  FIN7        G0046    Command and Control                            Standard Application Layer Protocol Technique/T1071 Software: Carbanak, Anunak          {The [[Software/S0030|Carbanak]] malware communicates to its command server using HTTP with an encrypted ...
FIN7  FIN7        G0046    Collection                                     Screen Capture                      Technique/T1113 Software: HALFBAKED                 {[[Software/S0151|HALFBAKED]] can obtain screenshots from the victim.[[CiteRef::FireEye FIN7 April 2017]]}
FIN7  FIN7        G0046    Command and Control                            Standard Application Layer Protocol Technique/T1071 Software: POWERSOURCE, DNSMessenger {[[Software/S0145|POWERSOURCE]] uses DNS TXT records for C2.[[CiteRef::FireEye FIN7 March 2017]][[CiteRef...
FIN7  FIN7        G0046    Execution                                      Windows Management Instrumentation  Technique/T1047 Software: HALFBAKED                 {[[Software/S0151|HALFBAKED]] can use WMI queries to gather system information.[[CiteRef::FireEye FIN7 Ap...
FIN7  FIN7        G0046    Command and Control                            Standard Application Layer Protocol Technique/T1071 Software: TEXTMATE, DNSMessenger    {[[Software/S0146|TEXTMATE]] uses DNS TXT records for C2.[[CiteRef::FireEye FIN7 March 2017]]}
FIN7  FIN7        G0046    Discovery                                      System Information Discovery        Technique/T1082 Software: HALFBAKED                 {[[Software/S0151|HALFBAKED]] can obtain information about the OS, processor, and BIOS.[[CiteRef::FireEye...
FIN7  FIN7        G0046    {Collection, Credential Access}                Input Capture                       Technique/T1056 Software: Carbanak, Anunak          {[[Software/S0030|Carbanak]] contains keylogger functionality.[[CiteRef::Kaspersky Carbanak]]}
FIN7  FIN7        G0046    Command and Control                            Standard Cryptographic Protocol     Technique/T1032 Software: Carbanak, Anunak          {[[Software/S0030|Carbanak]] encrypts the message body of HTTP traffic with RC2 and Base64 encoding.[[Cit...
FIN7  FIN7        G0046    Execution                                      PowerShell                          Technique/T1086 Software: HALFBAKED                 {[[Software/S0151|HALFBAKED]] can execute PowerShell scripts.[[CiteRef::FireEye FIN7 April 2017]]}
FIN7  FIN7        G0046    {Command and Control, Lateral Movement}        Remote File Copy                    Technique/T1105                                     {[[Group/G0046|FIN7]] uses a PowerShell script to launch shellcode that retrieves an additional payload.[...
FIN7  FIN7        G0046    Execution                                      PowerShell                          Technique/T1086 Software: POWERSOURCE, DNSMessenger {[[Software/S0145|POWERSOURCE]] is a PowerShell backdoor.[[CiteRef::FireEye FIN7 March 2017]][[CiteRef::C...
FIN7  FIN7        G0046    Execution                                      PowerShell                          Technique/T1086                                     {[[Group/G0046|FIN7]] uses a PowerShell script to launch shellcode that retrieves an additional payload.[...
FIN7  FIN7        G0046    Defense Evasion                                Masquerading                        Technique/T1036                                     {[[Group/G0046|FIN7]] has created a scheduled task named “AdobeFlashSync” to establish persistence.[[Cite...
FIN7  FIN7        G0046    Defense Evasion                                Obfuscated Files or Information     Technique/T1027 Software: POWERSOURCE, DNSMessenger {If the victim is using PowerShell 3.0 or later, [[Software/S0145|POWERSOURCE]] writes its decoded payloa...
FIN7  FIN7        G0046    Defense Evasion                                File Deletion                       Technique/T1107 Software: HALFBAKED                 {[[Software/S0151|HALFBAKED]] can delete a specified file.[[CiteRef::FireEye FIN7 April 2017]]}
FIN7  FIN7        G0046    Execution                                      Command-Line Interface              Technique/T1059 Software: TEXTMATE, DNSMessenger    {[[Software/S0146|TEXTMATE]] executes cmd.exe to provide  a reverse shell to attackers.[[CiteRef::FireEye...
```

### Getting an up to date table of Groups/APTs with the techniques and tools attributed to them and exporting it to a csv file
```
Invoke-ATTACKAPI -Attribution | select Group, 'Group Alias','Group ID', Tactic, TechniqueName,
TechniqueID, Tool, @{Name='Description'; Expression={$_.Description}}, 'Data Source'|
 export-csv -NoTypeInformation C:\Documents\ATTACK_Attribution.csv
```

### Showing an up to date table with all the valuable information from the MITRE ATTACK DB at once
```
Invoke-ATTACKAPI -All | ft

Tactic      TechniqueName           TechniqueID     Group             Group Alias                                         Group ID Tool
------      -------------           -----------     -----             -----------                                         -------- ----
Collection  Screen Capture          Technique/T1113 APT28             {APT28, Sednit, Sofacy, Pawn Storm...}              G0007
Collection  Screen Capture          Technique/T1113 APT28             {APT28, Sednit, Sofacy, Pawn Storm...}              G0007    Software: XAgentOSX
Collection  Data from Local System  Technique/T1005 APT1              {APT1, Comment Crew, Comment Group, Comment Panda}  G0006
Collection  Screen Capture          Technique/T1113 Cleaver           {Cleaver, TG-2889, Threat Group 2889}               G0003    Software: TinyZBot
Collection  Screen Capture          Technique/T1113 APT32             {APT32, OceanLotus Group}                           G0050    Software: Cobalt Strike
Collection  Screen Capture          Technique/T1113 APT29             {APT29, The Dukes, Cozy Bear}                       G0016    Software: CosmicDuke, TinyBaron,...
Collection  Data Staged             Technique/T1074 APT30             APT30                                               G0013    Software: SPACESHIP
Collection  Data from Local System  Technique/T1005 Ke3chang          Ke3chang                                            G0004
Collection  Data from Local System  Technique/T1005 Lazarus Group     {Lazarus Group, HIDDEN COBRA, Guardians of Peace}   G0032
Collection  Data from Local System  Technique/T1005 APT29             {APT29, The Dukes, Cozy Bear}                       G0016    Software: CosmicDuke, TinyBaron,...
Collection  Data from Local System  Technique/T1005 APT29             {APT29, The Dukes, Cozy Bear}                       G0016    Software: PinchDuke
Collection  Data from Local System  Technique/T1005 APT30             APT30                                               G0013    Software: FLASHFLOOD
Collection  Screen Capture          Technique/T1113 RTM               RTM                                                 G0048    Software: RTM
Collection  Screen Capture          Technique/T1113 MONSOON           {MONSOON, Operation Hangover}                       G0042    Software: BADNEWS
Collection  Screen Capture          Technique/T1113 menuPass          {menuPass, Stone Panda, APT10, Red Apollo...}       G0045    Software: RedLeaves, BUGJUICE
Collection  Email Collection        Technique/T1114 APT29             {APT29, The Dukes, Cozy Bear}                       G0016    Software: SeaDuke, SeaDaddy, Sea...
Collection  Email Collection        Technique/T1114 APT1              {APT1, Comment Crew, Comment Group, Comment Panda}  G0006
Collection  Screen Capture          Technique/T1113 Sandworm Team     {Sandworm Team, Quedagh}                            G0034    Software: BlackEnergy, Black Energy
Collection  Screen Capture          Technique/T1113 FIN7              FIN7                                                G0046    Software: HALFBAKED
Collection  Screen Capture          Technique/T1113 Dust Storm        Dust Storm                                          G0031    Software: ZLib
Collection  Screen Capture          Technique/T1113 Dragonfly         {Dragonfly, Energetic Bear}                         G0035    Software: Trojan.Karagany
Collection  Screen Capture          Technique/T1113 menuPass          {menuPass, Stone Panda, APT10, Red Apollo...}       G0045    Software: EvilGrab
Collection  Screen Capture          Technique/T1113 Group5            Group5                                              G0043
Collection  Screen Capture          Technique/T1113 Gamaredon Group   Gamaredon Group                                     G0047    Software: Pteranodon
Collection  Data Staged             Technique/T1074 APT30             APT30                                               G0013    Software: FLASHFLOOD
```

### Getting an up to date table with all the valuable information from the MITRE ATTACK DB at once and exporting it to a csv file
```
Invoke-ATTACKAPI -All | select @{Name='Tactic'; Expression={$_.tactic -join ','}}, @{Name='TechniqueName';
Expression={$_.techniquename -join ','}}, techniqueID, group, @{Name='Group Alias'; Expression={$_.'Group alias'
-join ','}}, 'Group ID', @{Name='Tool'; Expression={$_.Tool -join ','}}, @{Name='Description'; 
Expression={$_.Description -join ','}}, @{Name='Data Source'; Expression={$_.'Data Source' -join ','}}, 
@{Name='Bypass'; Expression={$_.Bypass -join ','}}, @{Name='Analytic Details'; Expression={$_.'Analytic Details'
-join ','}}, @{Name='Mitigation'; Expression={$_.Mitigation -join ','}}, @{Name='Platform'; 
Expression={$_.Platform -join ','}}, @{Name='Requires Permission'; Expression={$_.'Requires Permission' -join
','}}, @{Name='Requires System'; Expression={$_.'Requires System' -join ','}}, @{Name='CAPEC ID'; 
Expression={$_.'CAPEC ID' -join ','}}, @{Name='Contributor'; Expression={$_.Contributor -join ','}}, 
@{Name='URL'; Expression={$_.URL -join ','}} | Export-Csv -NoTypeInformation C:\\Downloads\ATTACK_ALL.csv
```

# Author
* Roberto Rodriguez [@Cyb3rWard0g](https://twitter.com/Cyb3rWard0g)
# Contributors
# Contributing
Feel free to submit a PR and make this script a better one for the community.
# TO-DO
