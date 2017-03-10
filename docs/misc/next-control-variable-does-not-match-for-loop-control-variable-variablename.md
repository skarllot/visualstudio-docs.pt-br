---
title: "Vari&#225;vel de controle Next n&#227;o corresponde a vari&#225;vel de controle de loop &#39;&lt; variablename &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30070"
  - "bc30070"
helpviewer_keywords: 
  - "BC30070"
ms.assetid: e9e96008-b053-4fa0-8966-decaad99fecd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vari&#225;vel de controle Next n&#227;o corresponde a vari&#225;vel de controle de loop &#39;&lt; variablename &gt;&#39;
A variável de controle no `Next` declaração de um `For...Next` loop deve coincidir com a variável no correspondente `For` instrução.  
  
 **ID do erro:** BC30070  
  
### Para corrigir este erro  
  
1.  Verifique a ortografia da variável no `Next` instrução in correspondente e `For` instrução para garantir que ela corresponde.  
  
2.  Certifique\-se de que nenhuma parte do loop delimitador foi excluído inadvertidamente.  
  
3.  Se este loop for parte de um conjunto de loops aninhados, verifique cada loop é encerrado corretamente.  
  
## Consulte também  
 [Instrução For...Next](/dotnet/visual-basic/language-reference/statements/for-next-statement)