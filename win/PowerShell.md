# diff
```
  Clear-Host
  $f1 = Get-Content "path\to\file1"
  $f2 = Get-Content "path\to\file2"
  Compare-Object $f1 $f2
```
# [grep](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-string?view=powershell-7)
```
Select-String -Path "path\to\*" -Pattern 'needle'
Select-String -Path "$PSHOME\en-US\*.txt" -Pattern '\?'

-CaseSensitive
-SimpleMatch: specifies that the string in the pattern isn't interpreted as a regular expression
```
# module
```
Find-Module -Name PowerShellGet | Install-Module

if (Get-Module -ListAvailable -Name SomeModule) {
    Write-Host "Module exists"
} else {
    Write-Host "Module does not exist"
}

Import-Module

Remove-Module
```

# object
```
Get-ADObject

Select-Object

Sort-Object

Get-ADObject -Filter * | MeasureObject

Get-ADObject - Filter * | Select-Object -ExpandProperty ObjectGUID -Last 5

(Get-ADUser -Identity Administrator -Properties *).PropertyCount

# By default AD has a limit of 1000 objects that it will return
Get-Help Get-ADObject

# Limit the result to 5
Get-ADObject - Filter *  -ResultSetSize 5

# count lines
Get-Content path\to\file | Measure-Object -Line
```

# variable
## use dot source
```
var.ps1
$var1 = "1"
$var2 = "2"

main.ps
..\vars.ps1
echo $var1
echo $var2
```

## use Global
```
var.ps1
$Global:var1 = "1"
$Global:var2 = "2"

main.ps
.\vars.ps1
echo $var1
echo $var2
```
https://stackoverflow.com/questions/1864128/load-variables-from-another-powershell-script

# version
```
$PSVersionTable.PSVersion

# Check whether the .NET Framework 4.6.2 or later is installed
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```
# sort and uniq
https://powershell.org/forums/topic/powershell-equivalent-to-sortuniq-csort-nr/
```
@(55,22,33,44,11,44,33,22,11,33,22,11,22,11,11) | Group-Object | Select-Object -Property Count, Name | Sort-Object -Property Count -Descending
@(55,22,33,44,11,44,33,22,11,33,22,11,22,11,11) | group | select Count, Name | sort Count -d

Get-Content "path\to\file" | group | select Count, Name | sort Count -d

Get-Content "path\to\file" | sort | Get-Unique > path\to\unique_lines.txt
```

* https://adamtheautomator.com/get-adobject/
* https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-6
* https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-6
* https://powershell.org/forums/topic/count-users-attributes-in-ad/
