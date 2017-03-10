---
title: "CA1410: os m&#233;todos de registro COM devem ser correspondentes | Microsoft Docs"
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
  - "CA1410"
  - "ComRegistrationMethodsShouldBeMatched"
helpviewer_keywords: 
  - "CA1410"
  - "ComRegistrationMethodsShouldBeMatched"
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1410: os m&#233;todos de registro COM devem ser correspondentes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldBeMatched|  
|CheckId|CA1410|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um tipo declara um método marcado com o atributo de <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> mas não declara um método marcado com o atributo de <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> , ou vice\-versa.  
  
## Descrição da Regra  
 Para que os clientes do Component Object Model \(COM\) para criar um tipo de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] , o tipo deve primeiro ser registrado.  Se estiver disponível, um método marcado com o atributo de <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> é chamado durante o processo de registro para executar código especificado pelo usuário.  Um método de correspondência que é marcado com o atributo de <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> é chamado durante o processo de unregistration para inverter as operações do método do registro.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, adicione o método de correspondência de registro ou de unregistration.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo que viola a regra.  O código a seguir mostra como comentário a correção da violação.  
  
 [!code-cs[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]  
  
## Regras Relacionadas  
 [CA1411: os métodos de registro COM não devem estar visíveis](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)  
  
## Consulte também  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Registrando assemblies com o COM](../Topic/Registering%20Assemblies%20with%20COM.md)   
 [Regasm.exe \(Ferramenta de Registro de Assembly\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)