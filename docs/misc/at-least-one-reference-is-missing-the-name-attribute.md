---
title: "Pelo menos uma refer&#234;ncia est&#225; com o atributo &#39;Nome&#39; faltando | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.refmissingname"
ms.assetid: 0703dc20-9cdd-4632-93a0-57a4ccea2fce
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Pelo menos uma refer&#234;ncia est&#225; com o atributo &#39;Nome&#39; faltando
Cada referência deve ter um tipo de  **nome** propriedade, como visto abaixo:  
  
```  
<Reference  
   Name = "System.XML"  
   AssemblyName = "System.Xml"  
/>  
```  
  
 Este erro indica que o  **nome** propriedade não foi encontrada para pelo menos uma referência.  
  
 Este erro é provavelmente causado editando manualmente o arquivo de projeto.  
  
 **Para corrigir este erro**  
  
-   Adicione referência novamente.  
  
     Quaisquer referências afetadas não serão adicionadas ao projeto.  
  
## Consulte também  
 [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md)