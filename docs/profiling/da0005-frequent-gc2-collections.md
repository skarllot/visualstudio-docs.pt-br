---
title: "DA0005: cole&#231;&#245;es de GC2 frequentes | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0005"
  - "vs.performance.rules.DAManyGC2Collections"
  - "vs.performance.5"
  - "vs.performance.rules.DA0005"
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0005: cole&#231;&#245;es de GC2 frequentes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|RuleId|DA0005|  
|Categoria|uso do .NET Framework|  
|Método de criação de perfil|Memória de .NET|  
|Message \(Mensagem\)|Muitos dos objetos estão sendo coletados na coleta de lixo de geração 2.|  
|Tipo de mensagem|Aviso|  
  
## Causa  
 Um número elevado de objetos de memória do .NET está sendo recuperado na coleta de lixo de geração 2.  
  
## Descrição da Regra  
 Microsoft .NET framework Common Language Runtime \(CLR\) fornece um mecanismo automático de gerenciamento de memória que use um coletor de lixo para recuperar a memória dos objetos que o aplicativo já não usa.  O coletor de lixo geração\- é orientado por, com base na suposição que muitas alocações sejam efêmeros.  As variáveis locais, por exemplo, devem ser breves.  Inicie o recém\-criado de objetos na geração gen 0 \(0\), e em andamento para a geração 1 quando sobrevive a uma execução de coleta de lixo, e transições finalmente a geração 2 se o aplicativo ainda o usa.  
  
 Os objetos da geração 0 são coletados com frequência e geralmente muito eficiente.  Os objetos da geração 1 são coletados com menos frequência e menos eficiente.  Finalmente, os objetos duradouros na geração 2 devem ser coletados mesmo com menos frequência.  A coleção de geração 2, que é uma execução completa de coleta de lixo, também é a operação mais cara.  
  
 Esta regra é disparada quando proporcional coletas de lixo muitos de geração 2 ocorreram.  Se objetos breves relativamente muitos sobrevivem à coleção de geração 1 mas podem ser coletado em uma coleção completa de geração 2, o custo de gerenciamento de memória podem se tornar facilmente excessivos.  Para [crise de vida intermediária](http://go.microsoft.com/fwlink/?LinkId=177835) obter mais informações, veja a postagem em boatos de desempenho do Mariani Rico no site do MSDN.  
  
## Como investigar um aviso  
 Revise os relatórios de [Exibições de dados da memória do .NET](../profiling/dotnet-memory-data-views.md) para entender o padrão do aplicativo de alocação de memória.  Use [Exibição do tempo de vida do objeto](../profiling/object-lifetime-view.md) para determinar qual dos objetos de dados do programa são sobrevivendo na geração 2 e depois sendo recuperado de lá.  Use [Exibição de alocações](../profiling/dotnet-memory-allocations-view.md) para determinar o caminho de execução que resultou nestas alocações.  
  
 Para obter informações sobre como melhorar o desempenho de coleta de lixo, consulte [Noções básicas do coletor de lixo e dicas de desempenho](http://go.microsoft.com/fwlink/?LinkId=148226) no site da Microsoft.  Para obter informações sobre a sobrecarga de coleta de lixo automática, consulte [Heap de descoberto objeto grande](http://go.microsoft.com/fwlink/?LinkId=177836).