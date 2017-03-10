---
title: "&#39;#End ExternalSource&#39; deve ser precedido por um #ExternalSource&#39; | Microsoft Docs"
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
  - "bc30578"
  - "vbc30578"
helpviewer_keywords: 
  - "BC30578"
ms.assetid: f011673d-eced-46a7-a08e-d54d86c8a76b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#End ExternalSource&#39; deve ser precedido por um #ExternalSource&#39;
A `#ExternalSource` diretivas referências código externo, possibilitando ao compilador informar, com acurácia, quando exceções ocorrerem dentro daquele código. Um `#ExternalSource` bloco deve começar com `#ExternalSource` e terminar com `#End ExternalSource`.  
  
 **ID do erro:** BC30578  
  
### Para corrigir este erro  
  
1.  Adicionar `#ExternalSource` para o local apropriado em seu código.  
  
2.  Remover `#End ExternalSource` se não for necessário.  
  
## Consulte também  
 [Diretiva \#ExternalSource](/dotnet/visual-basic/language-reference/directives/externalsource-directive)   
 [Compilação condicional NOTINBUILD \(Visual Basic\)](http://msdn.microsoft.com/pt-br/ad1e35e0-935e-4a35-a2ae-738bcf2a9240)