# Poetry

- [Poetry](#poetry)
  - [前言](#前言)
  - [安裝](#安裝)
  - [解除安裝](#解除安裝)
  - [使用](#使用)
    - [1. 建立專案](#1-建立專案)
    - [2. 新增依賴](#2-新增依賴)
    - [3. 安裝依賴](#3-安裝依賴)
    - [4. 執行腳本](#4-執行腳本)
    - [5. 管理環境](#5-管理環境)
    - [6. 移除依賴](#6-移除依賴)
    - [7. 更新依賴](#7-更新依賴)
  - [參考資料](#參考資料)

## 前言

- Poetry 是 Python 中用於「依賴管理」和「打包」的工具
- 它允許您聲明您的專案所依賴的庫，並為您管理(安裝/更新)它們
- 它提供了一個「lock file」，以確保可重複的安裝，並可以為您的專案構建發行版

## 安裝

Linux, macOS, WSL(Windows) : 

`curl -sSL https://install.python-poetry.org | python3 -`

PowerShell(Windows) : 

`(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | py -`

> 如果您是透過 Microsoft Store 安裝 Python，請將上述指令中的 `py` 替換為 `python`。

## 解除安裝

如果您決定不再使用 Poetry，您可以透過再次執行安裝程式並加上 `--uninstall` 選項，或是在執行安裝程式前設定 `POETRY_UNINSTALL` 環境變數，來完全移除系統中的 Poetry。

```bash
curl -sSL https://install.python-poetry.org | python3 - --uninstall
curl -sSL https://install.python-poetry.org | POETRY_UNINSTALL=1 python3 -
```

## 使用

以下用一個簡單的範例來說明 Poetry 的使用：

### 1. 建立專案

```bash
poetry new my-project
```

這會在當前目錄下建立一個名為 `my-project` 的專案，並在專案目錄下建立一個基本的專案結構。

```
my-project
├── README.rst
├── my_project
│   └── __init__.py
├── pyproject.toml
└── tests
    └── __init__.py
```

### 2. 新增依賴

透過 `cd my-project` 進入專案目錄，並透過 `poetry add <package>` 來新增依賴。

```bash
cd my-project
poetry add requests
```

以 requests 模組為例，這會在 `pyproject.toml` 中新增 `requests` 的依賴，並在 `poetry.lock` 中更新依賴的版本。

### 3. 安裝依賴

執行 `poetry install` 來安裝所有依賴。

```bash
poetry install
```

### 4. 執行腳本

透過執行 `poetry run <script>`，可以在虛擬環境中執行腳本。

```bash
poetry run python my_project/main.py
```

另外，您也可以透過 `poetry shell` 進入虛擬環境，來執行腳本。

```bash
poetry shell # 進入虛擬環境
python my_project/main.py
exit # 退出虛擬環境
```

### 5. 管理環境

透過 `poetry env info` 來查看虛擬環境的資訊。

```bash
poetry env info
```

### 6. 移除依賴

透過 `poetry remove <package>` 來移除依賴。

```bash
poetry remove requests
```

### 7. 更新依賴

透過 `poetry update` 來更新所有依賴，或透過 `poetry update <package>` 來更新特定依賴。

```bash
poetry update
poetry update requests
```

## 參考資料

- [Poetry 官方文件](https://python-poetry.org/docs/)
