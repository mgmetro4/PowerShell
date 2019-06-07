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
  "Gets the content of the item at the specified location."

  ```PowerShell
  $xml = [xml] (Get-Content -Path $source)
  ```

  ```PowerShell
  > Get-Content -Path .\file.txt -TotalCount 2      #use -TotalCount 2[-1] to get the 2nd line only

  Line 1
  Line 2
  ```

---

<a id="getchilditem"></a>
## Get-ChildItem  
  "Gets the items and child items in one or more specified locations."

  ```PowerShell
  > $a = Get-ChildItem .


  Directory: <dir>


  Mode                LastWriteTime         Length Name
  ----                -------------         ------ ----
  d-----         6/6/2019   1:16 PM                Folder1
  d-----        5/31/2019  10:19 AM                Folder2
  -a----        5/21/2019   4:13 PM            179 Cafe Hours.txt
  -a----        5/24/2019  11:13 AM       17517508 Project 1.zip

  > $a.GetType()     # System.Array
  ```
  ```PowerShell
  > $a = Get-ChildItem -Path . -Name
  > $a

  Folder1
  Folder2
  Cafe Hours.txt
  Project 1.zip


  > $a.GetType()    # System.Array
  ```

  ```PowerShell
  > $a = Get-ChildItem -Path . -Filter *.txt
  > $a.GetType()      # System.IO.FileSystemInfo
  ```

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
  "Selects objects from a collection of objects that are passed to it based on their property values."

  ```PowerShell
  Get-Process | Where-Object {$_.PriorityClass -eq "Normal"}
  ```

  ```PowerShell
  Get-Process | Where-Object -Property PriorityClass -eq -Value "Normal"
  ```

  Omit optional parameters:
  ```PowerShell
  Get-Service | where Status -eq "Stopped"
  ```

---

<a id="selectstring"></a>
## Select-String
  "Finds text in input strings and files."

  ```PowerShell
  'Hello', 'HELLO' | Select-String -Pattern 'HELLO' -CaseSensitive -SimpleMatch     # SimpleMatch = do not process pattern as a regular expression
  ```

  ```PowerShell
  $old_cmp_source = $components.file.source | Select-String -Pattern ("\\" + $cmp_name + ".txt") | Select-Object -First 1
  ```

  ```PowerShell
  > $a = "\alert2.txt", "\alert.txt" | Select-String -Pattern ".txt"  

  \alert2.txt
  \alert.txt
  ```
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
