---
title: "CA1903: usar apenas a API da estrutura de destino | Microsoft Docs"
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
  - "UseOnlyAPIFromTargetedFramework"
  - "CA1903"
helpviewer_keywords: 
  - "CA1903"
  - "UseOnlyApiFromTargetedFramework"
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1903: usar apenas a API da estrutura de destino
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseOnlyApiFromTargetedFramework|  
|CheckId|CA1903|  
|Categoria|Microsoft.Portability|  
|Alteração Significativa|Interromper \- quando é acionado na assinatura de um membro ou de um tipo externamente visível.<br /><br /> Interrompendo não \- quando é acionado no corpo de um método.|  
  
## Causa  
 Um membro ou um tipo está usando um membro ou um tipo que foram introduzidos em um pacote de serviços que não é incluído com a estrutura de destino do projeto.  
  
## Descrição da Regra  
 Os novos membros e os tipos foram incluídos no .NET Framework 2.0 Service Pack 1 e 2, o.NET Framework 3.0 Service Pack 1 e 2, e o.NET Framework 3.5 Service Pack 1.  Os projetos que visam versões principais do .NET Framework podem querer fazer dependências nesses novos APIs.  Para evitar essa dependência, esta regra é acionado em usos de quaisquer novos membros e tipos que não sejam incluídos por padrão na estrutura de destino do projeto.  
  
 **Estrutura de destino e dependências do Service Pack**  
  
|||  
|-|-|  
|Quando a estrutura de destino esteja|É acionado em utilização dos membros apresentados em|  
|.NET Framework 2.0|o.NET Framework 2.0 SP1, o .NET Framework 2.0 SP2|  
|.NET Framework 3.0|FRAMEWORK .NET 2.0 SP1, FRAMEWORK .NET 2.0 SP2, FRAMEWORK .NET 3.0 SP1, FRAMEWORK .NET 3.0 SP2|  
|.NET Framework 3.5|.NET Framework 3.5 SP1|  
|.NET Framework 4|N\/D|  
  
 Para alterar a estrutura de destino de um projeto, consulte [Direcionamento de uma versão específica do .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
## Como Corrigir Violações  
 Para remover a dependência no service pack, remova todos os usos do novo membro ou linear.  Se esta é uma dependência deliberada, ou suprimir o aviso ou cancelar esta regra.  
  
## Quando Suprimir Alertas  
 Não suprima um aviso dessa regra se essa não é uma dependência deliberada no pacote de serviços especificado.  Nessa situação, o aplicativo pode não é executado em sistemas sem este service pack instalado.  Suprimir o aviso ou desconectar essa regra se essa fosse uma dependência deliberada.  
  
## Exemplo  
 O exemplo a seguir mostra uma classe que usa o tipo DateTimeOffset que só está disponível no .NET 2.0 Service Pack 1.  Este exemplo requer que o .NET Framework 2.0 esteve selecionado na lista suspensa da estrutura de destino nas propriedades do projeto.  
  
 [!code-cs[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]  
  
## Exemplo  
 O exemplo a seguir corrige a violação previamente descrita substituindo pelo tipo de DateTimeOffset com o tipo DateTime.  
  
 [!code-cs[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]  
  
## Consulte também  
 [Avisos de portabilidade](../code-quality/portability-warnings.md)   
 [Direcionamento de uma versão específica do .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)