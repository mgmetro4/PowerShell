# Examples of Common Microsoft PowerShell cmdlets

[Cmdlet Docs](https://docs.microsoft.com/en-us/powershell/developer/cmdlet/cmdlet-overview)

---

# Contents

[ForEach-Object](#foreach)

[Get-Content](#getcontent)

[Get-ChildItem](#getchilditem)

[New-Item](#newitem)

[Add-Content](#addcontent)

[Clear-Content](#clearcontent)

[Rename-Item](#renameitem)

[Where-Object](#whereobject)

[Select-String](#selectstring)

[Test-Path](#testpath)

[Write-Host](#writehost)

[]()


---

<a id="foreach"></a>
## ForEach-Object -  %{}
  - "Performs an operation against each item in a collection of input objects."
  ```PowerShell
  1, 2, 3 | ForEach-Object {$_}

  1
  2
  3
  ```

  - can also be represented as:

  ```PowerShell
  1,2,3 | %{$_}
  ```

---

<a id="getcontent"></a>
## Get-Content


---

<a id="getchilditem"></a>
## Get-ChildItem  


---

<a id="newitem"></a>
## New-Item


---

<a id="addcontent"></a>
## Add-Content  


---

<a id=clearcontent""></a>
## Clear-Content


---

<a id="renameitem"></a>
## Rename-Item

  ```PowerShell
  Rename-Item -Path ./t.txt -NewName t2.txt    # t2.txt

  Rename-Item t2.txt -NewName t3               # t3

  Rename-Item t3 t3.txt                        # t3.txt

  Rename-Item t3.txt ./t.txt                   # t.txt
  ```

---

<a id="whereobject"></a>
## Where-Object


---

<a id="selectstring"></a>
## Select-String


---

<a id="testpath"></a>
## Test-Path
  ```PowerShell
  Test-Path -Path $source   # True / False
  ```

---

<a id="writehost"></a>
## Write-Host

  ```PowerShell
  $text = "Hello World"
  Write-Host Hello    # Hello
  Write-Host "World"  # World
  Write-Host $text    # Hello World
  ```
