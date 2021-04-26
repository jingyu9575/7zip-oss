# 7zo

This repository adds a build variant `7zo.exe` of the [7-Zip](https://www.7-zip.org/) command-line tool. It contains all the archive formats except RAR, which requires [source-available proprietary code](https://7-zip.org/license.txt).

## Build

To obtain executables linking dynamically to `msvcrt.dll`, the compilers from [Windows Driver Kit Version 7.1.0](https://www.microsoft.com/en-us/download/details.aspx?id=11800) can be used, with additional API headers `MAPI.h`, `Psapi.h` from Windows SDK v7.1A.

Change to the directory `CPP/7zip/Bundles/AloneOSS`. For x64 build:

```batch
set "WDK=<Path to WDK>"
set "PATH=%WDK%\bin\x86\amd64;%WDK%\bin\x86;%PATH%"
set "INCLUDE=%WDK%\inc\api;%WDK%\inc\api\crt\stl70;%WDK%\inc\crt;%INCLUDE%"
set "LIB=%WDK%\lib\wnet\amd64;%WDK%\lib\Crt\amd64;%LIB%"
nmake PLATFORM=x64 MY_DYNAMIC_LINK=1
```

For x86 build:

```batch
set "WDK=<Path to WDK>"
set "PATH=%WDK%\bin\x86\x86;%WDK%\bin\x86;%PATH%"
set "INCLUDE=%WDK%\inc\api;%WDK%\inc\api\crt\stl70;%WDK%\inc\crt;%INCLUDE%"
set "LIB=%WDK%\lib\wxp\i386;%WDK%\lib\Crt\i386;%LIB%"
nmake PLATFORM=x86 MY_DYNAMIC_LINK=1
```
