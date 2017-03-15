---
title: "CA1811: evitar c&#243;digo privado n&#227;o chamado | Microsoft Docs"
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
  - "AvoidUncalledPrivateCode"
  - "CA1811"
helpviewer_keywords: 
  - "CA1811"
  - "AvoidUncalledPrivateCode"
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1811: evitar c&#243;digo privado n&#227;o chamado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUncalledPrivateCode|  
|CheckId|CA1811|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um membro particular ou interno de nível de assembly \(\) não tem chamadores no assembly, não é invocado por Common Language Runtime, e não é invocado por um representante.  Os seguintes membros não são verificados por essa regra:  
  
-   Membros explícitos da interface.  
  
-   Construtores estáticos.  
  
-   Construtores de serialização.  
  
-   Métodos marcados com <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> ou <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.  
  
-   Membros que são substituições.  
  
## Descrição da Regra  
 Esta regra pode relatar falsos positivos se os pontos de entrada ocorrem que não são identificados atualmente pela lógica da regra.  Além disso, um compilador pode emitir o código noncallable em um assembly.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova o código noncallable ou adicione o código que o chama.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra.  
  
## Regras Relacionadas  
 [CA1812: evitar classes internas sem instâncias](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)  
  
 [CA1801: revisar parâmetros não usados](../Topic/CA1801:%20Review%20unused%20parameters.md)  
  
 [CA1804: remover locais não usados](../code-quality/ca1804-remove-unused-locals.md)