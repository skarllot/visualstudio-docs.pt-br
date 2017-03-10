---
title: "CA1411: os m&#233;todos de registro COM n&#227;o devem estar vis&#237;veis | Microsoft Docs"
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
  - "CA1411"
  - "ComRegistrationMethodsShouldNotBeVisible"
helpviewer_keywords: 
  - "ComRegistrationMethodsShouldNotBeVisible"
  - "CA1411"
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1411: os m&#233;todos de registro COM n&#227;o devem estar vis&#237;veis
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldNotBeVisible|  
|CheckId|CA1411|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um método que é marcado com <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> ou atributo de <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> externamente é visível.  
  
## Descrição da Regra  
 Quando um assembly é registrado em Component Object Model \(COM\), as entradas são adicionadas ao Registro para cada COM\- visível no assembly.  Os métodos que são marcados com os atributos de <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> e de <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> são chamados durante o registro e o unregistration processam, respectivamente, para executar o código do usuário que é específico ao registro\/unregistration desses tipos.  Este código não deve ser chamado fora desses processos.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere a acessibilidade do método a `private` ou a `internal` \(`Friend` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra dois métodos que violam a regra.  
  
 [!code-cs[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]  
  
## Regras Relacionadas  
 [CA1410: os métodos de registro COM devem ser correspondentes](../code-quality/ca1410-com-registration-methods-should-be-matched.md)  
  
## Consulte também  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Registrando assemblies com o COM](../Topic/Registering%20Assemblies%20with%20COM.md)   
 [Regasm.exe \(Ferramenta de Registro de Assembly\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)