# Security Tools for Non-Standard Hospitals

## Contents

* Crowdstrike
* Rapid7 Agent
* ~~BigFix Agent~~ (We're waiting to finalize install media)
* ~~Druva~~ (We're waiting on download media)

### Crowdstrike

#### Windows

Download a copy of the installer [here](https://s3.ca-central-1.amazonaws.com/pub.vcacanada.com/security_software/crowdstrike/WindowsSensor_7.04.17605.exe). Once downloaded, run the following command:

````powershell
WindowsSensor_7.04.17605.exe /install /quiet /norestart CID=289A4403E72C41AFAC93DB969D041FD7-AD PROXYDISABLE=1 ProvNoWait=1
````

You do not need to restart any machines for this to take effect. 

Verify installation:

1. In a command prompt window run `sc query csfalconservice`
2. Verify `STATE = "Running"`

#### Mac

Download a copy of the installer [here](https://pub.vcacanada.com/security_software/crowdstrike/FalconSensorMacOS_6.23.13601.pkg). Once downloaded, double click on the `.pkg` installer.

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
sc query ir_agent
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
