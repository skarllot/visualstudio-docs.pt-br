---
title: "CA2132: os construtores padr&#227;o devem ser pelo menos cr&#237;ticos como construtores padr&#227;o do tipo base | Microsoft Docs"
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
  - "CA2132"
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2132: os construtores padr&#227;o devem ser pelo menos cr&#237;ticos como construtores padr&#227;o do tipo base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|  
|CheckId|CA2132|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
> [!NOTE]
>  Esse aviso é aplicado somente ao código que está executando o CoreCLR \(a versão do CLR que é específica para aplicativos Web do Silverlight\).  
  
## Causa  
 O atributo de transparência do construtor padrão de uma classe derivada não é tão importante quanto a transparência da classe base.  
  
## Descrição da Regra  
 Os tipos e os membros que têm <xref:System.Security.SecurityCriticalAttribute> não podem ser usados pelo código de aplicativo do Silverlight.  Os tipos de segurança importantes e os membros podem ser usados apenas pelo código de confiança no.NET Framework para a biblioteca de classes do Silverlight.  Como um público ou uma construção seguras em uma classe derivada devem ter o mesmo ou a transparência maior que a sua classe base, uma classe em um aplicativo não pode ser derivada de uma SecurityCritical marcado classe.  
  
 Para o código da plataforma de CoreCLR, se um tipo de base tem um construtor público ou padrão não transparente protegido no tipo derivado deve obedecer as regras padrão de herança de construtor.  O tipo derivado também deve ter um construtor padrão e o construtor deve ser pelo menos crítico como o construtor padrão do tipo de base.  
  
## Como Corrigir Violações  
 Para corrigir a violação, remova o tipo ou não o derivar do tipo não transparente de segurança.  
  
## Quando Suprimir Alertas  
 Não suprima avisos desta regra.  As violações desta regra pelo código de aplicativo resultarão na CoreCLR que não permite carregar o tipo com <xref:System.TypeLoadException>.  
  
### Código  
 [!CODE [FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2132.defaultconstructorsmusthaveconsistenttransparency#1)]  
  
### Comentários