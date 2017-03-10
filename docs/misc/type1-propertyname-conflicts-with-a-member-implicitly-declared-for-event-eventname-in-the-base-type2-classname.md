---
title: "&lt; type1 &gt; &#39;&lt; propertyname &gt;&#39; est&#225; em conflito com um membro implicitamente declarado para o evento &#39;&lt; eventname &gt;&#39; na base de &lt; type2 &gt; &#39;&lt; classname &gt;&#39; | Microsoft Docs"
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
  - "vbc40014"
  - "bc40014"
helpviewer_keywords: 
  - "BC40014"
ms.assetid: 100534b9-d533-4e94-a2a7-0ed26426965b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt; type1 &gt; &#39;&lt; propertyname &gt;&#39; est&#225; em conflito com um membro implicitamente declarado para o evento &#39;&lt; eventname &gt;&#39; na base de &lt; type2 &gt; &#39;&lt; classname &gt;&#39;
Uma propriedade é declarada com o mesmo nome como um membro implícito formado de um evento na classe base. Por exemplo, se a classe base define um evento chamado `Event1`, o compilador gera os procedimentos implícitos `add_Event1` e `remove_Event1`. Se a propriedade nessa classe tiver um desses nomes, ela deve sombrear o membro da classe base.  
  
 Essa mensagem é um aviso.`Shadows` será considerado por padrão. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC40014  
  
### Para corrigir este erro  
  
1.  Para ocultar o membro da classe base, adicione a `Shadows` palavra\-chave para a declaração de propriedade.  
  
2.  Se você não pretende ocultar o membro da classe base, altere o nome da propriedade.  
  
## Consulte também  
 [Instrução Property](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Instrução Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Sombras](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Sombreamento no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)