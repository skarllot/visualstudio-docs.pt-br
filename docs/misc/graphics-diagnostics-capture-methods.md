---
title: "M&#233;todos de captura do diagn&#243;stico de gr&#225;ficos | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea21995d-0241-412e-8f62-600c3794247f
caps.latest.revision: 2
caps.handback.revision: 2
ms.author: "mithom"
manager: "douge"
---
# M&#233;todos de captura do diagn&#243;stico de gr&#225;ficos
Insira a introdução aqui.  
  
## Métodos de captura  
 No [!INCLUDE[win81](../debugger/includes/win81_md.md)], o tempo de execução do DirectX 11.2 pode capturar informação de gráficos internamente em nome de ferramentas de depuração, como diagnósticos de gráficos; isso é conhecido como *captura robusta*.  Antes de ser incluído esse suporte no tempo de execução do DirectX, as informações de gráficos eram capturadas interceptando determinadas chamadas de função do DirectX para registrar argumentos e outras informações antes de encaminhar as chamadas para o DirectX para serem concluídas; isso é chamado de *captura legada*.  
  
 Como o tempo de execução do DirectX assume a responsabilidade exclusiva por capturar informações de gráficos no [!INCLUDE[win81](../debugger/includes/win81_md.md)], não há necessidade de atualizar a captura legada para oferecer suporte ao DirectX 11.2 e, portanto, a captura legada é preterida.  No entanto, como o tempo de execução do DirectX 11.2 não tem suporte a versões do Windows anteriores ao [!INCLUDE[win81](../debugger/includes/win81_md.md)], o [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] ainda oferece suporte à captura legada para aplicativos destinados a [!INCLUDE[win8](../debugger/includes/win8_md.md)] e [!INCLUDE[win7](../debugger/includes/win7_md.md)].  
  
 Os dois métodos registram informações semelhantes e não mudam o modo como as informações de gráficos são capturadas, nem usam as ferramentas de Diagnósticos de Gráficos.  
  
### Captura robusta  
 A captura robusta tem suporte a diagnósticos de gráfico do [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] no [!INCLUDE[win81](../debugger/includes/win81_md.md)], no [!INCLUDE[winblue_winrt_2](../debugger/includes/winblue_winrt_2_md.md)] e no Windows Phone 8.1.  Oferece suporte a DirectX 10.0 a DirectX 11.2 e é capaz de capturar informações de gráficos sobre novos recursos do Direct3D 11.2 como, por exemplo, alocação dinâmica de recursos.  No entanto, não oferece suporte completo a todos os recursos do Direct3D 11.2. Por exemplo, não é possível depurar um sombreador HLSL que foi criado usando o recurso de vinculação de sombreador HLSL.  A captura robusta usa uma nova API de captura para dar suporte a seus cenários de captura programática.  
  
### Captura legada  
 A captura legada oferece suporte a diagnósticos de gráficos [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] e [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] no [!INCLUDE[win8](../debugger/includes/win8_md.md)], Windows RT 8 e [!INCLUDE[win7](../debugger/includes/win7_md.md)].  Compatível com DirectX 10.0 a DirectX 11.1.  A captura legada não tem suporte a nenhum recurso do Direct3D 11.2 e é preterida, exceto em cenários em que a captura robusta não está disponível.  A captura legada usa a API da captura definida no arquivo do cabeçalho `vsgcapture.h` para dar suporte a seus cenários de captura programática.  Esse tipo de captura programática também é preterida, exceto em cenários em que a captura robusta não está disponível.  
  
## Consulte também  
 [Capturando informações de gráficos](../debugger/capturing-graphics-information.md)   
 [Passo a passo: capturando informações de gráficos](../debugger/walkthrough-capturing-graphics-information.md)