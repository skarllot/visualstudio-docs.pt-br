---
title: "Membro de &#39;MustOverride&#39; n&#227;o compat&#237;vel com CLS n&#227;o &#233; permitido em &lt; classname &gt; compat&#237;vel com CLS | Microsoft Docs"
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
  - "bc40034"
  - "vbc40034"
helpviewer_keywords: 
  - "BC40034"
ms.assetid: 4eb36b3a-1bbe-4e99-9ecb-a12b8729b128
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Membro de &#39;MustOverride&#39; n&#227;o compat&#237;vel com CLS n&#227;o &#233; permitido em &lt; classname &gt; compat&#237;vel com CLS
Uma classe está marcada como `<CLSCompliant(True)>`, mas ele não contém um `MustOverride` propriedade ou um procedimento marcado como `<CLSCompliant(False)>` ou não está marcado.  
  
 Quando uma classe é compatível com o [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), um aplicativo que use essa classe acessa apenas os membros que também são marcados como `<CLSCompliant(True)>` e ignora os membros que não são. No entanto, o aplicativo não pode ignorar uma `MustOverride` propriedade ou procedimento, porque ele deve acessar essa propriedade ou procedimento para substituí\-la.  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute> para um elemento de programação, você definir o atributo `isCompliant` parâmetro como `True` ou `False` para indicar compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar o <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC40034  
  
### Para corrigir este erro  
  
-   Se você precisar de compatibilidade com CLS e tem controle sobre o código fonte da classe, sinalize o membro como `<CLSCompliant(True)>`.  
  
-   Se você precisar de compatibilidade com CLS e não tem controle sobre o código de origem de classe, ou se ela não for compatível, defina este membro dentro de uma classe diferente.  
  
-   Se você requer que esse membro permaneça incompatível, remova o `MustOverride` palavra\-chave da sua definição, remova o <xref:System.CLSCompliantAttribute> da definição da classe, ou marcar a classe como `<CLSCompliant(False)>`.  
  
## Consulte também  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [\< PAVE OVER \> escrevendo código compatível com CLS](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3)