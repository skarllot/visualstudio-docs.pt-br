---
title: "Argumento est&#225; ausente em &#39;-&#39; seq&#252;&#234;ncia de escape. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_RE_ESCAPEMISSINGARG"
  - "vs.message.0x800A00BD"
ms.assetid: 5bd6559b-8cd9-450f-91c8-335ff1b1ef86
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Argumento ausente na sequ&#234;ncia de escape &#39;\&#39;.
Esse erro geralmente ocorre durante a pesquisa ou substituir quando caracteres curingas ou expressões regulares são usados em uma cadeia de caracteres de pesquisa. Esse erro pode ser causado por uma barra invertida \(`\`\) no final de um padrão ou por `\x` ou `\u` inserido sem um caractere Unicode hexadecimal válido.  
  
### Para corrigir este erro  
  
1.  Para pesquisar usando o caractere de escape de expressão regular, digite `\`.  
  
2.  Para pesquisar um caractere Unicode, digite `\x` ou `\u` seguido de um valor Unicode válido.  
  
3.  Para procurar a barra invertida literal, use `\\`.  
  
## Consulte também  
 [Usando expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Localizar e substituir, localização rápida](http://msdn.microsoft.com/pt-br/dad03582-4931-4893-83ba-84b37f5b1600)   
 [Localizar nos arquivos](../ide/find-in-files.md)