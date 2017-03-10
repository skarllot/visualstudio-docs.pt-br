---
title: "Como incrementar a vers&#227;o da publica&#231;&#227;o do ClickOnce automaticamente | Microsoft Docs"
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
  - "implantação ClickOnce, incrementando a versão de publicação automaticamente"
  - "implantando aplicativos [ClickOnce], incrementando a versão de publicação automaticamente"
  - "propriedade Versão da Publicação, incrementando"
  - "publicando, ClickOnce"
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como incrementar a vers&#227;o da publica&#231;&#227;o do ClickOnce automaticamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ao publicar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo, alterando a `Publish Version` propriedade faz com que o aplicativo a ser publicado como uma atualização.  Por padrão, o Visual Studio incrementa automaticamente o `Revision` número da `Publish Version` cada vez que você publica o aplicativo.  
  
 Você pode desativar esse comportamento na  **Publicar** página da  **Project Designer**.  
  
> [!NOTE]
>  As caixas de diálogo e comandos de menu demonstradas podem ser diferentes daqueles descritos na Ajuda, dependendo das configurações ativas ou configurações de edição.  Para alterar as configurações, escolha  **Import and Export Settings** sobre o  **Ferramentas** menu.  Para obter mais informações, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Para desativar incrementando automaticamente a versão de publicação  
  
1.  Com um projeto selecionado no **Solution Explorer**, no menu **Project**, clique em **Properties**.  
  
2.  Clique na guia **Publish**.  
  
3.  No  **Publish Version** seção, limpar o  **incrementar automaticamente a revisão com cada versão** caixa de seleção.  
  
## Consulte também  
 [Como definir a versão da publicação do ClickOnce](../Topic/How%20to:%20Set%20the%20ClickOnce%20Publish%20Version.md)   
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)