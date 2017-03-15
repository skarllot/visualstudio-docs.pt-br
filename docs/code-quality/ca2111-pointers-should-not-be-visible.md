---
title: "CA2111: os ponteiros n&#227;o devem estar vis&#237;veis | Microsoft Docs"
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
  - "PointersShouldNotBeVisible"
  - "CA2111"
helpviewer_keywords: 
  - "CA2111"
  - "PointersShouldNotBeVisible"
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2111: os ponteiros n&#227;o devem estar vis&#237;veis
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PointersShouldNotBeVisible|  
|CheckId|CA2111|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um público ou <xref:System.IntPtr?displayProperty=fullName> protegido ou um campo de <xref:System.UIntPtr?displayProperty=fullName> não são somente leitura.  
  
## Descrição da Regra  
 <xref:System.IntPtr> e <xref:System.UIntPtr> do ponteiro são os tipos que são usados para acessar a memória não gerenciado.  Se um ponteiro não será privado, interno, ou somente leitura, o código mal\-intencionado pode alterar o valor do ponteiro, potencialmente permitindo o acesso aos locais arbitrários na memória ou fazendo com que o aplicativo ou falhas do sistema.  
  
 Se você pretende proteger o acesso ao tipo que contém o campo do ponteiro, consulte [CA2112: os tipos seguros não devem expor campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md).  
  
## Como Corrigir Violações  
 Proteger o ponteiro fazendo o somente leitura, interno, ou particular.  
  
## Quando Suprimir Alertas  
 Suprima um aviso dessa regra se você não depende do valor do ponteiro.  
  
## Exemplo  
 O código a seguir mostra os ponteiros que violam e satisfazem a regra.  Observe que os ponteiros não existe também violam a regra [CA1051: não declarar campos de instância visíveis](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).  
  
 [!code-cs[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]  
  
## Regras Relacionadas  
 [CA2112: os tipos seguros não devem expor campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA1051: não declarar campos de instância visíveis](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## Consulte também  
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>