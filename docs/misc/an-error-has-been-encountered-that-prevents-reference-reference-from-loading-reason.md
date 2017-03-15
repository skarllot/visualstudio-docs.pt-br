---
title: "Foi encontrado um erro que impede o carregamento da refer&#234;ncia &#39;refer&#234;ncia&#39;. &lt; motivo &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.reference_load_error"
ms.assetid: 0e922611-197b-4607-bc31-03f80bd3e7e1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Foi encontrado um erro que impede o carregamento da refer&#234;ncia &#39;refer&#234;ncia&#39;. &lt; motivo &gt;
Foi encontrado um erro fatal durante a remoção de uma referência do arquivo de projeto. As causas desse erro são identificadas em \< motivo \> e pode ser:  
  
-   GUID malformada para obter uma referência. Isso é aplicável apenas referências de COM.  
  
-   Ferramenta do wrapper incorreta. Atualmente, a propriedade da ferramenta wrapper pode ser uma das tlbimp, aximp ou primário. Isso é aplicável apenas referências de COM.  
  
-   Cadeia de caracteres de referência de projeto inválido. Isso é aplicável somente a referências de projeto para projeto.  
  
 **Para corrigir este erro**  
  
-   Adicione a referência ao projeto para resolver esse erro.  
  
     Qualquer referência para o qual este diagnóstico é exibido não será carregada para o projeto.  
  
## Consulte também  
 [NIB: Propriedades de projeto \(Visual Studio\)](http://msdn.microsoft.com/pt-br/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)