# Test

Male(Block) :
$folder = "C:\Program Files (x86)\TOPOO\ECLASS"

Get-ChildItem -Path $folder -Filter "*.exe" -Recurse | ForEach-Object {
    New-NetFirewallRule -DisplayName "Block_EClass_(_.Name)_In" -Direction Inbound -Program $_.FullName -Action Block
    New-NetFirewallRule -DisplayName "Block_EClass_(_.Name)_Out" -Direction Outbound -Program $_.FullName -Action Block
}

Female(Block) :
New-NetFirewallRule -DisplayName "Block_Teacher_In" -Direction Inbound -RemoteAddress "192.168.13.101" -Action Block -Profile Any
New-NetFirewallRule -DisplayName "Block_Teacher_Out" -Direction Outbound -RemoteAddress "192.168.13.101" -Action Block -Profile Any

$AdapterName = "乙太網路" $Adapter = Get-NetAdapter -Name $AdapterName -ErrorAction SilentlyContinue
if ($Adapter.Status -eq "Up") { Disable-NetAdapter -Name AdapterName-Confirm:false Write-Host "Internet DISCONNECTED ($AdapterName disabled)." -ForegroundColor Red } else { Enable-NetAdapter -Name AdapterName-Confirm:false Write-Host "Internet RECONNECTED ($AdapterName enabled)." -ForegroundColor Green }
