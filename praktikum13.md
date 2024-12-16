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
``` Start-Transcript -Path "os_praktikum13_output.txt" ``` ja ```Stop-Transcript``` - Alustab kõigi väljundite kirjutamist faili "os_praktik13_output.txt" ja Peatab väljundi faili kirjutamise.
```$hostname = hostname``` - Salvestab arvuti nime muutujas $hostname ja kuvab selle käsu Write-Host abil.
```$version = $PSVersionTable.PSVersion``` - Hangib PowerShelli versiooni ja kuvab selle.
```$osVersion = (Get-ComputerInfo).OsVersion``` - Hangib Windowsi operatsioonisüsteemi versiooni ja kuvab selle.
```Get-WmiObject Win32_NetworkAdapterConfiguration``` - Otsib teavet võrguadapterite kohta.
```Get-WmiObject Win32_ComputerSystem``` – hangib kogu süsteemi füüsilise mälu ja kuvab selle.
```Get-WmiObject Win32_Processor``` – hangib protsessori teabe.
```Get-WmiObject Win32_VideoController``` - hangib teavet videokaardi kohta.
```Get-Partition``` – kuvab teavet ketta partitsioonide kohta.
```Get-WmiObject Win32_LogicalDisk``` – hangib: Seadme ID, failisüsteem kogumaht (gigabaitides), vaba ruumi (gigabaitides).
```Get-WmiObject Win32_PnpSignedDriver``` – hangib PCI-seadmete draiverite loendi, sealhulgas nende kirjelduse ja draiveri versiooni.
```Get-WmiObject Win32_UserAccount``` – hangib kohalike kasutajate loendi.
```Get-Process``` – hangib teavet protsesside kohta.
```Get-Date``` – kuvab praeguse kuupäeva ja kellaaja.
