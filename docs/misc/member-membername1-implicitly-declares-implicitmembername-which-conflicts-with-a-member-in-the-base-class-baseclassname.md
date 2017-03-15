---
title: "Membro &#39;&lt; membername1 &gt;&#39; declara implicitamente &#39;&lt; implicitmembername &gt;&#39;, que est&#225; em conflito com um membro na classe base &#39;&lt; baseclassname &gt;&#39; | Microsoft Docs"
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
  - "vbc40022"
  - "bc40022"
helpviewer_keywords: 
  - "BC40022"
ms.assetid: be5bb2ee-2274-42b2-b843-179b14127b34
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Membro &#39;&lt; membername1 &gt;&#39; declara implicitamente &#39;&lt; implicitmembername &gt;&#39;, que est&#225; em conflito com um membro na classe base &#39;&lt; baseclassname &gt;&#39;
Membro '\< membername1 \>' declara implicitamente '\< implicitmembername \>', que está em conflito com um membro na classe base '\< baseclassname \>', e então o membro não deve ser declarado como 'Overloads'  
  
 Uma propriedade em uma classe derivada gera um membro implícito com o mesmo nome como um membro da classe base e especifica a [Sobrecargas](/dotnet/visual-basic/language-reference/modifiers/overloads) palavra\-chave.  
  
 Sobrecarga é usado para definir várias versões de uma propriedade ou procedimento todas na mesma classe. Você não pode definir uma versão adicional de um membro da classe base, a menos que esse membro da classe base já especifique `Overloads`. Como membro da classe base em conflito não especifica `Overloads`, o compilador pressupõe que esta propriedade [Sombras](/dotnet/visual-basic/language-reference/modifiers/shadows) o membro de classe de base implícito.  
  
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
  
 **ID do erro:** BC40022  
  
### Para corrigir este erro  
  
-   Se você pretende ocultar ou sombra, o membro da classe base, substitua o [Sobrecargas](/dotnet/visual-basic/language-reference/modifiers/overloads) palavra\-chave com o [Sombras](/dotnet/visual-basic/language-reference/modifiers/shadows) palavra\-chave na declaração da propriedade.  
  
-   Se você não pretende sombrear o membro da classe base, altere o nome da propriedade para evitar os conflitos de nome descritos na tabela anterior.  
  
## Consulte também  
 [Nomes de elemento declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)