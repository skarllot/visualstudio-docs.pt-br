---
title: "Membro &#39; &lt; interfacename &gt;. &lt; procedurename &gt;&#39; que corresponde a esta assinatura n&#227;o pode ser implementada como a interface &#39;&lt; interfacename &gt;&#39; cont&#233;m v&#225;rios membros com o mesmo nome e assinatura: &lt; signaturelist &gt; | Microsoft Docs"
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
  - "vbc30937"
  - "bc30937"
helpviewer_keywords: 
  - "BC30937"
ms.assetid: e917d85e-95e0-431a-9d09-39ce5d4fc894
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Membro &#39; &lt; interfacename &gt;. &lt; procedurename &gt;&#39; que corresponde a esta assinatura n&#227;o pode ser implementada como a interface &#39;&lt; interfacename &gt;&#39; cont&#233;m v&#225;rios membros com o mesmo nome e assinatura: &lt; signaturelist &gt;
Um procedimento ou propriedade tenta implementar um procedimento ou uma propriedade definida em uma interface implementada, mas o compilador encontra mais de uma versão do procedimento de interface ou propriedade com o mesmo nome e assinatura.  
  
 Esse erro pode ocorrer em uma situação com tipos genéricos construídos, como os seguintes esqueletos de declarações ilustram.  
  
```  
Public Interface baseInterface(Of t) Sub doSomething(ByVal inputValue As String) Sub doSomething(ByVal inputValue As t) End Class Public Class implementingClass Implements baseInterface(Of String) Sub doSomething(ByVal inputValue As String) _ Implements baseInterface(Of String).doSomething End Sub End Class  
```  
  
 Porque `implementingClass` implementa `baseInterface` fornecendo `String` para seu parâmetro de tipo `t`, as duas versões do `doSomething` em `baseInterface` assumem assinaturas idênticas, até onde `implementingClass` está preocupado. Como resultado, o compilador não pode determinar a versão que deseja implementar.  
  
 **ID do erro:** BC30937  
  
### Para corrigir este erro  
  
-   Altere o tipo de argumento ou argumentos fornecidos para a classe base para que ele não resulte em uma ou mais assinaturas idênticas de procedimentos ou propriedades membros.  
  
     \- ou \-  
  
-   Não implementam essa classe base. Você não pode implementá\-la com o conjunto de argumentos de tipo que você está usando, como você deve implementar cada um dos seus membros.  
  
## Consulte também  
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [Instrução Implements](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [NÃO está em compilação: Palavra\-chave Implements e a instrução Implements](http://msdn.microsoft.com/pt-br/b96560f7-6413-480f-a1e2-f80253bab5be)