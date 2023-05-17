## WinRepoUpdater

WinRepoUpdater is a PowerShell script designed to update multiple Git repositories located in a directory or its subdirectories. It automates the process of pulling the latest changes from the remote repository for each repository found.
## Features

- Updates multiple Git repositories in a specified directory or its subdirectories.
- Pulls the latest changes from the remote repository.
- Provides color-coded output for success and error messages.
- Displays a list of successfully updated repositories.

## Prerequisites

- PowerShell: The script is designed to run in a PowerShell environment.
- Git: Ensure that Git is installed and accessible through the command line.


## Usage/Examples

Clone the project

```powershell
  git clone https://github.com/YoruYagami/WinRepoUpdater.git
```

Go to the project directory

```powershell
  cd WinRepoUpdater
```

Import Module

```powershell
  . .\WinRepoUpdater.ps1
```

Call the function

```powershell
  Invoke-WinRepoUpdater
```

Update all the repos in a specific folder

```powershell
  Invoke-WinRepoUpdater C:\Users\pentester\C2-Frameworks\
```