---
title: "Como especificar o modo de instala&#231;&#227;o offline ou online do ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "implantação ClickOnce, especificando o modo de instalação"
  - "modo de instalação ClickOnce"
  - "modo de instalação"
  - "aplicativos offline"
  - "aplicativos online"
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como especificar o modo de instala&#231;&#227;o offline ou online do ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O `Install Mode` para um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo determina se o aplicativo será disponível off\-line ou on\-line.  Quando você escolhe  **o aplicativo está disponível apenas online**, o usuário deve ter acesso para o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] local \(uma página da Web ou um compartilhamento de arquivo\) para executar o aplicativo de publicação.  Quando você escolhe  **o aplicativo está disponível também offline**, o aplicativo adiciona entradas para o  **Iniciar** menu e o  **Adicionar ou remover programas** caixa de diálogo. o usuário é capaz de executar o aplicativo quando não estão conectados.  
  
 O `Install Mode` pode ser definido na  **Publicar** página da  **Project Designer**.  
  
 **Nota** a `Install Mode` também podem ser definidas usando o Assistente de publicação.  Para obter mais informações, consulte [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md).  
  
### Para disponibilizar um aplicativo de ClickOnce on\-line somente  
  
1.  Com um projeto selecionado no **Solution Explorer**, no menu **Project**, clique em **Properties**.  
  
2.  Clique na guia **Publish**.  
  
3.  No  **modo de instalação e configurações de** área, clique no  **o aplicativo está disponível apenas online** o botão de opção.  
  
### Para disponibilizar um aplicativo de ClickOnce on\-line ou off\-line  
  
1.  Com um projeto selecionado no **Solution Explorer**, no menu **Project**, clique em **Properties**.  
  
2.  Clique na guia **Publish**.  
  
3.  No  **modo de instalação e configurações de** área, clique no  **o aplicativo está disponível também offline** o botão de opção.  
  
     Quando instalado, o aplicativo adiciona entradas para o  **Iniciar** menu e obtenha o  **Adicionar ou remover programas** no painel de controle.  
  
## Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)   
 [Escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)