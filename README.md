# PowerShell - Extension .ps1
Resource for learning Microsoft PowerShell scripting
<br><br>


# Contents

[Create a File](#create-a-file) <br>
[Execute a Script](#execute-script) <br>
[Add a Comment](#comments) <br>
[Functions](#functions) <br>
[Basic I/O](#io-basic) <br>
[Check if Path/File Exists](#if-exists) <br>
[Comparisons](#compare) <br>
[Get Current Directory](#get-location) <br>
[Manipulate Path/Files](#paths-files) <br>
[Type Casting](#casting) <br>
[Batch to PowerShell Notes](#bat) <br>

---

<a id="create-a-file"></a>

## Create a File
  ```
  New-Item -Path "path" -Name "name" -ItemType "type" -value "value"
  ```
  - omit path for current directory or use `.`
  - works without string quotations for input that does not contain spaces.

  **Hello World**:

    ```
    New-Item hello.txt -value "Hello World"
    ```

<a id="execute-script"></a>

## Allow Script Execution and Execute Script
  1. Open PowerShell in Administration mode (right click -> Run as administrator)
  2. Enter `set-executionpolicy remotesigned`  . This will allow scripts to be run on in both non- and Adminisratior mode.
  3. Go to directory or use full path to enter: `./hello.ps1`

  - If you don't include `./` before the path name, you will encounter an error
  - If the path contains spaces, use `&"path with spaces/script.ps1" ` instead

  **Output**:
    ```
    Hello World
    ```


<a id="comments"></a>

## Add a Comment

`# this is a comment`


<a id="functions"></a>
## Functions

```PowerShell
function CreateDTSXWix {
  param( [string]$source, [string]$dest, [int]$SQL_VER )
}
```


<a id="io-basic"></a>

## Basic I/O

  **Contents**

  [create, write, overwrite .txt files](#txt-files) <br>
  [common special characters](#spec-chars) <br>


  <a id="txt-files"></a>
  ### Example: .txt Files

  - **Create** .txt file:    `New-Item ./test.txt -value "Foo"`

    test.txt:
      ```
      Foo
      ```

  - **Overwrite** file using -force:   `` New-Item ./test.txt -value "Foo Bar" -force ``

    test.txt:
      ```
      Foo Bar
      ```

  - **Append** to file: ``Add-Content test.txt -value "`nNext Line" ``
    - will not automatically add any whitespace to front of value

    test.txt:
      ```
      Foo Bar
      Next Line
      ```



  <a id="spec-chars"></a>

  ### Common Special Characters

  | Text Symbol   | Character |
  | ------------- | ------------- |     
  | `0            | Null                    |
  | `a            | Alert                   |
  | `b            | Backspace               |
  | `e            | Escape                  |
  | `f            | Form feed               |
  | `n            | New line                |
  | `r            | Carriage return         |
  | `t            | Horizontal tab          |
  | `u{x}         | Unicode escape sequence |
  | `v            | Vertical tab            |
  | --%           | Stop parsing            |



<a id="if-exists"></a>

## Check If Path/File Exists

  - Test-Path works for both files and directories: `Test-Path -Path <path> `

  ```PowerShell
  New-Item test.ps1
  Test-Path test.ps1
  Test-Path test2.ps1
  ```

  **Output**
  ```
  True
  False
  ```

<a id="compare"></a>

## Comparisons


  **Comparison Operator Chart**

  | Type | Operator | Descritpion |
  | ---  | ---      | --- |
  | Equality | -eq | equals |
  | | -ne | not equals |
  | | -gt | greater than |
  | | -ge | greater than or equal |
  | | -lt | less than |
  | | -le | less than or equal |


  - Compare Booleans

    ```PowerShell
    New-Item test.txt
    if($(Test-Path test.txt) -eq $True) {echo 10}
    ```

    **Output**: `10`

    - booleans are not case-sensitive. $true, $True, $false, $False, $tRUE, etc.




<a id="get-location"></a>

## Get Current Directory

  `Get-Location`

  Output:

  ```

  Path
  ----
  C:\Users\User1\Desktop


  ```

<a id="paths-files"></a>

## Manipulate Paths/Files
- Get path's parent:

 `Split-Path -parent "C:\Users\User1\Desktop" `   Output: ` C:\Users\User1 `

 `Split-Path -parent $(get-location) `   Output: ` C:\Users\User1 `

- **Get files from a directory** and write to console
  ```PowerShell
  Get-ChildItem -path $source -Filter *.dtsx |
  Foreach-Object {
	Write-Host $_   #or $PSItem
  }
  ```

- **Replace spaces in filename** with underscore
  ```PowerShell
  $file_name.Replace(' ', '_')
  ```

- Get **path name, basename, extension**:
  ```PowerShell
  $path = (New-Item -path ./foo.txt)
  $path.name        #foo.txt
  $path.basename    # foo
  $path.extension   # .txt
  ```


<a id="casting"></a>

## Type Casting

- **int to string**:

  ```PowerShell
  $myint = 10
  $mystring = "Num: " + ([string]$myint)
  Write-Host $mystring
  ```

  Output: ` Num: 10 `



<a id="bat"></a>
## Batch to PowerShell Notes
  | Batch | PowerShell |
  | --- | --- |
  | .bat | .ps1 |
  | %variable$ | $variable |
  | @echo on/off | no echo |
  | %p | $_ or $PSItem |
  | %SystemRoot% | $Env:SystemRoot |
  | @ to prevent echo | @ for arrays / hash tables |
  | Output direction >, >> | supported |
  | Input direction <, << | not supported - use piping instead |
  | ^n | `n (tick) |


  - %SystemRoot% = C:\Windows.PowerShell
