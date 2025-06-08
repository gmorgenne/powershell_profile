# powershell profile

I use windows terminal with oh-my-posh, both are installed via the microsoft store
Then add Terminal-Icons
then add posh-git
then add PSReadLine and enable history with listview

This is the sitecore theme, but it requires the image to be downloaded
full profile:
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
