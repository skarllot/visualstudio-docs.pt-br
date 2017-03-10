---
title: "CA2147: os m&#233;todos transparentes talvez n&#227;o usem declara&#231;&#245;es de seguran&#231;a | Microsoft Docs"
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
  - "SecurityTransparentCodeShouldNotAssert"
  - "CA2147"
  - "CA2128"
helpviewer_keywords: 
  - "CA2128"
  - "SecurityTransparentCodeShouldNotAssert"
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2147: os m&#233;todos transparentes talvez n&#227;o usem declara&#231;&#245;es de seguran&#231;a
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecurityTransparentCodeShouldNotAssert|  
|CheckId|CA2147|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Código que é marcado como <xref:System.Security.SecurityTransparentAttribute> não é concedido permissões suficientes para declarar.  
  
## Descrição da Regra  
 Esta regra analisa todos os métodos e em um assembly que é 100%\/transparentes críticos transparentes ou mistos, e sinaliza o usam declarativo ou obrigatório de <xref:System.Security.CodeAccessPermission.Assert%2A>.  
  
 Em tempo de execução, todas as chamadas a <xref:System.Security.CodeAccessPermission.Assert%2A> de código transparente causarão <xref:System.InvalidOperationException> a ser lançado.  Isso pode ocorrer em ambos os assemblies transparentes 100%, e também assemblies transparentes\/críticos mistos onde um método ou um tipo são declarados transparente, mas inclui um declarativo ou obrigatório declarar.  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2,0 introduziu um recurso nomeado *transparência*.  Os métodos individuais, os campos, as interfaces, as classes, e tipos podem ser transparentes ou críticos.  
  
 O código transparente não é permitido elevar privilégios de segurança.  Como consequência, todas as permissões concedidas ou exigidas ele são transmitidas automaticamente com o código ao domínio de aplicativo do chamador ou host.  Os exemplos das subam incluem afirmam, LinkDemands, SuppressUnmanagedCode, e código de `unsafe` .  
  
## Como Corrigir Violações  
 Para resolver o problema, uma ou outra marca o código que chama declarar com <xref:System.Security.SecurityCriticalAttribute>, ou remove uma declaração.  
  
## Quando Suprimir Alertas  
 Não suprima uma mensagem desta regra.  
  
## Exemplo  
 Este código falhará se `SecurityTestClass` é transparente, quando o método de `Assert` gerencie <xref:System.InvalidOperationException>.  
  
 [!CODE [FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts#1)]  
  
## Exemplo  
 Uma opção é a revisão de código do método de SecurityTransparentMethod no exemplo abaixo, e se o método é considerado seguro para a alto, identificar SecurityTransparentMethod por meio de Seguro\- crítico isso exige que uma auditoria de segurança, completo e detalhado, sem erros deve ser executado no método junto com todas as atendimento\- saída que ocorram no método em uma declaração:  
  
 [!CODE [FxCop.Security.SecurityTransparentCode2#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2#1)]  
  
 Outra opção é remover uma declaração de código, e permite que qualquer fluxo de demandas subsequente de permissão de E\/S de arquivo além de SecurityTransparentMethod ao chamador.  Isso habilita verificações de segurança.  Nesse caso, nenhum auditoria de segurança é necessário em geral, como as demandas de permissão fluirão ao chamador e\/ou ao domínio de aplicativo.  Exigências de permissão são bastante \- controlado com a política de segurança, o ambiente de hospedagem, e as concessões de permissão de código de origem.  
  
## Consulte também  
 [Avisos de segurança](../code-quality/security-warnings.md)