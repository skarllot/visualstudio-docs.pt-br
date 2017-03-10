---
title: "Vari&#225;vel local n&#227;o utilizada: &#39;&lt; localvariablename &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42024"
  - "BC42024"
helpviewer_keywords: 
  - "BC42024"
ms.assetid: 749b1315-0f85-4f7e-b68b-8cc4346c502b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vari&#225;vel local n&#227;o utilizada: &#39;&lt; localvariablename &gt;&#39;
Uma variável local em um procedimento está declarada mas nunca foi usada.  
  
 Uma possibilidade é que há um erro de ortografia entre as variáveis locais no procedimento. Se essa variável é na verdade usada em outra declaração mas digitada de maneira diferente, ele aparecerá ao compilador duas variáveis diferentes.  
  
 Por padrão, essa mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC42024  
  
### Para corrigir este erro  
  
1.  Verifique se há erros de ortografia entre as variáveis locais dentro do procedimento. Observe que maiúsculas e minúsculas não fazem diferença. Os nomes de `ABC` e `abc` são considerados para se referir à mesma variável.  
  
2.  Se não houver nenhum erro de ortografia, remova a declaração da variável ou usá\-lo em outra instrução no procedimento.  
  
## Consulte também  
 [Nomes de elemento declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)   
 [Instrução Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)