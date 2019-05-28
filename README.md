# PowerShell - Extension .ps1
Resource for learning Microsoft PowerShell scripting
<br><br>


# Contents

[Create a File](#create-a-file) <br>
[Execute a Script](#execute-script) <br>

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
  
  ** If you don't include `./` before the path name, you will encounter an error
  
  ** If the path contains spaces, use `&"path with spaces/script.ps1" ` instead

  **Output**:
    ```
    Hello World
    ```
