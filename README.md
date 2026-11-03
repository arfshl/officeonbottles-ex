# Run Microsoft Office in Bottles flatpak
### Bottles Setup

- Install Bottles
```
flatpak install flathub com.usebottles.bottles
```

- Grant necessary directory permission
```
flatpak override com.usebottles.bottles --user --filesystem=xdg-data/applications
flatpak override com.usebottles.bottles --user --filesystem=home
```

### Office 2007
- Download runner (skip if already exists)

Using winecx 24.0.7 32-bit

```
mkdir -p ~/.var/app/com.usebottles.bottles/data/bottles/runners/winecx-crossover-24.0.7
curl -L https://github.com/arfshl/winecx-bottles/releases/download/winecx-24.0.7-jammy/winecx-crossover-24.0.7-jammy-32bitonly.tar.xz --output /tmp/winecx.tar.xz
tar -xJf /tmp/winecx.tar.xz -C ~/.var/app/com.usebottles.bottles/data/bottles/runners/winecx-crossover-24.0.7-jammy-32bitonly
rm /tmp/winecx.tar.xz
```

- Import configuration from [here](https://github.com/arfshl/officeonbottles-ex/blob/main/backup_office2007-winecx.yml)

- Or create manual bottles with:

```
Name: office2007-winecx
Environment: Custom
Runner: winecx-crossover-24.0.7-jammy-32bitonly
Architecture: 32-bit
Windows Version: Windows 7
Depedencies: gdiplus msxml4 mspatcha riched20 gecko allfonts dotnet40
DLL Override: gdiplus riched20 xmllite Native, than Builtin
```

- Mount the iso and run setup.exe for installing office

### Office 2010

- Download runner (skip if already exists)

Using winecx 26.3.0 32-bit

```
mkdir -p ~/.var/app/com.usebottles.bottles/data/bottles/runners/winecx-crossover-26.3.0
curl -L https://github.com/arfshl/winecx-bottles/releases/download/winecx-26.3.0-jammy/winecx-crossover-26.3.0-jammy-32bitonly.tar.xz --output /tmp/winecx.tar.xz
tar -xJf /tmp/winecx.tar.xz -C ~/.var/app/com.usebottles.bottles/data/bottles/runners/winecx-crossover-26.3.0-jammy-32bitonly
rm /tmp/winecx.tar.xz
```

- Import configuration from [here](https://github.com/arfshl/officeonbottles-ex/blob/main/backup_office2010-winecx.yml)

- Or create manual bottles with:

```
Name: office2010-winecx
Environment: Custom
Runner: winecx-crossover-26.3.0-jammy-32bitonly
Architecture: 32-bit
Windows Version: Windows 7
Depedencies: gdiplus msxml4 mspatcha riched20 gecko allfonts dotnet40
DLL Override: gdiplus riched20 xmllite Native, than Builtin
```

- Mount the iso and run setup.exe for installing office

- Since ospp.vbs didn't work under wine, we put kms activation server directly on registry (bottles > tools, commandline > run this command):
```
reg add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SoftwareProtectionPlatform" /v KeyManagementServiceName /t REG_SZ /d "<yourdomains>" /f
reg add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SoftwareProtectionPlatform" /v KeyManagementServicePort /t REG_SZ /d "1688" /f
```

### Office 2013

- Download runner (skip if already exists)

Using winecx 26.3.0 32-bit

```
mkdir -p ~/.var/app/com.usebottles.bottles/data/bottles/runners/winecx-crossover-26.3.0
curl -L https://github.com/arfshl/winecx-bottles/releases/download/winecx-26.3.0-jammy/winecx-crossover-26.3.0-jammy-32bitonly.tar.xz --output /tmp/winecx.tar.xz
tar -xJf /tmp/winecx.tar.xz -C ~/.var/app/com.usebottles.bottles/data/bottles/runners/winecx-crossover-26.3.0-jammy-32bitonly
rm /tmp/winecx.tar.xz
```

- Import configuration from [here](https://github.com/arfshl/officeonbottles-ex/blob/main/backup_office2013-winecx.yml)

- Or create manual bottles with:

```
Name: office2013-winecx
Environment: Custom
Runner: winecx-crossover-26.3.0-jammy-32bitonly
Architecture: 32-bit
Windows Version: Windows 7
Depedencies: gdiplus msxml4 mspatcha riched20 gecko allfonts dotnet40
DLL Override: riched20 xmllite Native, than Builtin
```

- Mount the iso and run setup.exe for installing office

- Before launch, set d2d version and disable office hardware acceleration with this registry key (bottles > tools, commandline > run this command):

```
reg add "HKEY_CURRENT_USER\Software\Wine\Direct2D" /v max_version_factory /t REG_DWORD /d 0 /f
reg add "HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Graphics" /v DisableHardwareAcceleration /t REG_DWORD /d 1 /f
```

- Since ospp.vbs didn't work under wine, we put kms activation server directly on registry (bottles > tools, commandline > run this command):
```
reg add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SoftwareProtectionPlatform" /v KeyManagementServiceName /t REG_SZ /d "<yourdomains>" /f
reg add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SoftwareProtectionPlatform" /v KeyManagementServicePort /t REG_SZ /d "1688" /f
```

### Office 2016

- Download runner (skip if already exists)

Using winecx 26.3.0 32-bit

```
mkdir -p ~/.var/app/com.usebottles.bottles/data/bottles/runners/winecx-crossover-26.3.0
curl -L https://github.com/arfshl/winecx-bottles/releases/download/winecx-26.3.0-jammy/winecx-crossover-26.3.0-jammy-32bitonly.tar.xz --output /tmp/winecx.tar.xz
tar -xJf /tmp/winecx.tar.xz -C ~/.var/app/com.usebottles.bottles/data/bottles/runners/winecx-crossover-26.3.0-jammy-32bitonly
rm /tmp/winecx.tar.xz
```

- Import configuration from [here](https://github.com/arfshl/officeonbottles-ex/blob/main/backup_office2016-winecx.yml)

- Or create manual bottles with:

```
Name: office2016-winecx
Environment: Custom
Runner: winecx-crossover-26.3.0-jammy-32bitonly
Architecture: 32-bit
Windows Version: Windows 7
Depedencies: gdiplus msxml4 mspatcha riched20 gecko allfonts dotnet40
DLL Override: riched20 xmllite Native, than Builtin
```

- Mount the iso and run setup.exe for installing office

- Before launch, set d2d version and disable office hardware acceleration with this registry key (bottles > tools, commandline > run this command):

```
reg add "HKEY_CURRENT_USER\Software\Wine\Direct2D" /v max_version_factory /t REG_DWORD /d 0 /f
reg add "HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Common\Graphics" /v DisableHardwareAcceleration /t REG_DWORD /d 1 /f
```

- Since ospp.vbs didn't work under wine, we put kms activation server directly on registry (bottles > tools, commandline > run this command):
```
reg add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SoftwareProtectionPlatform" /v KeyManagementServiceName /t REG_SZ /d "<yourdomains>" /f
reg add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SoftwareProtectionPlatform" /v KeyManagementServicePort /t REG_SZ /d "1688" /f
```

### Screenshot
https://github.com/arfshl/officeonbottles-ex/tree/main/screenshots

### File Integrations
- [Office 2007](https://github.com/arfshl/officeonbottles-ex/tree/main/file-integrations/office2007)
- [Office 2010](https://github.com/arfshl/officeonbottles-ex/tree/main/file-integrations/office2010)
- [Office 2013](https://github.com/arfshl/officeonbottles-ex/tree/main/file-integrations/office2013)
- [Office 2016](https://github.com/arfshl/officeonbottles-ex/tree/main/file-integrations/office2016)

Replace `$USER` with your real username, and put this on `/home/$USER/.local/share/applications`

Recommended: Symlink your Documents folder to Wine C: drive folder

```
ln -s /home/$USER/Documents /home/$USER/.var/app/com.usebottles.bottles/data/bottles/bottles/office2016-winecx/drive_c/users/crossover/Documents/Documents
```
Replace `$USER` with your real username, and `office2016` with your office version

### Working Copies
https://archive.org/details/officemsivl

### Original Sourceslist
- https://www.youtube.com/watch?v=YvrUd8I_RPY
- https://github.com/Rustring/MsOffice-On-WineBottles-Improved
- https://github.com/tazihad/msoffice-bottle