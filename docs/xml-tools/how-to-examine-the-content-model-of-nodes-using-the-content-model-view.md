---
title: "How to: Examine the Content Model of Nodes Using the Content Model View | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Examine the Content Model of Nodes Using the Content Model View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico descreve como explorar os nós usando [Content Model View](../xml-tools/content-model-view.md).  
  
### Para criar um novo arquivo XSD e exibir o elemento raiz no modo do modelo de conteúdo  
  
1.  Crie um novo arquivo de esquema XML.  
  
2.  Clique **Use o editor XML para exibir e editar o arquivo subjacente de esquema XML** no modo de Início.  
  
3.  Copie o código de exemplo de esquema XML [Esquema XML de exemplo: Esquema de ordem de compra](../Topic/Sample%20XSD%20File:%20Purchase%20Order%20Schema.md) e cole\-o para substituir o código que foi adicionado ao novo arquivo XSD por padrão.  
  
4.  Selecione o elemento de `purchaseOrder` no esquema De clique com o botão direito do mouse no elemento de `purchaseOrder` no editor XML e selecionando **Mostrar em XML Explorer**.  
  
5.  Clique com o botão direito do mouse em `purchaseOrder` XML Explorer e selecione **Mostrar no modo do modelo de conteúdo**.  
  
     A exibição do modelo de conteúdo exibe o elemento de `purchaseOrder` na superfície de design.  
  
6.  Expanda `shipTo`, `billTo`, e nós de `items` clicando duas vezes em cada nó ou double clicando na seta à direita de cada nó.  
  
     Os nós de elemento de `purchaseOrder` são expandidos e agora você pode ver o modelo de conteúdo do elemento.  
  
7.  Clique em qualquer nó no elemento de `purchaseOrder` e examine a barra de rastreamento para ver onde o esquema define o nó selecionado for encontrado.  
  
8.  Clique no botão de **Mostrar a documentação** na barra de ferramentas XSD para ativar \/desativar o documenation.  Você também pode clicar com o botão direito do mouse na superfície de design para ativar \/desativar a documentação.  
  
9. Rick\- clique no nó de `purchaseOrder` e selecione **Gerencia o exemplo XML** para ver o documento de instância XML.