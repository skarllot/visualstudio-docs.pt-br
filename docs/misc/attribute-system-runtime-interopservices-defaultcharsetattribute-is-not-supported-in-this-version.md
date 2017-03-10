---
title: "N&#227;o h&#225; suporte para o atributo &#39;System.Runtime.InteropServices.DefaultCharSetAttribute&#39; nesta vers&#227;o | Microsoft Docs"
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
  - "bc32510"
  - "vbc32510"
helpviewer_keywords: 
  - "BC32510"
ms.assetid: e2eec233-6e0b-4f2f-a801-b0274e579c0e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o h&#225; suporte para o atributo &#39;System.Runtime.InteropServices.DefaultCharSetAttribute&#39; nesta vers&#227;o
O <xref:System.Runtime.InteropServices.DefaultCharSetAttribute?displayProperty=fullName> atributo permite que você especifique o conjunto para ser usado em marshaling cadeias de caracteres. Seu valor tem um membro do <xref:System.Runtime.InteropServices.CharSet?displayProperty=fullName> enumeração.  
  
 A versão atual do [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] não oferece suporte a esse atributo. O suporte é possível em versões futuras.  
  
 **ID do erro:** BC32510  
  
### Para corrigir este erro  
  
-   Usar cada [Instrução Declare](/dotnet/visual-basic/language-reference/statements/declare-statement) para especificar o conjunto de caracteres para o procedimento externo está declarando. O exemplo a seguir ilustra isso.  
  
    ```  
    Ansi Declare Function GetUserName Lib "advapi32.dll" _ (ByVal lpBuffer As String, ByRef nSize As Integer) As Integer Unicode Declare Sub externalProc Lib "projectlib.dll" _ (ByVal arg As Double)  
    ```  
  
     Se você não especificar o conjunto de caracteres no `Declare` instrução, o padrão é ANSI.  
  
## Consulte também  
 <xref:System.Runtime.InteropServices.DefaultCharSetAttribute>   
 <xref:System.Runtime.InteropServices.CharSet>   
 [NÃO está em compilação: Atributos no Visual Basic](http://msdn.microsoft.com/pt-br/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Instrução Declare](/dotnet/visual-basic/language-reference/statements/declare-statement)