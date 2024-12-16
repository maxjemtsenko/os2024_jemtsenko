Praktikum 13 - Skriptimine Windowsis

```
Start-Transcript -Path "output.txt"

$hostname = hostname 
Write-Host "Hostname:" $hostname

$version = $PSVersionTable.PSVersion
Write-Host "PowerShelli versioon: $version"

$osVersion = (Get-ComputerInfo).OsVersion
Write-Host "Windowsi versioon: $osVersion"

Write-Host "`nVõrgu konfiguratsioon"
Get-WmiObject Win32_NetworkAdapterConfiguration -Filter "IPEnabled='True'" | Where-Object { $_.Description -like "*Wi-Fi*" } | Select-Object IPAddress, IPSubnet, DefaultIPGateway, DHCPEnabled, MACAddress | Format-Table -AutoSize

Write-Host "`n Mälu"
Get-WmiObject Win32_ComputerSystem | Select-Object TotalPhysicalMemory | Format-Table -AutoSize

Write-Host "`nProtsessor"
Get-WmiObject Win32_Processor | Format-Table -AutoSize

Write-Host "`n Videokaart"
Get-WmiObject Win32_VideoController | Select-Object Name, DriverVersion, DriverDate, @{Name="Resolution";Expression={"$($_.CurrentHorizontalResolution) x $($_.CurrentVerticalResolution)"}} | Format-Table -AutoSize

Write-Host "`n Kõvaketasteetaste info"
Get-Partition | Format-Table
Get-WmiObject Win32_LogicalDisk | Select-Object DeviceID, FileSystem, @{Name="Size (GB)";Expression={[math]::Round($_.Size/1GB,2)}}, @{Name="FreeSpace (GB)";Expression={[math]::Round($_.FreeSpace/1GB,2)}} | Format-Table -AutoSize

Write-Host "`nPCI draiverite info"
Get-WmiObject –Class Win32_PnpSignedDriver | Where-Object {$_.DeviceID –like "PCI*"} | Select-Object Description, DriverVersion | Sort-Object Description | Format-Table -AutoSize

Write-Host "`nKasutajad"
Get-WmiObject Win32_UserAccount | Select-Object Name, Description, LocalAccount, Disabled | Format-Table -AutoSize

Write-Host "`nViimased protsessid "
Get-Process | Where-Object {$_.StartTime -ne $null} | Sort-Object StartTime -Descending | Select-Object -First 10 Name, Id, StartTime | Format-Table -AutoSize

$protsesside_arv = (Get-Process).Count
Write-Host "`nKäimasolevate protsesside arv: $protsesside_arv"

Write-Host "`nKuupäev ja kellaaeg"
Write-Host (Get-Date)

Stop-Transcript
```
