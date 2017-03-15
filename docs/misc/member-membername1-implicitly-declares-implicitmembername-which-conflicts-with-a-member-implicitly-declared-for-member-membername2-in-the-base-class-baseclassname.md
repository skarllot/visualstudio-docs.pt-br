---
title: "Membro &#39;&lt; membername1 &gt;&#39; declara implicitamente &#39;&lt; implicitmembername &gt;&#39;, que est&#225; em conflito com um membro implicitamente declarado para membro &#39;&lt; membername2 &gt;&#39; na classe base &#39;&lt; baseclassname &gt;&#39; | Microsoft Docs"
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
  - "vbc40018"
  - "bc40018"
helpviewer_keywords: 
  - "BC40018"
ms.assetid: 43844e55-9ce1-4b88-9aa8-839b37f30e5a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Membro &#39;&lt; membername1 &gt;&#39; declara implicitamente &#39;&lt; implicitmembername &gt;&#39;, que est&#225; em conflito com um membro implicitamente declarado para membro &#39;&lt; membername2 &gt;&#39; na classe base &#39;&lt; baseclassname &gt;&#39;
Membro '\< membername1 \>' declara implicitamente '\< implicitmembername \>', que está em conflito com um membro implicitamente declarado para membro '\< membername2 \>' na classe base '\< baseclassname \>'. Portanto o membro deve ser declarado 'Shadows'.  
  
 Um membro de uma classe derivada gera um membro implícito com o mesmo nome como um membro implícito de classe base. Como membros implícitos não especificar [Sobrecargas](/dotnet/visual-basic/language-reference/modifiers/overloads), o compilador pressupõe que esse membro [Sombras](/dotnet/visual-basic/language-reference/modifiers/shadows) o membro de classe de base implícito. Seu código é mais legível e menos propenso a erro, se você especificar explicitamente o `Shadows` palavra\-chave para esse membro.  
  
 O [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador cria membros implícitos correspondentes a certos elementos de programação que você declarar. A tabela a seguir resume esses implícita ou *sintética*, membros.  
  
|Elementos declarados|Membros criados implicitamente|  
|--------------------------|------------------------------------|  
|Enumeração|`value__` membro|  
|Evento|`add_<eventname>` procedimento<br /><br /> `remove_<eventname>` procedimento<br /><br /> `<eventname>Event` campo<br /><br /> `<eventname>EventHandler` Delegar|  
|Propriedade|`get_<propertyname>` procedimento<br /><br /> `set_<propertyname>` procedimento|  
|`My.Form` membro, `My.WebService` membro, ou uma classe marcada com o <xref:Microsoft.VisualBasic.MyGroupCollectionAttribute> atributo|`m_<variablename>` `Static` variável<br /><br /> `<variablename>` propriedade<br /><br /> `get_<variablename>` procedimento<br /><br /> `set_<variablename>` procedimento|  
|`WithEvents` variável|`_<variablename>` variável<br /><br /> `<variablename>` propriedade<br /><br /> `get_<variablename>` procedimento<br /><br /> `set_<variablename>` procedimento|  
  
 Devido ao risco de conflitos de nome, você deve evitar qualquer elemento de programação declarado usando a mesma forma como qualquer um desses membros implícitos de nomenclatura. Por exemplo, você deve evitar qualquer elemento nome que começa com `get_` ou `set_`.  
  
 Por padrão, essa mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC40018  
  
### Para corrigir este erro  
  
-   Se você pretende ocultar ou sombra, o membro de classe de base implícito, inclua o [Sombras](/dotnet/visual-basic/language-reference/modifiers/shadows) palavra\-chave na declaração de membro da classe derivada.  
  
-   Se você não pretende sombrear o membro da classe de base implícito, altere o nome do membro da classe derivada para evitar conflitos com nomes listados na tabela anterior.  
  
## Consulte também  
 [Nomes de elemento declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)