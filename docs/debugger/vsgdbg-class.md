---
title: "Classe VsgDbg | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Classe VsgDbg
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Representa uma interface para o controle programático do componente do aplicativo de diagnóstico de gráficos.  
  
## Sintaxe  
  
```cpp  
class VsgDbg;  
```  
  
## Membros  
 A classe de `VsgDbg` oferece suporte aos seguintes membros.  
  
### Construtores Públicos  
  
|Nome|Descrição|  
|----------|---------------|  
|[VsgDbg::VsgDbg \(Construtor\)](../Topic/VsgDbg::VsgDbg%20\(Constructor\).md)|Constrói uma instância da classe de `VsgDbg` e prepara o componente do aplicativo de diagnóstico de gráficos para capturar e registrar ativamente informações de gráficos.|  
|[VsgDbg::~VsgDbg \(Destruidor\)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|Destrói uma instância da classe de `VsgDbg` .|  
  
### Métodos Públicos  
  
|Nome|Descrição|  
|----------|---------------|  
|[AddMessage](../debugger/addmessage.md)|Adiciona uma mensagem personalizada a diagnósticos HUD dos gráficos \(exibição de início \- Acima\).|  
|[BeginCapture](../debugger/begincapture.md)|Inicia um intervalo de captura que termina com `EndCapture`.|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|Captura o restante do quadro atual no arquivo de log dos gráficos.|  
|[Copiar \(captura programática\)](../debugger/copy-programmatic-capture.md)|Copia o conteúdo dos gráficos ativas registra o arquivo \(.vsglog\) em um arquivo novo.|  
|[EndCapture](../debugger/endcapture.md)|Termina um intervalo de captura que é iniciado com `BeginCapture`.|  
|[Init](../debugger/init.md)|Prepara o componente do aplicativo de diagnóstico de gráficos para capturar e registrar ativamente informações de gráficos.|  
|[ToggleHUD](../debugger/togglehud.md)|Ativa o \/desativar ou desativado coberto HUD de diagnóstico de gráficos.|  
|[UnInit](../debugger/uninit.md)|Encerra o arquivo de log de gráficos, fechá\-lo e, libera os recursos usados quando o aplicativo gravava ativamente informações de gráficos.|  
  
## Comentários  
 A classe de `VsgDbg` representa uma interface que você pode usar para controlar programaticamente recursos de diagnóstico de gráficos.  Você pode usar alguns recursos mesmo quando você estiver ativa não capturando e não registrar informações dos gráficos; isso inclui a função de membro de `AddMessage` e a função de membro de `ToggleHUD` .  As outras funções de membro ao preparar o componente do aplicativo de diagnóstico de gráficos para iniciar ou parar a captura ativa de informações de gráficos, ou devem ser chamadas quando o aplicativo é ativamente capturar e registrar informações dos gráficos em um arquivo de log dos gráficos.