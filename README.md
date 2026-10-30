#### Original Sourceslist
- https://www.youtube.com/watch?v=YvrUd8I_RPY
- https://github.com/Rustring/MsOffice-On-WineBottles-Improved
- https://github.com/tazihad/msoffice-bottle


#### Bottles Setup

- Install Bottles
```
flatpak install flathub com.usebottles.bottles
```

- Grant necessary directory permission
```
flatpak override com.usebottles.bottles --user --filesystem=xdg-data/applications
flatpak override com.usebottles.bottles --user --filesystem=home
```

- Download runner

```
mkdir -p ~/.var/app/com.usebottles.bottles/data/bottles/runners/winecx-crossover-24.0.7
curl -L https://github.com/arfshl/officeonbottles-ex/releases/download/runners/winecx-crossover-24.0.7.tar.xz --output /tmp/winecx.tar.xz
tar -xJf /tmp/winecx.tar.xz -C ~/.var/app/com.usebottles.bottles/data/bottles/runners/winecx-crossover-24.0.7
rm /tmp/winecx.tar.xz
```

#### Office 2007
- Import configuration from [here](https://github.com/arfshl/officeonbottles-ex/blob/main/office2007-winecx-crossover-24.0.7.yml)

- Or create manual bottles

```
Environment: Custom
Runner: winecx-crossover-24.0.7
Architecture: 32-bit
Windows Version: Windows 7
Depedencies: gdiplus msxml4 mspatcha riched20 mono gecko allfonts dotnet40
DLL Override: gdiplus riched20 Native, than Builtin
```

- Mount the iso and install

#### Office 2010

- Import configuration from [here](https://github.com/arfshl/officeonbottles-ex/blob/main/office2010-winecx-crossover-24.0.7.yml)

- Or create manual bottles

```
Environment: Custom
Runner: winecx-crossover-24.0.7
Architecture: 32-bit
Windows Version: Windows 7
Depedencies: gdiplus msxml4 mspatcha riched20 mono gecko allfonts dotnet40
DLL Override: gdiplus riched20 Native, than Builtin
```
- Mount the iso and install

- Since ospp.vbs didn't work under wine, we put kms activation server directly on registry:
```
reg add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SoftwareProtectionPlatform" /v KeyManagementServiceName /t REG_SZ /d "<yourdomains>" /f
reg add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SoftwareProtectionPlatform" /v KeyManagementServicePort /t REG_SZ /d "1688" /f
```

#### File Integrations
- [Office 2010](https://github.com/tazihad/msoffice-bottle#file-integrations)

#### Working Copies
```
en_office_enterprise_2007_united_states_x86_cd_481472.iso
SHA256: f0f40578b72d12c31a35370f0e792175123b086a0832c2c4534ddbe37d75ad04
https://archive.org/download/officemsivl/en_office_enterprise_2007_united_states_x86_cd_481472.iso

SW_DVD5_Office_Professional_Plus_2010w_SP1_W32_English_CORE_MLF_X17-76748.ISO
SHA256: 38457021494137d8115ae853bcdff78f830a339cfa8ee78b3fa92fc1cb69b03b
https://archive.org/download/officemsivl/SW_DVD5_Office_Professional_Plus_2010w_SP1_W32_English_CORE_MLF_X17-76748.ISO
```