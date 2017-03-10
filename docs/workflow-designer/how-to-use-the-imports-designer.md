---
title: "How to: Use the Imports Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.View.ImportDesigner.UI"
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# How to: Use the Imports Designer
O designer imports permite que você inserir em namespaces para os tipos que você usará em suas expressões.  Bem como as palavras\-chave de **Imports** ou de **using** no Visual Basic. NET e C\#, especificando namespaces no designer imports permite que você digite simplesmente um nome de tipo na sua expressão em vez de um nome de tipo totalmente qualificado de versão.  
  
 O designer imports reage a alterações na interface do usuário e as alterações feitas quando o fluxo de trabalho é salvo.  Quando o fluxo de trabalho é salvo, namespaces podem ser adicionados automaticamente ao designer imports.  Eles incluem o seguinte:  
  
-   Namespaces para alguns tipos usados em declarações de variável e argumento.  
  
-   Namespaces para alguns tipos usados em expressões.  
  
-   Algumas outras namespaces necessárias para serializar o fluxo de trabalho \(por exemplo, namespaces usadas por atividades personalizados soltas no fluxo de trabalho\).  
  
 Quando o fluxo de trabalho é salvo, você pode notar que algumas namespaces que você excluiu manualmente que são adicionados automaticamente ao designer imports devido à lógica descrita na lista anterior.  
  
### Para adicionar um namespace à lista de namespaces importados  
  
1.  Abra um aplicativo de serviço do fluxo de trabalho WCF, um aplicativo de console de fluxo de trabalho, ou um projeto de biblioteca de atividade em [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] ou em um aplicativo de fluxo de trabalho rehosted.  
  
2.  Clique **Importações** na parte inferior de tela principal.  O designer imports aparecerá.  
  
3.  Insira ou selecione em um namespace do controle de lista suspensa na parte superior do designer imports.  
  
     Enquanto você digita, uma lista de namespaces válidas que correspondem aos caracteres tipados aparece.  
  
4.  Pressione **Enter** para adicionar um namespace à lista.  
  
5.  Se você deseja remover um namespace da lista, selecione o namespace e pressione a tecla de **Excluir** no teclado.  Observe que um namespace só pode ser excluída se o namespace não é válido por algum motivo, por exemplo se o assembly que contém o namespace não é referenciado pelo projeto.