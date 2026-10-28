#### Original Sourceslist
- https://www.youtube.com/watch?v=YvrUd8I_RPY
- https://github.com/Rustring/MsOffice-On-WineBottles-Improved
- https://github.com/tazihad/msoffice-bottle

#### Office 2007


#### Office 2010


```
reg add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SoftwareProtectionPlatform" /v KeyManagementServiceName /t REG_SZ /d "<yourdomains>" /f
reg add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SoftwareProtectionPlatform" /v KeyManagementServicePort /t REG_SZ /d "1688" /f
```
