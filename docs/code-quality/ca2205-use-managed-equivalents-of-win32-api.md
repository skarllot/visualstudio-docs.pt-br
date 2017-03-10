---
title: "CA2205: usar equivalentes gerenciados da API do Win32 | Microsoft Docs"
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
  - "UseManagedEquivalentsOfWin32Api"
  - "CA2205"
helpviewer_keywords: 
  - "CA2205"
  - "UseManagedEquivalentsOfWin32Api"
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2205: usar equivalentes gerenciados da API do Win32
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseManagedEquivalentsOfWin32Api|  
|CheckId|CA2205|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um método de invocação de plataforma é definido e um método com a funcionalidade equivalente existe na biblioteca de classes de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] .  
  
## Descrição da Regra  
 Um método de invocação de plataforma é usado para chamar uma função não gerenciado DLL e definido usando o atributo de <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> , ou a palavra\-chave de `Declare` no Visual Basic.  Um método definido incorretamente de invocação de plataforma pode resultar em exceções em tempo de execução devido a problemas como uma função misnamed, defeituoso um mapeamento de tipos de dados do parâmetro e o valor de retorno, e as especificações de campo incorretas, como a convenção de chamada e o conjunto de caracteres.  Se disponível, normalmente é mais simples e o sujeito a erros chamar o método gerenciado equivalente do que para definir diretamente e chamar o método não gerenciado.  Chamar um método de invocação de plataforma também pode resultar em problemas de segurança adicionais que precisam ser resolvidos.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, substitua a chamada para a função não gerenciado com uma chamada para seu equivalente gerenciado.  
  
## Quando Suprimir Alertas  
 Suprima um aviso dessa regra se o método sugerido de substituição não fornece a funcionalidade necessária.  
  
## Exemplo  
 O exemplo a seguir mostra uma definição do método de invocação de plataforma que viola a regra.  Além disso, as chamadas para o método de invocação de preparo e ao método gerenciado equivalente são mostrados.  
  
 [!code-cs[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]  
  
## Regras Relacionadas  
 [CA1404: chamar GetLastError logo depois de P\/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)  
  
 [CA1060: mover P\/Invokes para a classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: os pontos de entrada P\/Invoke devem existir](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)  
  
 [CA1401: P\/Invokes não deve estar visível](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)  
  
 [CA2101: especificar marshaling para argumentos da cadeia de caracteres P\/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)