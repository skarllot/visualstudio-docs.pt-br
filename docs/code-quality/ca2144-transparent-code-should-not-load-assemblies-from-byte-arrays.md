---
title: "CA2144: o c&#243;digo transparente n&#227;o deve carregar assemblies a partir de matrizes de bytes | Microsoft Docs"
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
  - "CA2144"
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2144: o c&#243;digo transparente n&#227;o deve carregar assemblies a partir de matrizes de bytes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|  
|CheckId|CA2144|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um método transparente carrega um assembly de uma matriz de bytes usando um dos seguintes métodos:  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
## Descrição da Regra  
 A revisão de segurança para o código transparente não é tão completa quanto a revisão de segurança para o código crítico, porque o código transparente não pode executar ações confidenciais de segurança.  Os assemblies carregados de uma matriz de bytes não podem ser anotados no código transparente, e a matriz de bytes pode conter código crítico ou, mais importante seguro\- crítico, que precisa ser auditado.  Em virtude disso, o código transparente não deve carregar os assemblies SMO uma matriz de bytes.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, marque o método que está carregando o assembly com <xref:System.Security.SecurityCriticalAttribute> ou atributo de <xref:System.Security.SecuritySafeCriticalAttribute> .  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 Aciona de regra no seguinte código porque um método transparente carrega um assembly de uma matriz de bytes.  
  
 [!code-cs[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../code-quality/codesnippet/CSharp/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays_1.cs)]