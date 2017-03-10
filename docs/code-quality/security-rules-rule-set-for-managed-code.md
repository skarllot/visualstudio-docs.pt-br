---
title: "Conjunto de regras de seguran&#231;a para c&#243;digo gerenciado | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Conjunto de regras de seguran&#231;a para c&#243;digo gerenciado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você deve incluir a regra das regras de segurança do Microsoft definida para maximizar o número de problemas potenciais de segurança que são relatadas.  
  
|Regra|Descrição|  
|-----------|---------------|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Revise consultas SQL para vulnerabilidades de segurança|  
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Exceções non\-CLSCompliant de captura em manipuladores gerais|  
|[CA2103](../code-quality/ca2103-review-imperative-security.md)|Segurança de revisão obrigatório|  
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Não declarar tipos mutáveis somente leitura de referência|  
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Os campos de matriz não devem ser somente leitura|  
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Afirma Seguro|  
|[CA2107](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|A revisão deny e só permitir o uso|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Segurança declarativa revisão em tipos de valor|  
|[CA2109](../code-quality/ca2109-review-visible-event-handlers.md)|Manipuladores de eventos visíveis revisão|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Os ponteiros não devem ser visíveis|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Os tipos não seguros deve expor campos|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|A segurança do método deve ser um superconjunto do tipo|  
|[CA2115](../Topic/CA2115:%20Call%20GC.KeepAlive%20when%20using%20native%20resources.md)|Chame GC.KeepAlive ao usar recursos nativos|  
|[CA2116](../Topic/CA2116:%20APTCA%20methods%20should%20only%20call%20APTCA%20methods.md)|Os métodos de APTCA só devem chamar métodos de APTCA|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Os tipos de APTCA só devem estender tipos de base de APTCA|  
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|Uso de SuppressUnmanagedCodeSecurityAttribute revisão|  
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Métodos do selo que satisfazem interfaces privadas|  
|[CA2120](../Topic/CA2120:%20Secure%20serialization%20constructors.md)|Construtores de serialização seguros|  
|[CA2121](../Topic/CA2121:%20Static%20constructors%20should%20be%20private.md)|Os construtores estáticos devem ser privados|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Não expõe métodos indiretamente com as demandas de link|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|As demandas do link de substituição devem ser idênticas com base|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Cláusulas vulneráveis de quebra automática finalmente tente externa|  
|[CA2126](../Topic/CA2126:%20Type%20link%20demands%20require%20inheritance%20demands.md)|As demandas do link do tipo exigem demandas de herança|  
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|As constantes críticos de segurança devem ser transparentes|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Os tipos críticos de segurança não podem participar da equivalência do tipo|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Os construtores padrão devem ser pelo menos críticos quanto construtores padrão do tipo de base|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|O delega devem associar a transparência consistente com métodos|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Os métodos devem manter a transparência consistente ao substituir métodos de base|  
|[CA2135](../Topic/CA2135:%20Level%202%20assemblies%20should%20not%20contain%20LinkDemands.md)|Os assemblies de nível 2 não devem conter LinkDemands|  
|[CA2136](../Topic/CA2136:%20Members%20should%20not%20have%20conflicting%20transparency%20annotations.md)|Os membros não devem ter conflitantes anotações de transparência|  
|[CA2137](../Topic/CA2137:%20Transparent%20methods%20must%20contain%20only%20verifiable%20IL.md)|Os métodos transparentes devem conter apenas o IL verificável|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Os métodos transparentes não devem chamar métodos com o atributo de SuppressUnmanagedCodeSecurity|  
|[CA2139](../Topic/CA2139:%20Transparent%20methods%20may%20not%20use%20the%20HandleProcessCorruptingExceptions%20attribute.md)|Os métodos transparentes não podem usar o atributo de HandleProcessCorruptingExceptions|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|O código transparente não deve referenciar itens críticos de segurança|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Os métodos transparentes não devem satisfazer LinkDemands|  
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|O código transparente não deve ser protegido com LinkDemands|  
|[CA2143](../Topic/CA2143:%20Transparent%20methods%20should%20not%20use%20security%20demands.md)|Os métodos transparentes não devem usar as demandas de segurança|  
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|O código transparente não deve carregar os assemblies das matrizes de bytes|  
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Os métodos transparentes não devem ser decorados com o SuppressUnmanagedCodeSecurityAttribute|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Os tipos devem ser pelo menos críticos quanto os tipos de base e interfaces|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Os métodos transparentes não podem usar segurança afirmam|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Os métodos transparentes não devem chamar em código nativo|  
|[CA2210](../Topic/CA2210:%20Assemblies%20should%20have%20valid%20strong%20names.md)|Os assemblies devem ter nomes fortes válidos|