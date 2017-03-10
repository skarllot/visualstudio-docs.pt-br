---
title: "Depura&#231;&#227;o e o processo de hospedagem | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurando [Visual Studio], processo de hospedagem"
  - "processo de hospedagem"
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depura&#231;&#227;o e o processo de hospedagem
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O processo de hospedagem do Visual Studio melhora o desempenho do depurador e habilita novos recursos do depurador, como a avaliação da expressão de tempo de design e depuração de confiança parcial. Se for necessário, você pode desabilitar o processo de hospedagem. Para obter mais informações, consulte [Como desabilitar o processo de hospedagem](../ide/how-to-disable-the-hosting-process.md). As seções a seguir descrevem algumas diferenças entre depuração com e sem o processo de hospedagem.  
  
## Depuração de confiança parcial e clique em\-segurança de uma vez  
 Depuração de confiança parcial requer o processo de hospedagem. Se você desabilitar o processo de hospedagem, depuração de confiança parcial não funcionará mesmo que a segurança de confiança parcial é habilitada no **segurança** página de **Propriedades do projeto**. Para obter mais informações, consulte [Como desabilitar o processo de hospedagem](../ide/how-to-disable-the-hosting-process.md) e [Como depurar um aplicativo parcialmente confiável](../debugger/how-to-debug-a-partial-trust-application.md).  
  
## Avaliação de expressão de tempo de design  
 Expressão de tempo de design sempre usa o processo de hospedagem. Desabilitar a hospedagem processar o **Propriedades do projeto** desabilita a avaliação da expressão de tempo de design para projetos de biblioteca de classes. Para outros tipos de projeto, a avaliação da expressão de tempo de design não está desabilitada. Em vez disso, o Visual Studio inicia o executável real e usa\-o para avaliação do tempo de design sem o processo de hospedagem. Essa diferença pode produzir resultados diferentes.  
  
## Diferenças de AppDomain.CurrentDomain.FriendlyName  
 `AppDomain.CurrentDomain.FriendlyName` Retorna resultados diferentes dependendo se o processo de hospedagem está habilitado. Se você chamar `AppDomain.CurrentDomain.FriendlyName` com o processo de hospedagem habilitado, ele retornará *app\_name*`.vhost.exe`. Se você chamar o processo de hospedagem desabilitado, ele retorna *app\_name*`.exe`.  
  
## Assembly.GetCallingAssembly\(\). Diferenças de FullName  
 `Assembly.GetCallingAssembly().FullName` Retorna resultados diferentes dependendo se o processo de hospedagem está habilitado. Se você chamar `Assembly.GetCallingAssembly().FullName` com o processo de hospedagem habilitado, ele retornará `mscorlib`. Se você chamar `Assembly.GetCallingAssembly().FullName` com o processo de hospedagem desabilitado, ele retornará o nome do aplicativo.  
  
## Consulte também  
 [Processo de hospedagem \(vshost.exe\)](../ide/hosting-process-vshost-exe.md)   
 [Como depurar um aplicativo parcialmente confiável](../debugger/how-to-debug-a-partial-trust-application.md)   
 [Como desabilitar o processo de hospedagem](../ide/how-to-disable-the-hosting-process.md)