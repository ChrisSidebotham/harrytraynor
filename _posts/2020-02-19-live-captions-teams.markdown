---
layout: post
title:  "Live Captions in Teams"
date:   2020-02-19 18:00 +0000
categories: Teams Office365
---
Accessibility should be the default. Teams has many solutions for accessibility, but if you are deaf or hearing impaired you can use the live captions tool to follow along in the call.

You can control whether this is turned on via PowerShell and the Office 365 Admin Centre - but below is the method to use PowerShell.

First you will need to install the [Skype For Business PowerShell Connector][skype-connector]... yes you heard right!

Then run the following command to connect to your tenant.

```powershell
Import-Module SkypeOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
```

You can then check what your current setting preference is. The two possible values are **Disabled** and **DisabledUserOverride**. This will either disable it completely or allow the user to turn captions on once the meeting has started.

```powershell
Get-CsTeamsMeetingPolicy | ft identity, live*
```
And then finally you can enable this feature by running this last command.

```PowerShell
# Enable
Set-CsTeamsMeetingPolicy -LiveCaptionsEnabledType DisabledUserOverride

# Disable
Set-CsTeamsMeetingPolicy -LiveCaptionsEnabledType Disabled
```

[skype-connector]: https://www.microsoft.com/download/details.aspx?id=39366
