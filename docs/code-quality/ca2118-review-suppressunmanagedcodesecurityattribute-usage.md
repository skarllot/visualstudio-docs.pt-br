---
title: "CA2118: revisar uso de SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs"
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
  - "CA2118"
  - "ReviewSuppressUnmanagedCodeSecurityUsage"
helpviewer_keywords: 
  - "CA2118"
  - "ReviewSuppressUnmanagedCodeSecurityUsage"
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2118: revisar uso de SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|  
|CheckId|CA2118|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um público ou um tipo ou membro protegido têm o atributo de <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> .  
  
## Descrição da Regra  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> altera o comportamento do sistema de segurança padrão para os membros que executam código não gerenciado usando o interoperabilidade COM ou a invocação de preparo.  Em geral, o sistema faz [Dados e modelagem](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md) para a permissão de código não gerenciado.  Essa solicitação ocorre em tempo de execução para cada invocação de membro, e verifica todo o chamador na pilha de chamadas para a permissão.  Quando o atributo estiver presente, o sistema faz [Demandas de link](../Topic/Link%20Demands.md) para a permissão: as permissões do chamador imediata são verificadas quando o chamador JIT\- é criado.  
  
 Este atributo é usado principalmente para aumentar o desempenho; no entanto, os ganhos de desempenho vêm com riscos de segurança significativos.  Se você colocar o atributo nos membros públicos que chamam métodos nativos, os chamadores na pilha de chamadas \(diferente do chamador imediata\) não precisam da permissão de código não gerenciado executar o código não gerenciado.  Dependendo das ações e a manipulação de entrada do membro público, pode permitir que os chamadores untrustworthy acessar a funcionalidade limitada normalmente ao código confiável.  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] confia em verificações de segurança para impedir que os chamadores ganhem acesso direto ao espaço de endereço atual do processo.  Como esse atributo ignora a segurança normal, o código gerará uma ameaça registra se pode ser usado para ler ou gravar na memória do processo.  Observe que o risco não está limitado aos métodos que fornecem intencionalmente o acesso à memória do processo; também está presente em qualquer cenário onde o código mal\-intencionado pode obter acesso por qualquer meio, por exemplo, a entrada surpreendente, danificado, ou inválido de entrega.  
  
 A política de segurança padrão não concede a permissão de código não gerenciado em um assembly a menos que esteja executando no computador local ou membro de um dos seguintes grupos:  
  
-   Meu grupo de códigos de fuso horário do computador  
  
-   Grupo de códigos de nome forte do Microsoft  
  
-   Grupo de códigos de nome forte de ECMA  
  
## Como Corrigir Violações  
 Revise cuidadosamente seu código para garantir que esse atributo seja absolutamente necessário.  Se você não estiver familiarizado com segurança de código gerenciado, ou não inclui as implicações de segurança de uso desse atributo, exclua\-o de seu código.  Se o atributo for necessário, você deve assegurar que os chamadores não pode usar seu código maliciosamente.  Se seu código não tem permissão para executar o código não gerenciado, esse atributo não tem nenhum efeito e deve ser removida.  
  
## Quando Suprimir Alertas  
 Para suprimir com segurança um aviso desta regra, você deve garantir que seu código não fornece chamadores acesso a operações nativos ou para recursos que podem ser usados em uma forma destrutiva.  
  
## Exemplo  
 O exemplo a seguir viola a regra.  
  
 [!code-cs[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]  
  
## Exemplo  
 No exemplo a seguir, o método de `DoWork` fornece um caminho publicamente acessível de código para o método `FormatHardDisk`de invocação da plataforma.  
  
 [!code-cs[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]  
  
## Exemplo  
 No exemplo a seguir, o método público `DoDangerousThing` causar uma violação.  Para resolver a violação, `DoDangerousThing` deve ser feito particular e, o acesso a ele deve ser a um método público protegido por uma procura de segurança, como ilustrado pelo método de `DoWork` .  
  
 [!CODE [FxCop.Security.TypeInvokeAndSuppress#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress#1)]  
  
## Consulte também  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>   
 [Diretrizes de codificação segura](../Topic/Secure%20Coding%20Guidelines.md)   
 [Security Optimizations](http://msdn.microsoft.com/pt-br/cf255069-d85d-4de3-914a-e4625215a7c0)   
 [Dados e modelagem](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)   
 [Demandas de link](../Topic/Link%20Demands.md)