---
title: "CA1017: marcar assemblies com ComVisibleAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1017"
  - "MarkAssembliesWithComVisible"
helpviewer_keywords: 
  - "MarkAssembliesWithComVisible"
  - "CA1017"
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1017: marcar assemblies com ComVisibleAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithComVisible|  
|CheckId|CA1017|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um assembly não tenha um atributo de <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> aplicado a ela.  
  
## Descrição da Regra  
 O atributo de <xref:System.Runtime.InteropServices.ComVisibleAttribute> determina como código gerenciado do acesso de clientes COM.  O bom design exige que os assemblies indica explicitamente a visibilidade da.  A visibilidade de COM pode ser definida para um assembly inteiro e então ser substituída para tipos e membros individuais do tipo.  Se o atributo não estiver presente, o conteúdo do assembly são visíveis aos clientes COM.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, adicione o atributo ao assembly.  Se você não quiser que o assembly seja visível aos clientes COM, aplicar o atributo e defina seu valor como `false`.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  Se você quiser que o assembly seja visível, aplicar o atributo e defina seu valor como `true`.  
  
## Exemplo  
 O exemplo a seguir mostra um assembly que tem o atributo de <xref:System.Runtime.InteropServices.ComVisibleAttribute> aplicado para impedir que seja visível para clientes COM.  
  
 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-cs[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]  
  
## Consulte também  
 [Interoperação com código não gerenciado](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Qualificando tipos do .NET para interoperação](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)