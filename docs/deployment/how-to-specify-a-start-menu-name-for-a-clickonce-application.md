---
title: "Como especificar um nome no menu Iniciar para um aplicativo ClickOnce | Microsoft Docs"
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
  - "implantação ClickOnce, nome do menu Iniciar"
  - "nome do menu Iniciar"
  - "nome do recurso do menu Iniciar"
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como especificar um nome no menu Iniciar para um aplicativo ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo é instalado para uso online e offline, é adicionada uma entrada para o  **Iniciar** menu e o  **Adicionar ou remover programas** lista.  Por padrão, o nome de exibição é o mesmo que o nome do assembly do aplicativo, mas você pode alterar o nome de exibição, definindo  **nome do produto** na  **Opções de publicação do** caixa de diálogo.  
  
 **Nome do produto** será exibido na página Publish; para um aplicativo off\-line instalado, ele será o nome da entrada na  **Iniciar** menu e ele também será o nome que aparece em  **Adicionar ou remover programas**.  
  
 **Nome do Editor** será exibido na página Publish acima  **nome do produto**, e para um aplicativo off\-line instalado, ele também será o nome da pasta que contém o ícone do aplicativo no  **Iniciar** menu.  
  
 Você pode definir o  **nome do produto** e  **nome do Editor** propriedades na  **Opções de publicação do** caixa de diálogo, disponível no  **Publicar** página da  **Project Designer**.  
  
### Para especificar um nome de menu Iniciar  
  
1.  Com um projeto selecionado no **Solution Explorer**, no menu **Project**, clique em **Properties**.  
  
2.  Clique na guia **Publish**.  
  
3.  Clique no  **Opções** botão para abrir o  **Opções de publicação do** caixa de diálogo.  
  
4.  Clique em  **Descrição**.  
  
5.  No  **Opções de publicação do** caixa de diálogo, digite o nome para exibir em  **nome do produto**.  
  
6.  Opcionalmente, você pode digitar um nome de editor em  **nome do Editor**.  
  
## Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)