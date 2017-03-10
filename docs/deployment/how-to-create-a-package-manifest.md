---
title: "Como criar um manifesto de pacote | Microsoft Docs"
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
  - "dependências, pacotes de inicializador personalizados"
  - "arquivos de pacote [ClickOnce]"
  - "arquivos de pacote [Windows Installer]"
  - "pré-requisitos, pacote de inicializador personalizado"
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como criar um manifesto de pacote
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para implantar os pré\-requisitos para seu aplicativo, você pode usar um pacote de bootstrapper.  Um pacote de bootstrapper contém um arquivo de manifesto único produto, mas um manifesto de pacote para cada localidade.  Funcionalidade compartilhada entre diferentes versões localizadas deve entrar no manifesto do produto.  
  
 Para obter mais informações sobre manifestos de pacote, consulte [Como criar um manifesto de produto](../deployment/how-to-create-a-product-manifest.md).  
  
## Criando o manifesto do pacote  
  
#### Para criar o manifesto do pacote  
  
1.  Crie um diretório para o pacote de bootstrapper.  Este exemplo usa o C:\\package.  
  
2.  Crie um subdiretório com o nome da localidade, como, por exemplo, en para inglês.  
  
3.  No Visual Studio, crie um arquivo XML chamado  `Package. XML`e salvá\-lo para a pasta C:\\package\\en.  
  
4.  Adicione o XML para listar o nome do pacote bootstrapper, a cultura para esse manifesto do pacote localizado e o contrato de licença opcional.  O XML a seguir usa as variáveis `DisplayName` e `Culture`, que são definidos em um elemento posterior.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  Adicione o XML para listar todos os arquivos que estão no diretório específicos da localidade.  O XML a seguir usa um arquivo chamado EULA. txt que é aplicável para o  **en** localidade.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  Adicione o XML para definir seqüências de caracteres localizáveis para o pacote de bootstrapper.  O XML a seguir adiciona as strings de erro para a localidade en.  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7.  Copie a pasta C:\\package para o diretório de bootstrapper de Visual Studio.  Para 2010 Visual Studio, este é o diretório \\Program Files\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages.  
  
## Exemplo  
 O manifesto de pacote contém informações específicas de localidade, como, por exemplo, mensagens de erro, os termos de licença de software e pacotes de idiomas.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.txt">  
  
  <PackageFiles>  
    <PackageFile Name="eula.txt"/>  
  </PackageFiles>  
  
  <Strings>  
    <String Name="DisplayName">Custom Bootstrapper Package</String>  
    <String Name="Culture">en</String>  
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>  
    <String Name="GeneralFailure">A general error has occurred while   
installing this package.</String>  
  </Strings>  
</Package>  
```  
  
## Consulte também  
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)