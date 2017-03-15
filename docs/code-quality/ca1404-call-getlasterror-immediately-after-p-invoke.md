---
title: "CA1404: chamar GetLastError logo depois de P/Invoke | Microsoft Docs"
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
  - "CallGetLastErrorImmediatelyAfterPInvoke"
  - "CA1404"
helpviewer_keywords: 
  - "CallGetLastErrorImmediatelyAfterPInvoke"
  - "CA1404"
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1404: chamar GetLastError logo depois de P/Invoke
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|  
|CheckId|CA1404|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 For feita uma chamada para o método de <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> ou função do Win32 `GetLastError` de equivalente, e a chamada de que vem antes não é a um método de invocação de plataforma.  
  
## Descrição da Regra  
 Um método de invocação de plataforma acessa o código não gerenciado e é definido com a palavra\-chave de `Declare` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou no atributo de <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> .  Em geral, na falha, funções não gerenciado chamam a função do Win32 `SetLastError` para definir um código de erro que é associado à falha.  O chamador de chamadas de funções que falharam a função do Win32 `GetLastError` para recuperar o código de erro e para determinar a causa da falha.  O código de erro é mantido em uma base por thread e substituído pela próxima chamada para `SetLastError`.  Depois que uma chamada para um método malsucedida da invocação de plataforma, código gerenciado pode recuperar o código de erro chamando o método de <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> .  Como o código de erro pode ser substituído por chamadas internos de outros métodos gerenciados da biblioteca de classe, o método de `GetLastError` ou de <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> deve ser chamado imediatamente depois da chamada do método de invocação de plataforma.  
  
 A regra ignora chamadas aos seguintes membros gerenciados quando ocorrem entre a chamada para o método de invocação de plataforma e chame para <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>.  Esses membros não alteram o código de erro e são úteis para determinar o êxito de algumas chamadas do método de invocação de plataforma.  
  
-   <xref:System.IntPtr.Zero?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, mova a chamada a <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> de modo que segue imediatamente a chamada para o método de invocação de plataforma.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se o código na chamada do método de invocação de preparo e a chamada do método de <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> não pode explicitamente ou implicitamente fazer com que o código de erro à alteração.  
  
## Exemplo  
 O exemplo a seguir mostra um método que viola a regra e um método que satisfaça a regra.  
  
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-cs[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]  
  
## Regras Relacionadas  
 [CA1060: mover P\/Invokes para a classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: os pontos de entrada P\/Invoke devem existir](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)  
  
 [CA1401: P\/Invokes não deve estar visível](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)  
  
 [CA2101: especificar marshaling para argumentos da cadeia de caracteres P\/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
 [CA2205: usar equivalentes gerenciados da API do Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)