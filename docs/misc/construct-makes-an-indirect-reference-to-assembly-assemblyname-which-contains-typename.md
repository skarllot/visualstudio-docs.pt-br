---
title: "Constru&#231;&#227;o faz uma refer&#234;ncia indireta ao assembly &#39;&lt; assemblyname &gt;&#39;, que cont&#233;m &#39;&lt; typename &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31528"
  - "vbc31528"
helpviewer_keywords: 
  - "BC31528"
ms.assetid: 33459c3f-8615-492e-b6ae-531ed597999e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Constru&#231;&#227;o faz uma refer&#234;ncia indireta ao assembly &#39;&lt; assemblyname &gt;&#39;, que cont&#233;m &#39;&lt; typename &gt;&#39;
Construção faz uma referência indireta ao assembly '\< assemblyname \>', que contém \< typename \>. Adicione uma referência de arquivo para \< filename \> ao seu projeto.  
  
 Uma expressão usa um tipo, como uma classe, estrutura, interface, enumeração ou delegado, mas o assembly não tem uma referência ao assembly que define o tipo de projeto.  
  
 **ID do erro:** BC31528  
  
### Para corrigir este erro  
  
-   Nas propriedades do projeto, adicione uma referência para o arquivo que contém o assembly que define o tipo que você está usando.  
  
## Consulte também  
 [NOTINBUILD: Resolvendo uma referência quando várias variáveis têm o mesmo nome](http://msdn.microsoft.com/pt-br/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [PONTA como: modificar propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [PONTA como: Adicionar ou remover referências usando a caixa de diálogo Adicionar referência](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)