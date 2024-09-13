Documentação e Download
============================
Download link: Adobe Acrobat Reader DC
Documentação Download: 

1) Baixe a versão mais recente em: https://get.adobe.com/br/reader/enterprise/;
2) Extraia para uma nova pasta do executável baixado acima;
3) (OPCIONAL) Instale "1-CustWiz2200320310_en_US_DC.exe" para configurar opções específicas a serem aplicadas via GPO;
4) Crie a GPO usando o arquivo MSI extraído acima usando as configurações personalizadas que você criou com o Custow Wizard acima (este último, opcional);





Documentation and download
Download link: Adobe Acrobat Reader DC
Documentation link: Documentation

Extract MSI files
cmd /c D:\Downloads\AcroRdrDC2300320269_en_US.exe -sfx_o"D:\Downloads\Reader" -sfx_ne
Create administrative installation point
cmd /c msiexec /a "D:\Downloads\Reader\AcroRead.msi" TARGETDIR="D:\Downloads\Reader_deployment"
Update administrative installation point
cmd /c msiexec /a "D:\Downloads\Reader_deployment\AcroRead.msi" /p "D:\Downloads\Reader\AcroRdrDCUpd2300320269.msp" TARGETDIR="D:\Downloads\Reader_deployment"
My enviroment setup
Group Policy and settings that i have configured in my servers and clients
Group Policy: Creating 32 and 64 bit WMI filters
Group Policy: Always Wait for the Network at Computer Startup and Logon
Group Policy: Display highly detailed status messages
Group Policy: Create an "Install a Program from the Network" desktop shortcut
My windows server setup:
Windows Server 2022: Install File Server role and prepare a share for software deployment with GPO
Windows Server 2022: Install DHCP server
Windows Server 2022: Install Active Directory Domain Services (AD DS)
