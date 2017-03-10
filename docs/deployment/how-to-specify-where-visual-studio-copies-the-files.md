---
title: "Como especificar onde o Visual Studio copiar&#225; os arquivos | Microsoft Docs"
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
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "propriedade Local de Publicação"
  - "publicando, especificando local"
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como especificar onde o Visual Studio copiar&#225; os arquivos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando você publicar um aplicativo usando o ClickOnce, os `Publish Location` propriedade especifica o local onde os arquivos de aplicativo e manifesto são colocados.  Isso pode ser um caminho de arquivo ou o caminho para um servidor FTP.  
  
 Você pode especificar o `Publish Location` propriedade o **publicar** página do **Project Designer**, ou usando o Assistente de publicação.  Para obter mais informações, consulte [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md).  
  
> [!NOTE]
>  Ao instalar mais de uma versão de um aplicativo usando o ClickOnce, a instalação moverá as versões anteriores do aplicativo para uma pasta chamada Arquivo, no local de publicação especificado.  O arquivamento de versões anteriores dessa maneira mantém o diretório de instalação livre de pastas da versão anterior.  
  
### Para especificar um local de publicação  
  
1.  Com um projeto selecionado no **Solution Explorer**, diante do **projeto** menu, clique em **propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  No **local de publicação** insira o local de publicação usando um dos seguintes formatos:  
  
    -   Para publicar em um caminho de disco ou compartilhamento de arquivo, insira o caminho usando um caminho UNC \(\\\\Server\\ApplicationName\) ou um caminho de arquivo \(C:\\Deploy\\ApplicationName\).  
  
    -   Para publicar em um servidor FTP, digite o caminho usando o formato ftp:\/\/ftp.microsoft.com\/ApplicationName.  
  
     Observe que o texto deve estar presente no **local de publicação** caixa para que o botão Procurar \(**...**\) botão trabalhar.  
  
## Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)