---
title: "CA2107: revisar uso de deny e permit only | Microsoft Docs"
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
  - "CA2107"
  - "ReviewDenyAndPermitOnlyUsage"
helpviewer_keywords: 
  - "ReviewDenyAndPermitOnlyUsage"
  - "CA2107"
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2107: revisar uso de deny e permit only
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewDenyAndPermitOnlyUsage|  
|CheckId|CA2107|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um método contém uma verificação de segurança que especifica a ação de segurança de PermitOnly ou Deny.  
  
## Descrição da Regra  
 As ações de segurança de [Using the PermitOnly Method](http://msdn.microsoft.com/pt-br/8c7bdb7f-882f-45b7-908c-6cbaa1767649) e de <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> só deve ser usada pelas que têm um conhecimento avançado de segurança de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] .  O código que usa essas ações de segurança deve passar pela revisão de segurança.  
  
 Negar altera o comportamento padrão de exames da pilha que ocorre em resposta a uma pesquisa de segurança.  Permite especificar as permissões que não devem ser concedidas para a duração do método negando, independentemente das permissões reais dos chamadores na pilha de chamadas.  Se a exames da pilha detecta um método que esteja protegido Deny, e se a permissão necessária é incluída nas permissões negado, a exames da pilha falha.  PermitOnly também altera o comportamento padrão de exames de pilha.  Permite que o código especifica apenas as permissões que podem ser concedidas, independentemente das permissões dos chamadores.  Se a exames da pilha detecta um método que esteja protegido por PermitOnly, e se a permissão necessária não é incluída nas permissões que são especificadas por PermitOnly, a exames da pilha falha.  
  
 O código que depende dessas ações deve ser cuidadosamente avaliado para vulnerabilidades de segurança devido à sua utilidade limitada e comportamento sutil.  Considere o seguinte:  
  
-   [Demandas de link](../Topic/Link%20Demands.md) não é afetado Deny ou por PermitOnly.  
  
-   Se negar ou o PermitOnly ocorrem no mesmo quadro de pilhas que a demanda que causa a exames da pilha, as ações de segurança não têm nenhum efeito.  
  
-   Os valores que são usados para construir permissões baseadas em geral caminho\- podem ser especificados em várias maneiras.  Negar acesso a um formulário de caminho não nega acesso a todos os formulários.  Por exemplo, se \\ de compartilhamento de arquivos servidor \\ \\ share é mapeado para uma unidade de rede X: , para negar acesso a um arquivo no compartilhamento, você deve negar servidor \\ \\ \\ share \\ Arquivo, X:\\File e todos os outros caminho que acessa o arquivo.  
  
-   <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> pode finalizar uma exames de pilha antes que negar ou o PermitOnly seja alcançado.  
  
-   Deny se tiver qualquer efeito, isto é, quando um chamador tem uma permissão que está bloqueada negar, o chamador pode acessar o recurso protegido diretamente, ignorando negar.  Da mesma forma, se o chamador não tiver a permissão negada, a exames da pilha falharia sem negar.  
  
## Como Corrigir Violações  
 O uso dessas ações causar uma violação de segurança.  Para corrigir uma violação, não use estas ações de segurança.  
  
## Quando Suprimir Alertas  
 Suprima um aviso desta regra somente depois que você concluir uma análise de segurança.  
  
## Exemplo  
 O exemplo a seguir demonstra algumas restrições Deny.  
  
 A seguinte biblioteca contém uma classe que tem dois métodos que são idênticos com exceção das demandas de segurança que as protegem.  
  
 [!CODE [FxCop.Security.PermitAndDeny#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny#1)]  
  
## Exemplo  
 O aplicativo seguir demonstra os efeitos Deny os métodos seguros de biblioteca.  
  
 [!code-cs[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]  
  
 O exemplo produz a seguinte saída.  
  
  **Procura: Deny do chamador não tem nenhum efeito sob demanda com a permissão declarada.**  
**LinkDemand: Deny do chamador não tem nenhum efeito em LinkDemand com a permissão declarada.**  
**LinkDemand: Deny do chamador não tem nenhum efeito com o código LinkDemand\- protegido.**  
**LinkDemand: Este Deny não tem nenhum efeito com o código LinkDemand\- protegido.**   
## Consulte também  
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>   
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>   
 [Diretrizes de codificação segura](../Topic/Secure%20Coding%20Guidelines.md)   
 [Overriding Security Checks](http://msdn.microsoft.com/pt-br/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [Using the PermitOnly Method](http://msdn.microsoft.com/pt-br/8c7bdb7f-882f-45b7-908c-6cbaa1767649)