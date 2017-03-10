---
title: "CA1060: mover P/Invokes para a classe NativeMethods | Microsoft Docs"
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
  - "MovePInvokesToNativeMethodsClass"
  - "CA1060"
helpviewer_keywords: 
  - "CA1060"
  - "MovePInvokesToNativeMethodsClass"
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1060: mover P/Invokes para a classe NativeMethods
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MovePInvokesToNativeMethodsClass|  
|CheckId|CA1060|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um método usa Serviços de Invocação de Plataforma para acessar código não gerenciado e não é um membro de uma das classes **NativeMethods**.  
  
## Descrição da Regra  
 Métodos de Invocação de Plataforma, tais como os marcados usando o atributo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>, ou métodos definidos usando a palavra\-chave `Declare` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] acessam código não gerenciado.  Esses métodos devem estar em uma das seguintes classes:  
  
-   **NativeMethods** \- esta classe não suprime movimentação da pilha para permissão de código não gerenciado. \(<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> não deve ser aplicado a esta classe.\) Essa classe é para métodos que possam ser usados em qualquer lugar já que será feita uma movimentação de pilha.  
  
-   **SafeNativeMethods** \- essa classe suprime movimentação de pilha para permissão de código não gerenciado. \(<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> é aplicado a esta classe.\) Essa classe é para métodos que são seguros para que qualquer um chame.  Os chamadores de esses métodos não precisam fazer uma checagem de segurança completa para certificar\-se de que o uso é seguro, já que, os métodos são inofensivos para qualquer chamador.  
  
-   **UnsafeNativeMethods** \- essa classe suprime movimentação de pilha para permissão de código não gerenciado. \(<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> é aplicado a esta classe.\) Essa classe é para métodos potencialmente perigosos.  Qualquer chamador destes métodos deve fazer uma checagem de segurança completa para certificar\-se de que o uso é seguro uma vez que não haverá movimentação de pilha.  
  
 Essas classes são declaradas como `internal` \(`Friend`, no Visual Basic\) e declaram um construtor particular para impedir que novas instâncias sejam criadas.  Os métodos nestas classes devem ser `static` e `internal` \(`Shared` e `Friend` no Visual Basic\).  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, mova o método para a classe apropriada de **NativeMethods**.  Para a maioria dos aplicativos, mover P\/Invokes para uma nova classe chamada de **NativeMethods** é suficiente.  
  
 No entanto, se você estiver desenvolvendo bibliotecas para uso em outros aplicativos, você deve considerar definir duas outras classes que chamadas de **SafeNativeMethods** e **UnsafeNativeMethods**.  Essas classes são semelhantes à classe **NativeMethods**; no entanto, são marcadas usando um atributo especial chamado **SuppressUnmanagedCodeSecurityAttribute**.  Quando esse atributo é aplicado, o runtime não faz uma movimentação completa de pilha para certificar\-se de que todos os chamadores têm a permissão **UnmanagedCode**.  O runtime normalmente verifica por esta permissão na inicialização.  Uma vez que a verificação não é executada, é possível aumentar melhorar o desempenho para chamadas a estes métodos não gerenciados. Isso também habilita que código com permissões limitadas chame estes métodos.  
  
 Você deve, no entanto, usar este atributo com muito cuidado.  Ele pode ter graves implicações na segurança se implementado incorretamente.  
  
 Para obter informações sobre como implementar métodos, consulte o exemplo **NativeMethods**, o exemplo **SafeNativeMethods**, e o exemplo **UnsafeNativeMethods**.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir declara um método que viola esta regra.  Para corrigir a violação o **RemoveDirectory** P\/Invoke deve ser movido para uma classe adequada que seja projetada para armazenar somente P\/Invokes.  
  
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-cs[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]  
  
## Exemplo de NativeMethods  
  
### Descrição  
 Uma vez que a classe **NativeMethods** não deve ser marcada usando P\/Invokes **SuppressUnmanagedCodeSecurityAttribute**, que são colocado nela ela exigirá permissão **UnmanagedCode**.  Uma vez que a maioria dos aplicativos são executados do computador local e rodam sob confiança total, isso geralmente não é um problema.  No entanto, se você estiver desenvolvendo bibliotecas reutilizáveis, você deve considerar definir uma classe **SafeNativeMethods** ou **UnsafeNativeMethods**.  
  
 O exemplo a seguir mostra um método **Interaction.Beep** que envolve a função **MessageBeep** do user32.dll.  O P\/Invoke **MessageBeep** é colocado na classe **NativeMethods**.  
  
### Código  
 [!code-cs[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]  
  
## Exemplo de SafeNativeMethods  
  
### Descrição  
 Os métodos de P\/Invoke que podem ser expostos com segurança a qualquer aplicativo e que não têm nenhum efeito colateral devem ser colocados em uma classe chamada de **SafeNativeMethods**.  Você precisa requerer permissões e você prestar muita atenção ao local de onde são chamados.  
  
 O exemplo a seguir mostra uma propriedade **Environment.TickCount** que envolve a função **GetTickCount** de kernel32.dll.  
  
### Código  
 [!CODE [FxCop.Design.NativeMethodsSafe#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe#1)]  
  
## Exemplo de UnsafeNativeMethods  
  
### Descrição  
 Os métodos de P\/Invoke que não podem ser chamados com segurança e que podem causar efeitos colaterais devem ser colocados em uma classe chamada de **UnsafeNativeMethods**.  Esses métodos devem rigorosamente checados para certificar\-se que não sejam expostos ao usuário inadvertidamente.  A regra [CA2118: revisar uso de SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) pode ajudar com isso.  Alternativamente, os métodos devem ter uma outra permissão que é demandada no lugar de **UnmanagedCode** quando eles os usam.  
  
 O exemplo a seguir mostra um método **Cursor.Hide** que envolve a função **ShowCursor** de user32.dll.  
  
### Código  
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-cs[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]  
  
## Consulte também  
 [Avisos de design](../code-quality/design-warnings.md)