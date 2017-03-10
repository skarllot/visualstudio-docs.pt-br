---
title: "CA1016: marcar assemblies com AssemblyVersionAttribute | Microsoft Docs"
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
  - "MarkAssembliesWithAssemblyVersion"
  - "CA1016"
helpviewer_keywords: 
  - "CA1016"
  - "MarkAssembliesWithAssemblyVersion"
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1016: marcar assemblies com AssemblyVersionAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithAssemblyVersion|  
|CheckId|CA1016|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 O assembly não tem um número de versão.  
  
## Descrição da Regra  
 A identidade de um assembly é composto das seguintes informações:  
  
-   Nome do assembly  
  
-   Número de versão  
  
-   Cultura  
  
-   Chave pública \(para assemblies altamente nomeados\).  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] usa o número de versão para identificar exclusivamente um assembly, e para associar digitar os assemblies altamente nomeados.  O número de versão é usado junto com a versão e a política do publicador.  Por padrão, os aplicativos são executados somente com a versão do assembly com que foram criados.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, adicione um número de versão ao assembly usando o atributo de <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> .  Consulte o exemplo a seguir.  
  
## Quando Suprimir Alertas  
 Não suprima um aviso desta regra para assemblies que são usados por terceiros, ou em um ambiente de produção.  
  
## Exemplo  
 O exemplo a seguir mostra um assembly que tem o atributo de <xref:System.Reflection.AssemblyVersionAttribute> aplicado.  
  
 [!code-cs[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]  
  
## Consulte também  
 [Controle de versão de assemblies](../Topic/Assembly%20Versioning.md)   
 [Como criar uma política de editor](../Topic/How%20to:%20Create%20a%20Publisher%20Policy.md)