---
title: "Namespace de raiz &lt; nomenamespace &gt; n&#227;o &#233; compat&#237;vel com CLS | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40038"
  - "vbc40038"
helpviewer_keywords: 
  - "BC40038"
ms.assetid: ec850295-b2fe-4f19-b808-d22fe0aaa32d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Namespace de raiz &lt; nomenamespace &gt; n&#227;o &#233; compat&#237;vel com CLS
Um assembly é marcado como `<CLSCompliant(True)>`, mas o nome do namespace raiz começa com um sublinhado \(`_`\).  
  
 Um elemento de programação pode conter um ou mais sublinhados, mas to ser compatível com o [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), ele não deve começar com um sublinhado. Consulte [Nomes de elemento declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names).  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute> para um elemento de programação, você definir o atributo `isCompliant` parâmetro como `True` ou `False` para indicar compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar o <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC40038  
  
### Para corrigir este erro  
  
-   Se você precisar de compatibilidade com CLS, altere o nome do namespace raiz para que ele não começa com um sublinhado.  
  
-   Se você precisar que o nome do namespace raiz permanecem inalterados, em seguida, remova o <xref:System.CLSCompliantAttribute> do assembly ou marcá\-lo como `<CLSCompliant(False)>`.  
  
## Consulte também  
 [Instrução Namespace](/dotnet/visual-basic/language-reference/statements/namespace-statement)   
 [Namespaces no Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/namespaces)   
 [\/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace)   
 [NIB: Como: alterar o Namespace para um aplicativo \(Visual Basic\)](http://msdn.microsoft.com/pt-br/029d85c0-e173-4f7a-afba-a29f3aaf6ebf)   
 [Nomes de elemento declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)   
 [Convenções de nomenclatura do Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/naming-conventions)   
 [\< PAVE OVER \> escrevendo código compatível com CLS](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3)