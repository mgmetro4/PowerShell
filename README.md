# PowerShell - Extension .ps1
Resource for learning Microsoft PowerShell scripting
<br><br>


# Contents

[Create a File](#create-a-file) <br>
[Execute a Script](#execute-script) <br>
[Add a Comment](#comments) <br>
[Basic I/O](#io-basic) <br>
[Check if Path/File Exists](#if-exists) <br>
[Comparisons](#compare) <br>

<br><br><br>

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

