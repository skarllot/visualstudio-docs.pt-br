---
title: "Falha na resolu&#231;&#227;o de sobrecarga porque nenhum acess&#237;vel &#39;&lt; genericprocedurename &gt;&#39; aceita este n&#250;mero de argumentos de tipo | Microsoft Docs"
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
  - "bc32087"
  - "vbc32087"
helpviewer_keywords: 
  - "BC32087"
ms.assetid: a3eaafd3-80f6-4b7d-9b75-47b043fe17b5
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Falha na resolu&#231;&#227;o de sobrecarga porque nenhum acess&#237;vel &#39;&lt; genericprocedurename &gt;&#39; aceita este n&#250;mero de argumentos de tipo
Uma chamada para um procedimento genérico sobrecarregado não pode ser resolvida porque o compilador não pode acessar qualquer versão sobrecarregada com o número apropriado de parâmetros de tipo.  
  
 Quando você chama um procedimento genérico, você deve fornecer um argumento de tipo para cada parâmetro de tipo. Como alternativa, você pode fornecer nenhum tipo em todos os argumentos e permitir que o compilador tente fazer *inferência de tipo*. Para obter mais informações, consulte "Inferência de tipo" em [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 **ID do erro:** BC32087  
  
### Para corrigir este erro  
  
1.  Certifique\-se de que a versão que você pretende chamar está acessível pelo código de chamada. Consulte [Níveis de acesso no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels).  
  
2.  Adicione ou remova argumentos de tipo do seu código de chamada para que a lista de argumentos de tipo corresponde à lista de parâmetros de tipo da versão que você pretende chamar.  
  
     \- ou \-  
  
     Remova todos os argumentos de tipo do seu código de chamada e deixar que o compilador tenta inferência de tipo. Lembre\-se de que a inferência de tipos pode falhar se houver conflitos ou ambigüidades.  
  
## Consulte também  
 [Propriedades e métodos sobrecarregados](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods)   
 [Resolução de sobrecarga](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)