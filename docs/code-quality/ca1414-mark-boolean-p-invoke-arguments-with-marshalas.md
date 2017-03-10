---
title: "CA1414: marcar argumentos P/Invoke boolianos com MarshalAs | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1414"
  - "MarkBooleanPInvokeArgumentsWithMarshalAs"
helpviewer_keywords: 
  - "CA1414"
  - "MarkBooleanPInvokeArgumentsWithMarshalAs"
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1414: marcar argumentos P/Invoke boolianos com MarshalAs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|  
|CheckId|CA1414|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Uma declaração de método de invocação de plataforma do inclui um parâmetro ou um valor de retorno <xref:System.Boolean?displayProperty=fullName> mas o atributo de <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> não é aplicado ao parâmetro ou ao valor de retorno.  
  
## Descrição da Regra  
 Um método de invocação de plataforma acessa o código não gerenciado e é definido com a palavra\-chave de `Declare` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou em <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>.  <xref:System.Runtime.InteropServices.MarshalAsAttribute> especifica o comportamento marshaling usado para converter tipos de dados entre o código gerenciado e não gerenciado.  Muitos tipos de dados simples, como <xref:System.Byte?displayProperty=fullName> e <xref:System.Int32?displayProperty=fullName>, têm uma única representação em código não gerenciado e que não exigem a especificação de seu comportamento marshaling; Common Language Runtime fornece automaticamente comportamento correto.  
  
 O tipo de dados de <xref:System.Boolean> tiver várias representações em código não gerenciado.  Quando <xref:System.Runtime.InteropServices.MarshalAsAttribute> não for especificado, o comportamento marshaling do padrão para o tipo de dados de <xref:System.Boolean> é <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>.  Este é um inteiro de 32 bits, que não é apropriada em todas as condições.  A representação booliana que é exigida pelo método não gerenciado deve ser determinada e corresponde a <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>apropriado.  UnmanagedType.Bool é o tipo do Win32 BOOL, que sempre é 4 bytes.  UnmanagedType.U1 deve ser usado para C\+\+ `bool` ou outros tipos de 1 byte.  Para obter mais informações, consulte [Default Marshaling for Boolean Types](http://msdn.microsoft.com/pt-br/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, aplique <xref:System.Runtime.InteropServices.MarshalAsAttribute> para o parâmetro ou ao valor de retorno de <xref:System.Boolean> .  Defina o valor do atributo a <xref:System.Runtime.InteropServices.UnmanagedType>apropriado.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  Se o comportamento marshaling de opção é apropriado, o código é mantido mais facilmente quando o comportamento é especificado explicitamente.  
  
## Exemplo  
 O exemplo a seguir mostra dois métodos de invocação de plataforma que são marcados com os atributos apropriados de <xref:System.Runtime.InteropServices.MarshalAsAttribute> .  
  
 [!code-cs[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]  
  
## Regras Relacionadas  
 [CA1901: as declarações de P\/Invoke devem ser portáteis](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)  
  
 [CA2101: especificar marshaling para argumentos da cadeia de caracteres P\/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
## Consulte também  
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>   
 [Default Marshaling for Boolean Types](http://msdn.microsoft.com/pt-br/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)   
 [Interoperação com código não gerenciado](../Topic/Interoperating%20with%20Unmanaged%20Code.md)