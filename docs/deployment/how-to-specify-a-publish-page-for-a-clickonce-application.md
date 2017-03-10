---
title: "Como especificar uma p&#225;gina de publica&#231;&#227;o para um aplicativo ClickOnce | Microsoft Docs"
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
  - "implantação ClickOnce, especificando página de publicação"
  - "implantando aplicativos [ClickOnce], especificando página de publicação"
  - "propriedade Página de Publicação"
  - "publicando, ClickOnce"
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como especificar uma p&#225;gina de publica&#231;&#227;o para um aplicativo ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ao publicar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo, uma página de Web padrão \(Publish\) é gerada e publicada junto com o aplicativo.  Esta página contém o nome do aplicativo, um link para instalar o aplicativo e\/ou algum pré\-requisito e um link para um tópico da Ajuda que descreve [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  O  **Publish Page** propriedade para o seu projeto permite que você especifique um nome para a página da Web para seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  
  
 Depois que a página da publicação tiver sido especificada, na próxima vez que você publica, ele será copiado para o local de publicação; ele não será substituído se você publicar novamente.  Se você quiser personalizar a aparência da página, você pode fazer isso sem se preocupar com a perda das alterações.  Para obter mais informações, consulte [Como personalizar a página da Web padrão do ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 O  **Publish Page** propriedade pode ser definida  **Opções de publicação do** caixa de diálogo, acessível a partir o  **Publicar** painel do  **Project Designer**.  
  
### Para especificar uma página da Web personalizada para um aplicativo de ClickOnce  
  
1.  Com um projeto selecionado no  **Solution Explorer**diante do  **projeto** menu do botão  **Propriedades**.  
  
2.  Selecione o  **Publicar** painel.  
  
3.  Clique no  **Opções** botão para abrir o  **Opções de publicação do** caixa de diálogo.  
  
4.  Clique em **Deployment**.  
  
5.  No  **Opções de publicação do** diálogo caixa, certifique\-se de que o  **publicar a página da web de implantação aberta após** caixa de seleção estiver marcada \(ele deve ser selecionado por padrão\).  
  
6.  No  **página da web de implantação:** caixa, digite o nome para sua página da Web e, em seguida, clique em  **OK**.  
  
### Para impedir que a página Publicar iniciando a cada vez que você publicar  
  
1.  Com um projeto selecionado no  **Solution Explorer**diante do  **projeto** menu do botão  **Propriedades**.  
  
2.  Selecione o  **Publicar** painel.  
  
3.  Clique no  **Opções** botão para abrir o  **Opções de publicação do** caixa de diálogo.  
  
4.  Clique em **Deployment**.  
  
5.  No  **Opções de publicação do** caixa de diálogo, limpar o  **publicar a página da web de implantação aberta após** caixa de seleção.  
  
## Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)   
 [Como personalizar a página da Web padrão do ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)