# Security Tools for Non-Standard Hospitals

## Contents

* Crowdstrike
* Rapid7 Agent
* ~~BigFix Agent~~ (We're waiting to finalize install media)
* ~~Druva~~ (We're waiting on download media)

### Crowdstrike

#### Windows Method 1: Download/Install with powershell

Run the following powershell commands to download and install Crowdstrike:

````powershell
Invoke-WebRequest -uri "https://s3.ca-central-1.amazonaws.com/pub.vcacanada.com/security_software/crowdstrike/windows/latest-2/WindowsSensor.exe" -OutFile "$env:TEMP\WindowsSensor.exe"
."$env:TEMP\WindowsSensor.exe" /install /quiet /norestart CID=289A4403E72C41AFAC93DB969D041FD7-AD PROXYDISABLE=1 ProvNoWait=1
````

#### Windows Method 2: Download manually and install with command prompt

Download a copy of the installer [here](https://s3.ca-central-1.amazonaws.com/pub.vcacanada.com/security_software/crowdstrike/windows/latest-2/WindowsSensor.exe). Once downloaded, run the following `cmd` command from the directory you downloaded the installer into:

````powershell
WindowsSensor.exe /install /quiet /norestart CID=289A4403E72C41AFAC93DB969D041FD7-AD PROXYDISABLE=1 ProvNoWait=1
````

#### Windows: Verify install

No restart is necessary after installing, so to verify the install simply run the following command in a `cmd` or `powershell` prompt and verify that `STATE = "Running"`.  It may take a minute or two after running the install command before the service will show up.

````powershell
sc.exe query csfalconservice
````

#### Mac

Download a copy of the installer [here](https://s3.ca-central-1.amazonaws.com/pub.vcacanada.com/security_software/crowdstrike/mac/latest-2/FalconSensorMacOS.pkg). Once downloaded, double click on the `.pkg` installer.

````zsh
sudo /Applications/Falcon.app/Contents/Resources/falconctl grouping-tags set "VCA,VCA_Canada"


sudo /Applications/Falcon.app/Contents/Resources/falconctl license us:e5f592cd-bf99-454e-81a7-8f270446bd24
````

### Rapid7 Agent

Windows:

1. [Download a copy of the agent](https://pub.vcacanada.com/security_software/rapid7/windows/agentInstaller-x86_64.msi)
2. Run this command in an elevated powershell window while inside the same working directory as the `.msi` file:

````powershell
msiexec /i agentInstaller-x86_64.msi /l*v insight_agent_install_log.log /quiet CUSTOMTOKEN=us:e5f592cd-bf99-454e-81a7-8f270446bd24 CUSTOMATTRIBUTES="VCA,VCA_Canada"
````

You can verify the installation by running the following command inside a command prompt window:

````cmd
sc.exe query ir_agent
````

Linux:

1. [Download the install script](https://pub.vcacanada.com/security_software/rapid7/linux/agent_installer.sh)
2. Run the following commands inside a terminal:

````bash
chmod u+x agent_installer.sh
sudo ./agent_installer.sh install_start --token us:e5f592cd-bf99-454e-81a7-8f270446bd24 --attributes "VCA,VCA_Canada"
````

<!-- ### BigFix Agent

1.	Install BigFix agent for remote systems
\\vcaantech.com\folders\Apps\install_media\InfoSec\IBM\IBM BigFix Client\9.5.17.94 - Off Network
2.	Extract all files and run ‘BigFixAgent.msi’
NOTE: The clientsettings.cfg file must be in the same folder as the BigFixAgent.msi installer
3.	Register agent to DMZ Relay:Register agent to DMZ Relay:
1.	From command prompt run: 
C:\Program Files (x86)\BigFix Enterprise\BES Client\BESClient -register <password> http://bf.vca.com:52311"
2.	Restart the Besclient service -->

### Druva

If you do not have an offsite backup, please install Druva on all servers housing critical data. The practice management software is the bare minimum we want to backup. If this is the case, please contact the VCA Canada IT Team immediately.
