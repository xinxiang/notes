https://stackoverflow.com/questions/13015245/powershell-script-wont-execute-as-a-windows-scheduled-task
```
powershell.exe -NoProfile -NoLogo -NonInteractive -ExecutionPolicy Bypass -File \\path\to\script.ps1
```
# Fail to run
Check the Last run result column

(0xFFFD0000)
The field “Add arguments (optional)” contains an invalid file name. For example: you refer to myscript.ps2 instead of myscript.ps1

The system cannot find the file specified (800070002)
The field “Program/script” contains an invalid directory

The task is currently running. (041301) hangs
The field “Program/script” contains an invalid executable name extension. For example: powershell.sexe instead of powershell.exe would lead the task to be hanging. In the end, the task will time out after 72 hours.

(0x1)
The field “Add arguments (optional)” contains an invalid argument. For example: -Gile instead of -File could lead to this error.

Ref: https://www.itexperience.net/0xfffd0000-in-task-scheduler-when-running-powershell-script/
