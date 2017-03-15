---
title: "Como criar um manifesto de produto | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "dependências, pacote de inicializador personalizado"
  - "pré-requisitos, pacote de inicializador personalizado"
  - "arquivos de produto [ClickOnce]"
  - "arquivos de produto [Windows Installer]"
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como criar um manifesto de produto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para implantar os pré\-requisitos para seu aplicativo, você pode criar um pacote de bootstrapper.  Um pacote de bootstrapper contém um arquivo de manifesto único produto, mas um manifesto de pacote para cada localidade.  O manifesto de pacote contém os aspectos específicos de localização do seu pacote.  Isso inclui seqüências de caracteres, os contratos de licença de usuário final e os pacotes de idiomas.  
  
 Para obter mais informações sobre manifestos de produto, consulte [Como criar um manifesto de pacote](../deployment/how-to-create-a-package-manifest.md).  
  
## Criando o manifesto do produto  
  
#### Para criar o manifesto do produto  
  
1.  Crie um diretório para o pacote de bootstrapper.  Este exemplo usa o C:\\package.  
  
2.  No Visual Studio, crie um novo arquivo XML chamado  `Product. XML`e salvá\-lo para a pasta C:\\package.  
  
3.  Adicione o seguinte XML para descrever o código de produto e o espaço para nome XML para o pacote.  Substitua o código de produto com um identificador exclusivo para o pacote.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  Adicione o XML para especificar que o pacote tem uma dependência.  Este exemplo usa uma dependência no 3.1 do Microsoft Windows Installer.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  Adicione o XML para listar todos os arquivos que estão no pacote bootstrapper.  Este exemplo usa o nome de arquivo do pacote CorePackage.msi.  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  Copiar ou mover o arquivo CorePackage.msi para a pasta C:\\package.  
  
7.  Adicione o XML para instalar o pacote usando os comandos de bootstrapper.  O bootstrapper adiciona automaticamente o **\/qn** sinalizar para o arquivo. msi, que instalará silenciosamente.  Se o arquivo for um. exe, o bootstrapper executa o arquivo. exe usando o shell.  O XML a seguir mostra o sem argumentos para CorePackage.msi, mas você pode colocar o argumento de linha de comando para o atributo de argumentos.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  Adicione o seguinte XML para verificar se este pacote de bootstrapper está instalado.  Substitua o código do produto com o GUID para o componente redistribuível.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Adicione o XML para alterar o comportamento de bootstrapper dependendo se o componente de bootstrapper já estiver instalado.  Se o componente estiver instalado, o pacote de bootstrapper não é executado.  O XML a seguir verifica se o usuário atual for um administrador porque este componente requer privilégios administrativos.  
  
    ```  
    <InstallConditions>  
        <BypassIf   
           Property="IsMsiInstalled"   
           Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
            Compare="ValueNotEqualTo" Value="True"  
            String="NotAnAdmin"/>  
    </InstallConditions>  
    ```  
  
10. Adicione o XML para definir códigos de saída, se a instalação for bem\-sucedida e se uma reinicialização é necessária.  O XML a seguir demonstra que a falha e FailReboot códigos, o que indicam que o bootstrapper não continuará instalando pacotes de saída.  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Adicione o seguinte XML para finalizar a seção para comandos de bootstrapper.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. Mova a pasta de C:\\package para o diretório de bootstrapper de Visual Studio.  Para 2010 Visual Studio, este é o diretório \\Program Files\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages.  
  
## Exemplo  
 O manifesto do produto contém instruções de instalação para pré\-requisitos personalizados.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Product  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  ProductCode="Custom.Bootstrapper.Package">  
  
  <RelatedProducts>  
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
  </RelatedProducts>  
  
  <PackageFiles>  
    <PackageFile Name="CorePackage.msi"/>  
  </PackageFiles>  
  
  <InstallChecks>  
    <MsiProductCheck Product="IsMsiInstalled"   
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
  </InstallChecks>  
  
  <Commands>  
    <Command PackageFile="CorePackage.msi" Arguments="">  
  
      <InstallConditions>  
        <BypassIf Property="IsMsiInstalled"  
          Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
          Compare="ValueNotEqualTo" Value="True"  
         String="NotAnAdmin"/>  
      </InstallConditions>  
  
      <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
      </ExitCodes>  
    </Command>  
  </Commands>  
</Product>  
```  
  
## Consulte também  
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)