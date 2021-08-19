**Initial Microsoft Business Central on Sandbox (Prepare Development Environment)**

**For more your information:**
[Working with Development Sandboxes and Entitlements](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/devenv-work-sandbox-entitlements)

**Preparing Hyper-V**
1. Run script via powershell to enable hyper-v
> Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All

**Preparing Docker for Window Desktop**
1. Download [Docker](https://www.docker.com/) 
2. Install Docker 
3. SignUp & SignIn Docker 
4. Switch the docker mode from Linux to Window container via right click the icon

**Preparing Docker for Window Server**
1. Run powershell to install docker
> Install-Module -Name DockerMsftProvider -Repository PSGallery -Force

> Install-Package -Name docker -ProviderName DockerMsftProvider

**Preparing Powershell**
1. Install [BcContainerHelper](https://www.powershellgallery.com/packages/BcContainerHelper/) via powershell
> Install-Module -Name BcContainerHelper
2. Create container & download image via powershell
> New-BCContainer -accept_eula -updateHosts -containerName bcsandboxau -artifactUrl (Get-BCArtifactUrl -country au) -assignPremiumPlan -WebClientPort 1234 -DeveloperServicesPort 1804 -auth NavUserPassword
3. Fill user & password. 

**Error**
If username contain dot or password is not meet at least 1 upper and 1 number, suggest to use P@ssword1
> unable to update the password. the value provided for the new password does not meet the length, complexity, or history requirements of the domain.

**Forward Port from Docker to public**
> netsh interface portproxy delete v4tov4 listenport=1234 listenaddress=[Host LocalIP]
> netsh interface portproxy delete v4tov4 listenport=1804 listenaddress=[Host LocalIP]

> netsh interface portproxy add v4tov4 listenport=1234 listenaddress=[Host LocalIP] connectport=1234 connectaddress=[Docker LocalIP]
> netsh interface portproxy add v4tov4 listenport=1804 listenaddress=[Host LocalIP] connectport=1804 connectaddress=[Docker LocalIP]

Example [Host LocalIP] = 192.168.10.102

**Preparing Visual Studio Code**
1. Download & Install [VSCode](https://code.visualstudio.com/)
2. Open VSCode and Install AL Language from Extension Marketplace
