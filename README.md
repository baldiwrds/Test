# Test

$AdapterName = "乙太網路"
$Adapter = Get-NetAdapter -Name $AdapterName -ErrorAction SilentlyContinue

if ($Adapter.Status -eq "Up") {
    Disable-NetAdapter -Name $AdapterName -Confirm:$false
    Write-Host "Internet DISCONNECTED ($AdapterName disabled)." -ForegroundColor Red
} else {
    Enable-NetAdapter -Name $AdapterName -Confirm:$false
    Write-Host "Internet RECONNECTED ($AdapterName enabled)." -ForegroundColor Green
}
