---
title: "Criando pacotes de bootstrapper | Microsoft Docs"
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
  - "Implantando aplicativos [Visual Studio], pré-requisitos"
  - "Implantando aplicativos [Visual Studio], pré-requisitos personalizados"
  - "pré-requisitos, personalizados"
  - "Arquivo RedistList"
  - "pré-requisitos personalizados"
  - "lista de redistribuíveis"
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
caps.latest.revision: 45
caps.handback.revision: 45
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Criando pacotes de bootstrapper
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O programa de instalação é um instalador genérico que pode ser configurado para detectar e instalar componentes redistribuíveis, como programas executáveis e arquivos do Windows Installer \(. msi\). O instalador também é conhecido como bootstrapper. Ele é programado por um conjunto de manifestos XML que especificam os metadados para gerenciar a instalação do componente.  
  
 O bootstrapper primeiro detecta se qualquer um dos pré\-requisitos já estão instalados. Se os pré\-requisitos não estiverem instalados, primeiro o bootstrapper mostra os contratos de licença. Em segundo lugar, depois que o usuário final aceita os contratos de licença, a instalação dos pré\-requisitos começa. Caso contrário, se todos os pré\-requisitos forem detectados, o bootstrapper apenas inicia o instalador do aplicativo.  
  
## Criando pacotes personalizados  
 Você pode gerar os manifestos usando o Editor de XML no Visual Studio. Para obter mais informações, consulte [Como criar um manifesto de pacote](../deployment/how-to-create-a-package-manifest.md) e [Como criar um manifesto de produto](../deployment/how-to-create-a-product-manifest.md). Para ver um exemplo de como criar um pacote de bootstrapper, consulte [Instruções passo a passo: criando um bootstrapper personalizado para mostrar um prompt de privacidade](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).  
  
 Para criar um pacote de bootstrapper, você precisa fornecer o redistribuível na forma de um EXE ou MSI ao gerador de manifesto do Bootstrapper. Em seguida, o gerador de manifesto do Bootstrapper cria os seguintes arquivos:  
  
-   O manifesto do produto, Product, que contém todos os metadados para o pacote de idioma neutro. Contém metadados comuns a todas as versões localizadas do componente redistribuível.  
  
-   O manifesto do pacote, Package. XML, que contém metadados específicos do idioma. Ele geralmente contém mensagens de erro localizada. Um componente deve ter pelo menos um manifesto de pacote para cada versão localizada desse componente.  
  
 Depois que esses arquivos são criados, coloque o arquivo de manifesto do produto para uma pasta chamada para o bootstrapper personalizado. O arquivo de manifesto de pacote vai para uma pasta chamada para a localidade. Por exemplo, se o arquivo de manifesto de pacote for para redistribuição em inglês, coloque o arquivo em uma pasta chamada en. Repita esse processo para cada localidade, como ja para japonês e de para alemão. O pacote final de bootstrapper personalizado pode ter a seguinte estrutura de pasta.  
  
 `CustomBootstrapperPackage`  
  
 `product.xml`  
  
 `CustomBootstrapper.msi`  
  
 `de`  
  
 `eula.rtf`  
  
 `package.xml`  
  
 `en`  
  
 `eula.rtf`  
  
 `package.xml`  
  
 `ja`  
  
 `eula.rtf`  
  
 `package.xml`  
  
 Por fim, copie os arquivos redistribuíveis para o local de pasta do bootstrapper. Para obter mais informações, consulte [Como criar um pacote de bootstrapper localizado](../deployment/how-to-create-a-localized-bootstrapper-package.md).  
  
```  
\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 ou  
  
```  
\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 Você também pode determinar o local da pasta do bootstrapper de **caminho** valor na seguinte chave do registro:  
  
```  
HKLM\Software\Microsoft\GenericBootstrapper\11.0  
```  
  
 Em sistemas de 64 bits, use a seguinte chave do registro:  
  
```  
HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0  
```  
  
 Cada componente redistribuível aparece em sua própria subpasta no diretório de pacotes. O produto arquivos redistribuíveis e manifestos serão colocados nessa subpasta. Versões localizadas dos manifestos do componente e pacote são colocadas em subpastas nomeadas de acordo com o nome da cultura.  
  
 Depois que esses arquivos são copiados na pasta do bootstrapper, o pacote de bootstrapper aparece automaticamente na caixa de diálogo pré\-requisitos do Visual Studio. Se o pacote de bootstrapper personalizado não for exibido, feche e reabra a caixa de diálogo de pré\-requisitos. Para obter mais informações, consulte [Caixa de diálogo Pré\-requisitos](../ide/reference/prerequisites-dialog-box.md).  
  
 A tabela a seguir mostra as propriedades que são preenchidas automaticamente pelo bootstrapper.  
  
|Propriedade|Descrição|  
|-----------------|---------------|  
|ApplicationName|O nome do aplicativo.|  
|ProcessorArchitecture|O processador e bits por palavra da plataforma de destino por um executável. Os valores incluem o seguinte:<br /><br /> -   Intel<br />-   IA64<br />-   AMD64|  
|[Version9x](https://msdn.microsoft.com/en-us/library/aa372490\(v=vs.140\).aspx)|O número de versão para os sistemas operacionais Microsoft Windows 95, Windows 98 ou Windows ME. A sintaxe da versão é Major.Minor.ServicePack.|  
|[VersionNT](https://msdn.microsoft.com/en-us/library/aa372495\(v=vs.140\).xaspx)|O número de versão para os sistemas operacionais Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 ou Windows 7. A sintaxe da versão é Major.Minor.ServicePack.|  
|[VersionMSI](https://msdn.microsoft.com/en-us/library/aa372493\(v=vs.140\).aspx)|Execute a versão do assembly do Windows Installer \(MSI\) durante a instalação.|  
|[AdminUser](https://msdn.microsoft.com/en-us/library/aa367545\(v=vs.140\).aspx)|Essa propriedade é definida se o usuário tem privilégios de administrador. Os valores são true ou false.|  
|InstallMode|O modo de instalação indica onde o componente precisa ser instalado do. Os valores incluem o seguinte:<br /><br /> -   HomeSite \- instalação dos pré\-requisitos do site do fornecedor.<br />-   SpecificSite \- pré\-requisitos estão instalados no local selecionado.<br />-   SameSite \- pré\-requisitos estão instalados no mesmo local que o aplicativo.|  
  
## Separando redistribuíveis das instalações do aplicativo  
 Você pode impedir que os arquivos redistribuíveis sendo implantado em projetos de instalação. Para fazer isso, crie uma lista redistribuível na pasta RedistList em seu diretório do .NET Framework:  
  
 `%ProgramFiles%\Microsoft.NET\RedistList`  
  
 A lista redistribuível é um arquivo XML que você deve nomear usando o seguinte formato: *nome da empresa*.*Nome do componente*. Redistlist. Assim, por exemplo, se o componente é chamado de Datawidgets feito por Acme, use datawidgets. Um exemplo de conteúdo da lista redistribuível pode ter esta aparência:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<FileList Redist="Acme.DataWidgets" >  
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />  
</FileList>  
```  
  
## Consulte também  
 [Como instalar pré\-requisitos com um aplicativo ClickOnce](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [Caixa de diálogo Pré\-requisitos](../ide/reference/prerequisites-dialog-box.md)   
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)   
 [Usar o Visual Studio 2005 Bootstrapper para iniciar sua instalação](http://go.microsoft.com/fwlink/?LinkId=107537)