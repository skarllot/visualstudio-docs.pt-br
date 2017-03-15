---
title: "Tipo de restri&#231;&#227;o de par&#226;metro gen&#233;rico &lt; typename &gt; n&#227;o &#233; compat&#237;vel com CLS | Microsoft Docs"
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
  - "bc40040"
  - "vbc40040"
helpviewer_keywords: 
  - "BC40040"
ms.assetid: c640dd59-56a9-43ed-b199-32a60f7b9b06
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de restri&#231;&#227;o de par&#226;metro gen&#233;rico &lt; typename &gt; n&#227;o &#233; compat&#237;vel com CLS
Um tipo genérico é marcado como `<CLSCompliant(True)>`, mas uma restrição em um de seus parâmetros de tipo Especifica um tipo que está marcado como `<CLSCompliant(False)>`, não é marcada ou não se qualifica porque ele é um tipo incompatível.  
  
 Para um tipo para ser compatível com o [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), ele deve usar somente tipos compatíveis com CLS. Isso se aplica também as restrições em parâmetros de tipo de um tipo genérico.  
  
 O seguinte [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] tipos de dados não são compatíveis com CLS:  
  
-   [Tipo de dados SByte](/dotnet/visual-basic/language-reference/data-types/sbyte-data-type)  
  
-   [Tipo de dados UInteger](/dotnet/visual-basic/language-reference/data-types/uinteger-data-type)  
  
-   [Tipo de dados ULong](/dotnet/visual-basic/language-reference/data-types/ulong-data-type)  
  
-   [Tipo de dados UShort](/dotnet/visual-basic/language-reference/data-types/ushort-data-type)  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute> atributo a um elemento de programação, você definir o atributo `isCompliant` parâmetro como `True` ou `False` para indicar compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC40040  
  
### Para corrigir este erro  
  
-   Se o tipo genérico deve aceitar um parâmetro de tipo restringido por esse tipo específico, remova <xref:System.CLSCompliantAttribute>. O tipo não pode ser compatível com CLS.  
  
-   Se o tipo genérico deve ser compatível com CLS, altere o tipo desta restrição para o tipo compatível com CLS mais próximo. Por exemplo, no lugar de `UInteger` você poderá usar `Integer` se você não precisar do intervalo de valor acima de 2.147.483.647. Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [\< PAVE OVER \> escrevendo código compatível com CLS](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3)