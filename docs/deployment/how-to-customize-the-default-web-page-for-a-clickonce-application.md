---
title: "Como personalizar a p&#225;gina da Web padr&#227;o para um aplicativo ClickOnce | Microsoft Docs"
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
  - "página da Web Publish.htm"
  - "página da Web padrão da implantação ClickOnce"
  - "Implantando aplicativos ClickOnce, publicando"
  - "publicação do ClickOnce"
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como personalizar a p&#225;gina da Web padr&#227;o para um aplicativo ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para publicar um aplicativo ClickOnce a Web, uma página da Web é automaticamente gerada e publicado com o aplicativo.  A página padrão contém o nome do aplicativo e link para instalar o aplicativo, para instalar pré\-requisitos, ou para acessar a ajuda no MSDN.  
  
> [!NOTE]
>  Links reais que você vê na página depende do computador onde a página está sendo exibida e quais pré\-requisitos que você está incluindo.  
  
 O nome padrão para a página da Web é Publish.htm; você pode alterar o nome em **Designer de Projeto**.  Para obter mais informações, consulte [Como especificar uma página de publicação para um aplicativo ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 A página Publish.htm é publicado somente se uma versão mais recente é detectada.  
  
> [!NOTE]
>  Alterações feitas ao seu **Publicar** configurações não afetará a página Publish.htm, com uma exceção: se você adicionar ou remover após publicar pré\-requisitos inicialmente, a lista de pré\-requisitos não será exata.  Você precisará editar o texto do link necessário para refletir as alterações.  
  
### Para personalizar a página da Web publicado  
  
1.  Publicar seu aplicativo ClickOnce para um local da Web.  Para obter mais informações, consulte [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md).  
  
2.  Em o servidor Web, abra o arquivo Publish.htm no visual Web designer ou em outro editor HTML.  
  
3.  Personalizar a página conforme desejado e salvar a.  
  
4.  Opcional.  Para impedir que o Visual Studio substitua seu personalizado para publicar a página da Web, desmarque **Gerar automaticamente a Web após a implantação inicial de cada publicação** na caixa de diálogo opções de publicação.  
  
## Consulte também  
 [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como instalar pré\-requisitos com um aplicativo ClickOnce](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [Como especificar uma página de publicação para um aplicativo ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)