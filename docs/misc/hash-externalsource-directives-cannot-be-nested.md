---
title: "Diretivas de &#39;#ExternalSource&#39; n&#227;o podem ser aninhadas | Microsoft Docs"
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
  - "bc30580"
  - "vbc30580"
helpviewer_keywords: 
  - "BC30580"
ms.assetid: 56c6ef4b-28b1-4a62-8afa-d83a7742b507
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Diretivas de &#39;#ExternalSource&#39; n&#227;o podem ser aninhadas
Você tentou colocar um `#ExternalSource` diretiva dentro de outra `#ExternalSource` bloco. A `#ExternalSource` diretivas referências código externo, possibilitando ao compilador informar, com acurácia, quando exceções ocorrerem dentro daquele código.  
  
 `#ExternalSource` blocos não podem ser aninhados em outros `#ExternalSource` blocos.  
  
 **ID do erro:** BC30580  
  
### Para corrigir este erro  
  
-   Mover interno `#ExternalSource` diretiva fora de circunscrição `#ExternalSource` bloco.  
  
## Consulte também  
 [Diretiva \#ExternalSource](/dotnet/visual-basic/language-reference/directives/externalsource-directive)   
 [Compilação condicional NOTINBUILD \(Visual Basic\)](http://msdn.microsoft.com/pt-br/ad1e35e0-935e-4a35-a2ae-738bcf2a9240)