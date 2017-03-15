---
title: "Avisos de confiabilidade | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.reliabilityrules"
helpviewer_keywords: 
  - "avisos de confiabilidade"
  - "avisos de confiabilidade"
  - "avisos da análise de código gerenciado, avisos de confiabilidade"
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Avisos de confiabilidade
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os avisos da confiabilidade dão suporte à biblioteca e a confiabilidade do aplicativo, como o uso correto de memória e do thread.  
  
## Nesta seção  
  
|Regra|Descrição|  
|-----------|---------------|  
|[CA2000: descartar objetos antes de perder o escopo](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Como um evento excepcional pode ocorrer que evite o finalizador de um objeto de execução, o objeto deve ser explicitamente descartado antes que todas as referências a ele estão fora do escopo.|  
|[CA2001: evitar métodos problemáticos de chamada](../Topic/CA2001:%20Avoid%20calling%20problematic%20methods.md)|Um membro chama um método potencialmente perigoso ou problemático.|  
|[CA2002: não bloquear objetos com identidade fraca](../Topic/CA2002:%20Do%20not%20lock%20on%20objects%20with%20weak%20identity.md)|Um objeto será considerado como ter uma identidade quando fraco pode ser acessado diretamente nos limites do domínio de aplicativo.  Um thread que tentar adquirir um bloqueio em um objeto que tem uma identidade e pode ser bloqueada por um segundo thread em um domínio de aplicativo diferente que tem um bloqueio no mesmo objeto.|  
|[CA2003: não tratar fibras como threads](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Um thread gerenciado está sendo tratado como um thread Win32.|  
|[CA2004: remover chamadas para GC.KeepAlive](../Topic/CA2004:%20Remove%20calls%20to%20GC.KeepAlive.md)|Se você estiver convertendo para uso de SafeHandle, remova todas as chamadas a GC.KeepAlive \(objeto\).  Nesse caso, as classes não devem ter que chamar GC.KeepAlive, supondo que elas não tiverem um finalizador mas dependem de SafeHandle para finalizar o identificador do sistema operacional para ele.|  
|[CA2006: use SafeHandle para encapsular recursos nativos](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|O uso de IntPtr em código gerenciado pode indicar um problema potencial de segurança e à confiabilidade.  Todos os usos de IntPtr devem ser examinados para determinar se o uso de um SafeHandle, ou a tecnologia semelhante, são necessários em seu lugar.|