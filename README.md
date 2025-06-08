# powershell profile

I use windows terminal with oh-my-posh, both are installed via the microsoft store. Setup instructions:
install windows terminal
install oh-my-posh

Then open powershell and install modules and setup profile:

- install nerd font: `oh-my-posh font install`
- create/update powershell profile (`code $PROFILE` in powershell)
- script execution policy may prevent oh my posh from working after editing profile, to fix run `Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope CurrentUser` 
- then add Terminal-Icons `Install-Module -Name Terminal-Icons`
- then add posh-git `Install-Module -Name posh-git`
- then add PSReadLine `Install-Module PsReadLine -Force`
- PSReadLine may already be installed, but check the version and upgrade `Install-Module -Name PSReadLine -RequiredVersion 2.3.6`

full profile:
```
oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\jv_sitecorian.omp.json" | Invoke-Expression
Enable-PoshTooltips
Import-Module -Name Terminal-Icons
Import-Module -Name posh-git
Import-Module PSReadLine
$PSReadLineColorOptions = @{
    "Command" = [ConsoleColor]::Green
    "Parameter" = [ConsoleColor]::Gray
    "Operator" = [ConsoleColor]::Magenta
    "Variable" = [ConsoleColor]::White
    "String" = [ConsoleColor]::Yellow
    "Number" = [ConsoleColor]::Blue
    "Type" = [ConsoleColor]::Cyan
    "Comment" = [ConsoleColor]::DarkCyan
}
$PSReadLineOptions = @{
	EditMode = "Windows"
	PredictionSource = "History"
	PredictionViewStyle = "ListView"
	Color = $PSReadLineColorOptions
}
Set-PSReadLineOption @PSReadLineOptions
```
