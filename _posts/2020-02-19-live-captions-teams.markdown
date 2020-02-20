---
layout: post
title:  "Live Captions in Teams"
date:   2020-02-19 18:00 +0000
categories: Teams Office365
---
Accessibility should be the default. Teams has many solutions for accessibility, but if you are deaf or hearing impaired you can use the live captions to follow along in calls or meetings.

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

```powershell
# Enable
Set-CsTeamsMeetingPolicy -LiveCaptionsEnabledType DisabledUserOverride

# Disable
Set-CsTeamsMeetingPolicy -LiveCaptionsEnabledType Disabled
```

For a list of all the other Teams call based policies you can set - Microsoft has great [documentation][skype-policy-settings] on what you can change these settings.

[skype-connector]: https://www.microsoft.com/download/details.aspx?id=39366
[skype-policy-settings]: https://docs.microsoft.com/en-us/powershell/module/skype/set-csteamsmeetingpolicy?view=skype-ps
