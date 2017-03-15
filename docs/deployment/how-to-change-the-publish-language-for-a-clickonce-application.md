---
title: "Como alterar o idioma de publica&#231;&#227;o para um aplicativo ClickOnce | Microsoft Docs"
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
  - "implantação ClickOnce, alterando a linguagem de publicação"
  - "propriedade Linguagem de publicação"
  - "publicando, ClickOnce"
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como alterar o idioma de publica&#231;&#227;o para um aplicativo ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ao publicar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo, a interface do usuário exibida durante a instalação padrão é o idioma e cultura do seu computador de desenvolvimento.  Se você estiver publicando um aplicativo localizado, você precisará especificar um idioma e cultura para coincidir com a versão localizada.  Isso é determinado pelo `Publish language` propriedade para o seu projeto.  
  
 O `Publish language` propriedade pode ser definida  **Opções de publicação do** caixa de diálogo, acessível a partir o  **Publicar** página da  **Project Designer**.  
  
> [!NOTE]
>  As caixas de diálogo e comandos de menu demonstradas podem ser diferentes daqueles descritos na Ajuda, dependendo das configurações ativas ou configurações de edição.  Para alterar as configurações, escolha  **Import and Export Settings** sobre o  **Ferramentas** menu.  Para obter mais informações, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Para alterar o idioma da publicação  
  
1.  Com um projeto selecionado no **Solution Explorer**, no menu **Project**, clique em **Properties**.  
  
2.  Clique na guia **Publish**.  
  
3.  Clique no  **Opções** botão para abrir o  **Opções de publicação do** caixa de diálogo.  
  
4.  Clique em  **Descrição**.  
  
5.  No  **Opções de publicação do** diálogo Selecione um idioma e cultura da  **Publicar idioma** na lista suspensa e clique  **OK**.  
  
## Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)