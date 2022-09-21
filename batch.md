# Windows batch �ο�

��Դ:
- http://steve-jansen.github.io/guides/windows-batch-scripting/part-10-advanced-tricks.html
- https://www.tutorialspoint.com/batch_script/batch_script_quick_guide.htm
- https://ss64.com/nt/

## ���������ӳ���

```
SET foo="bar"
if "%foo%"=="bar" (goto isbar) else (goto isnotbar)
echo.

:isbar
echo foo is bar
goto endbar

:isnotbar
echo foo is not bar

:endbar
```

```
:choicestart
SET /p choice="Enter 1: "
if NOT %choice%==1 (goto choicestart)
```

## ��������

- ��ǰĿ¼: `%CD%`
- ��ǰbatch�ļ�: `%~dp0`
- ��ǰbatch�ļ��Ĳ���: %1 - %9

## Zip/unzip

��ѹ (Win 10 1903 (Jan 2018) or later): `tar -xf "myfile.zip"`

��ѹ (can be run in cmd): `powershell Expand-Archive myfile.zip output/ -Force`

ѹ��(can be run in cmd): `powershell Compress-Archive -path mypath -destinationpath -mydestpath`

## �ļ�����

Win 10 1903 �Ժ�汾: `curl "https://.../file.zip" -o myfile.zip`

���� (can be run in a cmd): `powershell Invoke-WebRequest -Uri "http://host.com/file_example_JSON_1kb.json" -OutFile c:\test.json`

## Copy all files from one location to another (in this example, up one directory)

`robocopy .\currentFolder\ .\ /E /MOVE /NFL /NDL /NJH /NJS /NC /NS /NP`

## Restart the batch file (maybe something in the PATH changed)

`start "" "%~f0"`

## Check if something is in the PATH

```
for %%X in (wt.exe) do (set FOUNDWT=%%~$PATH:X)
if defined FOUNDWT (goto found) else (goto notfound)
```

## Open a website in default browser

`start https://www.google.com`

## Run a commandline command in this window

`start "" /wait /b ping www.google.com`

## Get file hash

`certutil -hashfile myfile.zip MD5`

MD4, MD5, SHA1, SHA256, and SHA512 are allowed

To get only the hash returned: `certutil -hashfile myfile.zip MD5 | findstr /V ":"` as the only line without a colon is the hash

## Rename all files to a different file type

`ren *.rar *.cbr`

## Take control of all files in directory (after reinstalling Windows for example)

```
takeown /f %1 /r /d y
icacls %1 /grant administrators:F /t
```

## Put every .mp3 file in the folder and all sub folders into a .m3u playlist

`for /R %%X in (*.mp3) do (echo %%X >> playlist.m3u)`

## Turn off echoing every command

`@echo off` 

The @ makes the current command also silent; `echo off` turns off all subsequent echoes, but not itself

## Write an empty line to a text file

`echo. >> out.txt`

Note the period after echo - `echo.`

## Write the contents of a text file to another text file

append to the end or create if it doesn't exist: `type "filename.txt" >> out.txt`

overwrite or create if it doesn't exist: `type "filename.txt" > out.txt`

## Write comments

`:: this is a comment`

Alternatively, `rem this is a comment`

## Wait/sleep for 9 seconds

`ping -n 9 127.0.0.1 > NUL`

## Wait for user to press any key before closing (useful when intended to be run by double-clicking)

`pause`

## Redirecting stdout and stderr

`[command] >NUL` - pipe stdout to null

`[command] 2>&1` - pipe stderr to stdout