Documentação e Download
============================
Download link: [Adobe Acrobat Reader DC](https://get.adobe.com/reader/enterprise/)

Documentação Download: [Documentação](https://www.adobe.com/devnet-docs/acrobatetk/tools/VirtualizationGuide/cmdline.html#msi-support)


1) Baixe a versão mais recente;
2) Extraia para uma nova pasta do executável;
3) (OPCIONAL) Instale "1-CustWiz2200320310_en_US_DC.exe" para configurar opções específicas a serem aplicadas via GPO;
4) Crie a GPO usando o arquivo MSI extraído acima usando as configurações personalizadas que você criou com o Custow Wizard acima (este último, opcional);

Extract MSI files
> cmd /c D:\Downloads\AcroRdrDC2300320269_en_US.exe -sfx_o"D:\Downloads\Reader" -sfx_ne

Create administrative installation point
> cmd /c msiexec /a "D:\Downloads\Reader\AcroRead.msi" TARGETDIR="D:\Downloads\Reader_deployment"

Update administrative installation point
> cmd /c msiexec /a "D:\Downloads\Reader_deployment\AcroRead.msi" /p "D:\Downloads\Reader\AcroRdrDCUpd2300320269.msp" TARGETDIR="D:\Downloads\Reader_deployment"
