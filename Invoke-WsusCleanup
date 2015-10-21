$distributionGroup = "WSUS@Contoso.com"
$PSEmailServer = "MAILRELAY.CONTOSO.COM"

$output = @()

$output += "$env:COMPUTERNAME was cleaned, the notes from the cleanup are below."
$output += "`n"

$output += Get-WsusServer | Invoke-WsusServerCleanup -CleanupObsoleteComputers
$output += "`n"
$output += Get-WsusServer | Invoke-WsusServerCleanup -CleanupUnneededContentFiles
$output += "`n"
$output += Get-WsusServer | Invoke-WsusServerCleanup -CompressUpdates
$output += "`n"
$output += Get-WsusServer | Invoke-WsusServerCleanup -DeclineExpiredUpdates
$output += "`n"
$output += Get-WsusServer | Invoke-WsusServerCleanup -DeclineSupersededUpdates
$output += "`n"
$output += Get-WsusServer | Invoke-WsusServerCleanup -CleanupObsoleteUpdates

Send-MailMessage -From "$env:COMPUTERNAME@$env:USERDNSDOMAIN" -To $distributionGroup -Subject "WSUS Server Cleanup" -Body "$output"
