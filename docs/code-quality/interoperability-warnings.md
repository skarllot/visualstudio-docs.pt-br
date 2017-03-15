---
title: "Avisos de interoperabilidade | Microsoft Docs"
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
  - "vs.codeanalysis.Interoperabilityrules"
helpviewer_keywords: 
  - "avisos da análise de código gerenciado, avisos de interoperabilidade"
  - "avisos de interoperabilidade"
  - "avisos de interoperabilidade"
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Avisos de interoperabilidade
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os avisos de interoperabilidade dão suporte à interação com clientes COM.  
  
## Nesta seção  
  
|Regra|Descrição|  
|-----------|---------------|  
|[CA1400: os pontos de entrada P\/Invoke devem existir](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)|Um público ou um método protegido são marcados usando o atributo de System.Runtime.InteropServices.DllImportAttribute.  Ou biblioteca não gerenciado não pode ser encontrada ou o método não pode corresponder a uma função na biblioteca.|  
|[CA1401: P\/Invokes não deve estar visível](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)|Um público ou um método protegido em um tipo utilitário têm o atributo de System.Runtime.InteropServices.DllImportAttribute \(também implementada pela palavra\-chave declarar no Visual Basic\).  Esses métodos não devem ser expostos.|  
|[CA1402: evitar sobrecargas em interfaces visíveis COM](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Quando os métodos sobrecarregados são expostos para clientes COM, apenas a primeira sobrecarga do método retém seu nome.  As sobrecargas subsequentes são renomeadas exclusivamente através do nome a um caractere de sublinhado \(\_\) e um inteiro que corresponde à ordem de declaração de sobrecarga.|  
|[CA1403: os tipos de layout automático não devem ser visíveis em COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Um tipo de valor COM\- visível é marcado usando o atributo de System.Runtime.InteropServices.StructLayoutAttribute definido como LayoutKind.Auto.  O layout deless podem ser alterados entre versões de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], que interromperão clientes COM que esperam por um layout específico.|  
|[CA1404: chamar GetLastError logo depois de P\/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|For feita uma chamada para o método de Marshal.GetLastWin32Error ou à função de  [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)]GetLastError de equivalente, e a chamada imediatamente anterior não é a um método de invocação de plataforma.|  
|[CA1405: os tipos base de tipo visível em COM devem ser visíveis em COM](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Um tipo COM\- visível é derivado de um tipo que não é COM\- visível.|  
|[CA1406: evitar argumentos Int64 para clientes do Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Visual Basic 6 clientes COM não pode acessar inteiros de 64 bits.|  
|[CA1407: evitar membros estáticos em tipos visíveis COM](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)|COM o não oferece suporte a métodos estáticos.|  
|[CA1408: não usar AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|Tipos que usa uma interface dupla permite que clientes para associar a um layout específico da interface.  Todas as modificações em uma versão futura ao layout do tipo ou de qualquer tipo de base do travará clientes COM que são associados à interface.  Por padrão, se o atributo de ClassInterfaceAttribute não for especificado, uma interface de expedição somente é usada.|  
|[CA1409: os tipos visíveis Com devem ser criáveis](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Um tipo de referência que é marcado como visível a especificamente COM parâmetros contém um construtor público mas não contém um construtor \(sem parâmetros\) público padrão.  Um tipo sem um construtor público padrão não é creatable por clientes COM.|  
|[CA1410: os métodos de registro COM devem ser correspondentes](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Um tipo declara um método marcado usando o atributo de <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> mas não declara um método marcado usando o atributo de <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> , ou vice\-versa.|  
|[CA1411: os métodos de registro COM não devem estar visíveis](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Um método que foi marcada usando o atributo de System.Runtime.InteropServices.ComRegisterFunctionAttribute ou atributo de System.Runtime.InteropServices.ComUnregisterFunctionAttribute externamente é visível.|  
|[CA1412: marcar interfaces ComSource como IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Um tipo é marcado usando o atributo de System.Runtime.InteropServices.ComSourceInterfacesAttribute e, pelo menos uma das interfaces especificadas não está marcado usando o atributo de System.Runtime.InteropServices.InterfaceTypeAttribute definido como ComInterfaceType.InterfaceIsIDispatch.|  
|[CA1413: evitar campos não públicos em tipos de valor visíveis COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|Os campos público da instância de tipo de valor COM\- visíveis são visíveis aos clientes COM.  Revise o conteúdo dos campos de informações que não são expostos, ou que terá efeitos não intencional de design ou de segurança.|  
|[CA1414: marcar argumentos P\/Invoke boolianos com MarshalAs](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|O tipo de dados booliano tiver várias representações em código não gerenciado.|  
|[CA1415: declarar P\/Invokes corretamente](../code-quality/ca1415-declare-p-invokes-correctly.md)|Esta regra procura as declarações de método de invocação de plataforma que visem as funções de [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] que têm um ponteiro para um parâmetro SOBREPOR da estrutura e o parâmetro gerenciado correspondente não é um ponteiro para uma estrutura de <xref:System.Threading.NativeOverlapped?displayProperty=fullName>.|