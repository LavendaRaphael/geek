
## New-Ttem

<https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/new-item>

```powershell
New-Item -ItemType SymbolicLink -Path .\link -Target .\Notice.txt
(Get-Item .\Notice.txt).Delete()
```

## 调用cmd

```powershell
cmd /Cl
```
