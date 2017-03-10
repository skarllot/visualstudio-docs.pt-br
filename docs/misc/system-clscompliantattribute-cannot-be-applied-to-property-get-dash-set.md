---
title: "CLSCompliantAttribute n&#227;o pode ser aplicado &#224; propriedade &#39;Get&#39; / &#39;Set&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40043"
  - "BC40043"
helpviewer_keywords: 
  - "BC40043"
ms.assetid: 2ff45c09-32be-4ca9-b42a-63ce2536db7d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CLSCompliantAttribute n&#227;o pode ser aplicado &#224; propriedade &#39;Get&#39; / &#39;Set&#39;
Uma definição de propriedade se aplica a <xref:System.CLSCompliantAttribute> atributo à sua `Get` ou `Set` instrução.  
  
 Para uma propriedade ser compatível com o [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), toda a propriedade deve ser marcada como `<CLSCompliant(True)>`. Você deve aplicar o <xref:System.CLSCompliantAttribute> para o [Instrução Property](/dotnet/visual-basic/language-reference/statements/property-statement), não para o `Get` ou o `Set` instrução.  
  
 Quando você aplica <xref:System.CLSCompliantAttribute> para um elemento de programação, você definir o atributo `isCompliant` parâmetro como `True` ou `False` para indicar compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC40043  
  
### Para corrigir este erro  
  
-   Remover <xref:System.CLSCompliantAttribute> da `Get` ou `Set` instrução.  
  
-   Se a propriedade deve ser compatível com CLS, marcar o `Property` instrução como `<CLSCompliant(True)>`.  
  
## Consulte também  
 [\< PAVE OVER \> escrevendo código compatível com CLS](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3)   
 [Instrução Get](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Instrução Set](/dotnet/visual-basic/language-reference/statements/set-statement)