---
title: "Membro &#39;&lt; nome do membro &gt;&#39; define implicitamente um membro &#39;&lt; implicitmembername &gt;&#39; que tem o mesmo nome que um par&#226;metro de tipo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC32070"
  - "vbc32070"
helpviewer_keywords: 
  - "BC32070"
ms.assetid: cc0b3fcf-c141-47e2-9b33-d2b91c8bf2d6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Membro &#39;&lt; nome do membro &gt;&#39; define implicitamente um membro &#39;&lt; implicitmembername &gt;&#39; que tem o mesmo nome que um par&#226;metro de tipo
Um membro de uma classe genérica gera um membro implícito com o mesmo nome que um parâmetro de tipo para a classe.  
  
 O [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador cria membros implícitos correspondentes a certos elementos de programação que você declarar. A tabela a seguir resume esses implícita ou *sintética*, membros.  
  
|Elementos declarados|Membros criados implicitamente|  
|--------------------------|------------------------------------|  
|Enumeração|`value__` membro|  
|Evento|`add_<eventname>` procedimento<br /><br /> `remove_<eventname>` procedimento<br /><br /> `<eventname>Event` campo<br /><br /> `<eventname>EventHandler` Delegar|  
|Propriedade|`get_<propertyname>` procedimento<br /><br /> `set_<propertyname>` procedimento|  
|`My.` variável de coleção|`m_<variablename>` `Static` variável<br /><br /> `<variablename>` propriedade<br /><br /> `get_<variablename>` procedimento<br /><br /> `set_<variablename>` procedimento|  
|`WithEvents` variável|`_<variablename>` variável<br /><br /> `<variablename>` propriedade<br /><br /> `get_<variablename>` procedimento<br /><br /> `set_<variablename>` procedimento|  
  
 Devido à possibilidade de conflitos de nome, você deve evitar qualquer elemento de programação declarado usando a mesma forma como qualquer um desses membros implícitos de nomenclatura. Por exemplo, você deve evitar qualquer elemento nome que começa com `get_` ou `set_`.  
  
 **ID do erro:** BC32070  
  
### Para corrigir este erro  
  
-   Se o nome do parâmetro de tipo é flexível, alterá\-la para evitar conflitos com os nomes listados na tabela anterior.  
  
-   Se o parâmetro de tipo deve manter seu nome, altere o nome do membro da classe para evitar conflitos com os nomes listados na tabela anterior.  
  
## Consulte também  
 [Nomes de elemento declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)