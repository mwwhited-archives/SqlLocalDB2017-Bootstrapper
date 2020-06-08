# SqlLocalDB2017-Bootstrapper

ClickOnce and Visual Studio Installer bootstrapper package for Microsoft SQL Server 2017/2019 Express LocalDB.

## SQL LocalDB 2017/2019

In "visual studio / project properties / publish / Prerequisites" SQL Server 2017/2019 Express LocalDB can not be selected. 
Copy the SqlLocalDB2017 and SqlLocalDB2019 folder into the proper place e.g.: 
*%ProgramFiles(x86)%\Microsoft SDKs\ClickOnce Bootstrapper\Packages* and restart Visual Studio.

## DAC Framework

https://go.microsoft.com/fwlink/?linkid=2128142

## Extract info from existing MSI



c:\Users\matt.whited\Downloads\dacframework.msi
cscript /nologo WiRunSQL.vbs c:\Users\matt.whited\Downloads\dacframework.msi "SELECT Property,Value FROM Property" 
WHERE Property = 'ProductCode'"

UpgradeCode  {D3FE1F7A-09B9-40D1-9A33-3AA33C31DC05}
ARPNOMODIFY  1
ALLUSERS  1
WIXUI_INSTALLDIR  bin
Manufacturer  Microsoft Corporation
ProductCode  {696B61AD-8754-4629-95DC-F4CF5249385F}
ProductLanguage  1033
ProductName  Microsoft SQL Server Data-Tier Application Framework (x64)
ProductVersion  15.0.4769.1
DefaultUIFont  WixUI_Font_Normal
ErrorDialog  ErrorDlg
SecureCustomProperties  WIX_DOWNGRADE_DETECTED;WIX_UPGRADE_DETECTED
WixPdbPath  F:\B\16846\6200\Binaries\x64\Release\DACFramework.wixpdb

## Other stuff

SET TempSqlDeployPath=%temp%\nucleus\sqldeploy
SET SqlDatabase=NucleusDB
SET SqlServer=(localdb)\NucleusDB

SET TempSqlConnection=server=%SqlServe%;database=%SqlDatabase%;trusted_connection=true;

SET SqlPackageCmd=sqlpackage.exe
SET SqlCmdCmd=sqlcmd.exe

SET SqlTarget=%TempSqlDeployPath%\current.database.dacpac
SET SqlSource=Lightwell.Nucleus.Persistence.NucleusDb.dacpac
SET SqlChangeScript=%TempSqlDeployPath%\update.database.sql

REM IF NOT EXIST "%TempSqlDeployPath%" (MKDIR "%TempSqlDeployPath%")
REM "%SqlPackageCmd%" /a:script /op:"%SqlChangeScript%" /of:True /sf:"%SqlSource%" /tcs:"%TempSqlConnection%"
REM "%SqlCmdCmd%" -S "%SqlServer%" -d "%SqlDatabase%" -E -i "%SqlChangeScript%"

"%SqlPackageCmd%" /a:publish /op:"%SqlChangeScript%" /of:True /sf:"%SqlSource%" /tcs:"%TempSqlConnection%"


https://superuser.com/questions/747094/easiest-way-to-grant-log-on-as-a-service-to-a-windows-user-from-the-command-li
https://morgantechspace.com/2013/11/Set-or-Grant-Logon-As-A-Service-right-to-User.html
ntrights +r SeServiceLogonRight -u jeroen -m \\%COMPUTERNAME%

https://dotnet.microsoft.com/download/dotnet-core/thank-you/runtime-desktop-3.1.3-windows-x64-installer


https://download.visualstudio.microsoft.com/download/pr/5954c748-86a1-4823-9e7d-d35f6039317a/169e82cbf6fdeb678c5558c5d0a83834/windowsdesktop-runtime-3.1.3-win-x64.exe


http://go.microsoft.com/fwlink/?LinkId=863262&clcid=0x409

C:\Program Files\dotnet\packs\Microsoft.WindowsDesktop.App.Ref\3.1.0