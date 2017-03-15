---
title: "Refer&#234;ncia indireta est&#225; sendo feita a vers&#227;o do assembly &lt; assemblyname &gt; &lt; laterversionnumber &gt;, que cont&#233;m &#39;&lt; typename &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32207"
  - "bc32207"
helpviewer_keywords: 
  - "BC32207"
ms.assetid: a3de74b5-bedd-4e36-b379-485e4b3903f7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Refer&#234;ncia indireta est&#225; sendo feita a vers&#227;o do assembly &lt; assemblyname &gt; &lt; laterversionnumber &gt;, que cont&#233;m &#39;&lt; typename &gt;&#39;
Referência indireta está sendo feita a versão do assembly \< assemblyname \> \< laterversionnumber \>, que contém '\< typename \>'. Este projeto referencia uma versão anterior da versão \< assemblyname \> \< earlierversionnumber \>. Para usar '\< typename \>', você deve substituir a referência ao \< assemblyname \> versão \< laterversionnumber \> ou superior.  
  
 Uma expressão faz uma referência indireta a outro projeto, que tem uma referência para uma versão anterior do mesmo assembly.  
  
 Normalmente, você deve usar somente a versão mais recente de um assembly.  
  
 **ID do erro:** BC32207  
  
### Para corrigir este erro  
  
1.  Use o nome do tipo citado para determinar qual projeto também referencia o mesmo assembly.  
  
2.  Determinar qual versão do assembly referências do projeto e altere seu projeto para fazer referência a mesma versão.  
  
## Consulte também  
 [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md)   
 [PONTA como: Adicionar ou remover referências usando a caixa de diálogo Adicionar referência](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Solucionando Problemas de Referências Quebradas](../ide/troubleshooting-broken-references.md)