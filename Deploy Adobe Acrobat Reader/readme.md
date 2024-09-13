# Guia de Configuração do Adobe Acrobat Reader DC via GPO

Este repositório fornece um guia passo a passo para instalar e configurar o **Adobe Acrobat Reader DC** em um ambiente corporativo usando **GPOs (Group Policy Objects)**. O processo inclui instruções sobre como baixar, extrair e personalizar a instalação do Acrobat Reader DC, com a opção de configurar parâmetros específicos via **Adobe Customization Wizard**.

A seguir, você encontrará o tutorial completo, incluindo links para download e comandos necessários para preparar e implantar o software.

---

## **Documentação e Download**

### Download do Adobe Acrobat Reader DC

Baixe a versão corporativa mais recente do **Adobe Acrobat Reader DC** diretamente do site oficial:

[Adobe Acrobat Reader DC](https://get.adobe.com/reader/enterprise/)

### Download do Adobe Customization Wizard (Opcional)

Baixe a versão mais recente do **Adobe Customization Wizard** diretamente do site oficial:

[Adobe Customization Wizard](https://ardownload3.adobe.com/pub/adobe/acrobat/win/AcrobatDC/misc/CustWiz2200320310_en_US_DC.exe)

### Documentação Oficial da Adobe

Para mais detalhes sobre a personalização e suporte de instalação via MSI, consulte a documentação oficial:

[Documentação Adobe Acrobat Reader DC](https://www.adobe.com/devnet-docs/acrobatetk/tools/VirtualizationGuide/cmdline.html#msi-support)

[Documentação Adobe Customization Wizard](https://www.adobe.com/devnet-docs/acrobatetk/tools/Wizard/index.html)

---

## **Passo a Passo para criação do Instalador via MSI**

### 1. **Baixe a Versão Mais Recente**_

- Acesse o link de download acima e faça o download do instalador corporativo do **Adobe Acrobat Reader DC**.

### 2. **Extraia o Executável para uma Nova Pasta**

- Após o download, extraia o conteúdo do instalador para uma pasta específica. O comando abaixo pode ser utilizado para essa finalidade:

```bash
cmd /c C:\Temp\AcroRdrDC2400320112_pt_BR.exe -sfx_o"C:\Temp\Reader" -sfx_ne
```

### 3. Criar Ponto de Instalação Administrativa
Após extrair o instalador, você deve criar um ponto de instalação administrativa para facilitar o gerenciamento e implantação do software:

```bash
cmd /c msiexec /a "C:\Temp\Reader\AcroRead.msi" TARGETDIR="C:\Temp\Reader_deployment"
```

### ** (Opcional) Personalize as Opções de Instalação via Customization Wizard
Se desejar aplicar configurações específicas, instale o Adobe Customization Wizard. Ele permite personalizar diversas opções antes da implantação via GPO.
Use o Customization Wizard para desativar atualizações automáticas, configurar políticas de segurança, entre outras opções.

### 4. Atualizar o Ponto de Instalação Administrativa
Para garantir que a instalação esteja sempre atualizada, aplique as atualizações mais recentes ao ponto de instalação:

```bash
cmd /c msiexec /a "C:\Temp\Reader_deployment\AcroRead.msi" /p "C:\Temp\Reader\AcroRdrDCUpd2400320112.msp" TARGETDIR="C:\Temp\Reader_deployment"
```

### 5. Crie a GPO Usando o Arquivo MSI Extraído
Com as configurações personalizadas criadas no Customization Wizard (caso tenha utilizado), prossiga para a criação da GPO usando o arquivo MSI extraído. O arquivo MSI será utilizado para implementar as configurações personalizadas na rede.
