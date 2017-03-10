---
title: "m&#233;todo de &#39;&lt; procedurename &gt;&#39; para o evento &#39;&lt; eventname &gt;&#39; n&#227;o &#233; poss&#237;vel marcar CLS porque seu tipo recipiente &#39;&lt; typename &gt;&#39; n&#227;o &#233; compat&#237;vel com CLS | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40053"
  - "bc40053"
helpviewer_keywords: 
  - "BC40053"
ms.assetid: 5f7aaf64-b5e6-4f97-9ebd-44cd4c7e8bf5
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# m&#233;todo de &#39;&lt; procedurename &gt;&#39; para o evento &#39;&lt; eventname &gt;&#39; n&#227;o &#233; poss&#237;vel marcar CLS porque seu tipo recipiente &#39;&lt; typename &gt;&#39; n&#227;o &#233; compat&#237;vel com CLS
Um evento personalizado declara um `AddHandler` ou `RemoveHandler` procedimento e marcá\-lo como `<CLSCompliant(True)>`, mas o evento é definido em um tipo que está marcado como `<CLSCompliant(False)>` ou não está marcado.  
  
 Quando você aplica <xref:System.CLSCompliantAttribute> para um elemento de programação, você definir o atributo `isCompliant` parâmetro como `True` ou `False` para indicar compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC40053  
  
### Para corrigir este erro  
  
-   Se você precisar de compatibilidade com CLS, defina o evento em um tipo que é compatível com CLS.  
  
-   Se você precisar que o evento permaneça em seu tipo recipiente, remova <xref:System.CLSCompliantAttribute> da sua definição ou marque\-a como `<CLSCompliant(False)>`.  
  
## Consulte também  
 [Como declarar eventos personalizados para evitar bloqueio](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md)   
 [Como declarar eventos personalizados para conservar memória](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md)   
 [NÃO na compilação: AddHandler e RemoveHandler](http://msdn.microsoft.com/pt-br/a7a24bd2-519a-46fe-8a2c-2b9df2ca28ef)   
 [\< PAVE OVER \> escrevendo código compatível com CLS](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3)