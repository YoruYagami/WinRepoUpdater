# Define colors for text output
$colors = @{
    Success = "Green"
    Error = "Red"
}

# Function to update git repositories
function Invoke-WinRepoUpdater {
    param (
        [string]$path = (Get-Location).Path
    )

    Write-Host "Updating repositories in directory: $path"
    Write-Host "---------------------------------------------"

    # Get a list of all directories in the specified path
    $directories = Get-ChildItem -Path $path -Directory -Recurse

    # Array to store successfully updated repositories
    $updatedRepos = @()

    foreach ($directory in $directories) {
        # Check if the directory is a git repository by checking for .git subdirectory
        $gitDir = Join-Path -Path $directory.FullName -ChildPath ".git"
        if (Test-Path $gitDir) {
            Write-Host "Updating repository: $($directory.Name)"
            Write-Host "--------------------------"

            # Navigate into the repository directory
            Set-Location -Path $directory.FullName

            # Attempt to pull the latest changes from the remote repository
            $pullResult = git pull

            if ($LASTEXITCODE -eq 0) {
                # Pull succeeded
                Write-Host "Repository is up to date" -ForegroundColor $colors.Success
                $updatedRepos += $directory.Name
            } else {
                # Pull failed
                Write-Host "Error updating repository: $($directory.Name)" -ForegroundColor $colors.Error
            }

            Write-Host
        }
    }

    Write-Host "---------------------------------------------"
    Write-Host "All repositories have been updated"

    # Output the list of successfully updated repositories
    if ($updatedRepos.Count -gt 0) {
        Write-Host "Updated repositories:"
        $updatedRepos | ForEach-Object { Write-Host "- $_" }
    }
}
