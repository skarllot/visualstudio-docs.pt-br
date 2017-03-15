---
title: "Acessadores de propriedade n&#227;o podem ser declarados &#39;&lt; accessmodifier &gt;&#39; em uma propriedade &#39;Default&#39; | Microsoft Docs"
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
  - "bc31107"
  - "vbc31107"
helpviewer_keywords: 
  - "BC31107"
ms.assetid: 25657b33-df85-4535-8043-69795c987175
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Acessadores de propriedade n&#227;o podem ser declarados &#39;&lt; accessmodifier &gt;&#39; em uma propriedade &#39;Default&#39;
Um [Instrução Get](/dotnet/visual-basic/language-reference/statements/get-statement) ou [Instrução Set](/dotnet/visual-basic/language-reference/statements/set-statement) em um padrão propriedade inclui o `Private` palavra\-chave.  
  
 Uma propriedade padrão não pode ser `Private`, e nem seus procedimentos de propriedade individual podem \(`Get` ou `Set`\).  
  
 **ID do erro:** BC31107  
  
### Para corrigir este erro  
  
-   Remover o `Private` palavra\-chave from a `Get` ou `Set` instrução ou remover `Default` do [Instrução Property](/dotnet/visual-basic/language-reference/statements/property-statement).  
  
## Consulte também  
 [Procedimentos de propriedade](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Como declarar uma propriedade com níveis de acesso mistos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)   
 [Como declarar e chamar uma propriedade padrão no Visual Basic](../Topic/How%20to:%20Declare%20and%20Call%20a%20Default%20Property%20in%20Visual%20Basic.md)