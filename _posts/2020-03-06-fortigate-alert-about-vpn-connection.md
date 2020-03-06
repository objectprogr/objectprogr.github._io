---
layout: post
title: "FortiGate alert about VPN connecTion"
excerpt: "FortiGate alert about VPN connecyion"
paermalink: /2020/03/fortigate-alert-about-vpn-connection.html
tags: powershell fortigate vpn
categories: homepage
---


In our company We`ll needed start manage FortiGate logs. We decide that the first step will be detect in logs information about VPN connection/disconnecting and sending alert to email.

# Assumptions
- detect VPN connection/disconnection in logs
- prepare and send email with details

# FortiGate configuration
To beginning We started new machine with Windows 10 pro and installing [Kiwi Syslog Server Free Edition](https://www.kiwisyslog.com/free-tools/kiwi-free-syslog-server). On DHCP server We have created reservation for Windows where installed kiwi syslog server.
Open Kiwi Syslog Server and go to File - Setup - Inputs and add IP address (IP address your FortiGate) - Apply - OK.
Go to FortiGate (We use FortiGate 60D v6.0.5) - Log&Report - Log Settings - enable Send Logs to Syslog and add IP address computer where is installed Kiwi Syslog Server - Applay.
Now, back to Kiwi Syslog Server and now you should see logs from FortiGate.

# Powershell script
Next step is writing powershell script which will be searching informations about VPN connection/disconnection.

```powershell
#CSS
$CSS = @"
    <style>
TABLE {width: 600px; border-width: 1px; border-style: solid; border-color: black; border-collapse: collapse; font-family: Tahoma; background-color: rgb(252, 252, 252); }
TH {border-width: 1px; padding: 3px; border-style: solid; border-color: #bebebe;  color: #9696dc; font-size: 12pt;}
TD {border-width: 1px; padding: 3px; border-style: solid; border-color: #bebebe; font-size: 11pt; text-align: center;}
H4 {font-family: Tahoma; font-size: 10pt; color: #9696dc; font-style: italic;}
SPAN {font-family: Tahoma; font-size: 10pt; color: #9696dc; font-style: italic;}
    </style>
"@
#------------------------------|
# Variables
$currentDate = Get-Date -Format "yyyy-MM-dd"
$currentDateTime = Get-Date -Format 'yyyy-MM-dd hh-mm-ss'

#------------------------------|
#Tmp file where will be adding entries that were previously found
#Before sendind alert script checking this tmp file hasn't been sent before

#$tmpFile = "C:\test logs\"
$tmpFile = "C:\FortigateLogs_VPN\tmpFiles\"
$tmpFileName = "tmpFile-tunnelUp-" + $currentDate + ".txt"
$finalTmpFile = Join-Path $tmpFile $tmpFileName

#------------------------------|
# Path to kiwi log files
#$LogsPath = "C:\test logs\"
$LogsPath = "C:\Kiwi syslog\Syslogd\Logs\"

#------------------------------|
# Creating date in format like kiwi syslog save log file name SyslogCatchAll- + actuall date
$logName = "SyslogCatchAll-" + $currentDate + ".txt"
$FinalLogPath = Join-Path $LogsPath $logName
$IPaddress = Get-NetIPAddress |Where {$_.IPAddress -like '192.168.*'} | select IPAddress
$FinalIP = $IPaddress | ForEach-Object {
    $_ -replace '{','' `
       -replace '}','' `
       -replace 'IPAddress=','' `
       -replace '@','' 
}

#------------------------------|
# HTML report
$htmlReportName = "HtmlReport " + $currentDateTime.ToString() + ".html"
$htmlReportTitle = "Fortigate VPN - TUNNEL UP " + $currentDateTime
$htmlReportHeader = "<h2>Fortigate VPN - TUNNEL UP report $currentDateTime</h2><span>Source: $FinalLogPath</span>"

#------------------------------|
#Informtaion about kiwi syslog server location
$Footer = "<span>Report generated in computer: $env:computername IP: $FinalIP</span>"

#------------------------------|
#Find in logs
$query1 =  Select-String -Path $FinalLogPath -Pattern "tunnel-up" | ConvertFrom-String 

foreach($query in $query1){
    if([string]::IsNullOrEmpty($query)){
        
    }else{
        $gg = $query | select @{Name='Date';Expression={$_.P6.substring(5,10)}}, @{Name='Time'; Expression={$_.P3}}

        if([System.IO.File]::Exists($finalTmpFile)){
            $data = Get-Content $finalTmpFile
        }else{
        $sasaas = $data | %{$_ -match $gg }
        if($sasaas -contains $true){
            
        }else{
    #------------------------------|
    #Execute
    #Getting only this information which we want 

    $emailBody2 = $query | select @{Name='Date';Expression={$_.P6.substring(5,10)}},
        @{Name='Time';Expression={$_.P3}},
        @{Name='Action';Expression={$_.P24.substring(8,9)}} | 
        ConvertTo-Html -Title $htmlReportTitle -PreContent $htmlReportHeader -Head $CSS

    $emailBody3 = $query | select @{Name='Remip';Expression={($_.P25)}},
        @{Name='Locip';Expression={($_.P26)}} | 
        ConvertTo-Html 

    $emailBody4 = $query | select @{Name='User';Expression={($_.P33 )}}, 
        @{Name='Xauthgroup';Expression={($_.P34 )}} | 
        ConvertTo-Html 

    $emailBody5 = $query | select @{Name='AssignIP';Expression={($_.P35 )}},
        @{Name='VPNtunnel';Expression={($_.P36 )}},
        @{Name='TunnelIP';Expression={($_.P37 )}} | 
        ConvertTo-Html 

    #------------------------------|
    #Delete all unnecessary informations

    $finalEmailBody1  = $emailBody3 | ForEach-Object {
        $_ -replace 'remip=','' `
        -replace 'locip=',''
    }
    $finalEmailBody2  = $emailBody4 | ForEach-Object {
        $_ -replace 'xauthuser=','' `
        -replace '&quot;','' `
        -replace 'xauthgroup=',''
    }
    $finalEmailBody3  = $emailBody5 | ForEach-Object {
        $_ -replace '&quot;','' `
        -replace 'assignip=','' `
        -replace 'vpntunnel=','' `
        -replace 'tunnelip=','' 
    }
    #------------------------------|
    # Send email
    $SMTPServer = "" 
    $EmailFrom = ""
    $EmailTo =  "" 
    $Subject = $htmlReportTitle  
    $body =  $emailBody2 + $finalEmailBody1 + $finalEmailBody2 + $finalEmailBody3 + $Footer
    $SMTPClient = New-Object Net.Mail.SmtpClient($SmtpServer, smtpPORT) 
    $SMTPClient.EnableSsl = $false
    $SMTPClient.Credentials = New-Object System.Net.NetworkCredential("login", "password");
    $msg = New-object Net.Mail.MailMessage($EmailFrom, $EmailTo, $Subject, $body)
    $msg.IsBodyHTML = $true  
    $SMTPClient.Send($msg)
    #------------------------------|
    #Save data to tmp file
    Add-Content $finalTmpFile $gg
}
        }
    }
}
```
Last step is adding this script to windows task scheduler. We settings 5 minuts interval.

# Examples
![Report](/assets/images/report.png)