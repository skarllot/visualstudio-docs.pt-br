---
title: "CA2151: campos com tipos cr&#237;ticos devem ser cr&#237;ticos para seguran&#231;a | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09db9d25-7d58-4725-a252-4a07baadf046
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2151: campos com tipos cr&#237;ticos devem ser cr&#237;ticos para seguran&#231;a
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName||  
|CheckId|CA2151|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um campo transparente de segurança ou um campo de segurança crítica é declarado.  O tipo é especificado como de segurança crítica.  Por exemplo:  
  
```c#  
[assembly: AllowPartiallyTrustedCallers]  
  
   [SecurityCritical]  
   class Type1 { } // Security Critical type  
  
   class Type2 // Security transparent type  
   {  
      Type1 m_field; // CA2151, transparent field of critical type  
   }  
  
```  
  
 Neste exemplo, `m_field` é um campo transparente de segurança de um tipo de segurança crítica.  
  
## Descrição da Regra  
 Para usar tipos de segurança crítica, o código que faz referência ao tipo deve ser de segurança crítica ou de segurança crítica segura.  Isso será verdadeiro mesmo que a referência seja indireta.  Por exemplo, ao fazer referência a um campo transparente de tipo crítico, o código deve ser de segurança crítica ou de segurança.  Por isso, ter um campo de segurança transparente ou de segurança crítica é enganoso porque o código transparente continuará incapaz de acessar o campo.  
  
## Como Corrigir Violações  
 Para corrigir uma violação dessa regra, marque o campo com o atributo <xref:System.Security.SecurityCriticalAttribute> ou crie o tipo referenciado pela segurança transparente ou crítica do campo.  
  
```c#  
// Fix 1: Make the referencing field security critical  
[assembly: AllowPartiallyTrustedCallers]  
  
   [SecurityCritical]  
   class Type1 { } // Security Critical type  
  
   class Type2 // Security transparent type  
   {  
      [SecurityCritical]  
      Type1 m_field; // Fixed: critical type, critical field  
   }  
  
// Fix 2: Make the referencing field security critical  
[assembly: AllowPartiallyTrustedCallers]  
  
   class Type1 { } // Type1 is now transparent  
  
   class Type2 // Security transparent type  
   {  
      [SecurityCritical]  
      Type1 m_field; // Fixed: critical type, critical field  
   }  
  
```  
  
## Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
### Código  
 [!code-cs[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2151-fields-with-critical-types-should-be-security-critical_1.cs)]  
  
### Comentários