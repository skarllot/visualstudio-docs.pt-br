---
title: "&#39;#ExternalSource&#39; deve finalizar com &#39;#End ExternalSource&#39; correspondente | Microsoft Docs"
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
  - "vbc30579"
  - "bc30579"
helpviewer_keywords: 
  - "BC30579"
ms.assetid: 8d658008-eddc-4b7d-a8d4-036da42957bf
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#ExternalSource&#39; deve finalizar com &#39;#End ExternalSource&#39; correspondente
A `#ExternalSource` diretivas referências código externo, possibilitando ao compilador informar, com acurácia, quando exceções ocorrerem dentro daquele código. Um `#ExternalSource` bloco deve começar com `#ExternalSource` e terminar com `#End ExternalSource`.  
  
 **ID do erro:** BC30579  
  
### Para corrigir este erro  
  
1.  Adicionar `#End ExternalSource` para o local apropriado em seu código.  
  
2.  Remover inicial `#ExternalSource` se não for necessário.  
  
## Consulte também  
 [Diretiva \#ExternalSource](/dotnet/visual-basic/language-reference/directives/externalsource-directive)   
 [Compilação condicional NOTINBUILD \(Visual Basic\)](http://msdn.microsoft.com/pt-br/ad1e35e0-935e-4a35-a2ae-738bcf2a9240)