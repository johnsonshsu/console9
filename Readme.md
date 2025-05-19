# .NET 9 主控台專案範本
## 1. 設計目的
本專案範本是使用 **.NET 9** 的 **Console** 範本建立，再加入以下的修改而成

1. 加入 **.vscode** 資料夾
2. 加入 **.vscode\launch.json** 設定檔
3. 加入 **.vscode\tasks.json** 設定
4. 修改 **Program.cs** 程式，調整成傳統的 **Main()** 

主要是用於快速建立一個 **.NET 9** 的主控台程式。

## 2. launch.json 設定檔內容
```json=
{
  // 使用 IntelliSense 以得知可用的屬性。
  // 暫留以檢視現有屬性的描述。
  // 如需詳細資訊，請瀏覽: https://go.microsoft.com/fwlink/?linkid=830387
  "version": "0.2.0",
  "configurations": [
    {
      "name": ".NET Core Launch (console)",
      "type": "coreclr",
      "request": "launch",
      "preLaunchTask": "build",
      "program": "${workspaceFolder}\\bin\\Debug\\net9.0\\console9.dll",
      "args": [],
      "cwd": "${workspaceFolder}",
      "stopAtEntry": false,
      "console": "externalTerminal"
    }
  ]
}
```

## 3. tasks.json 設定檔內容
```json=
{
  // See https://go.microsoft.com/fwlink/?LinkId=733558
  // for the documentation about the tasks.json format
  "version": "2.0.0",
  "tasks": [
    {
      "label": "build",
      "command": "dotnet",
      "type": "shell",
      "args": [
        "build",
        // 要求 dotnet build 產生檔案名稱的完整路徑.
        "/property:GenerateFullPaths=true",
        // 不要產生摘要，否則會導致問題面板中出現重複錯誤
        "/consoleloggerparameters:NoSummary"
      ],
      "group": "build",
      "presentation": {
        "reveal": "silent"
      },
      "problemMatcher": "$msCompile"
    }
  ]
}
```