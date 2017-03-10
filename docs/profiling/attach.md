---
title: "Anexar | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Anexar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A opção de VSPerfCmd.exe **Attach** iniciar a criação de perfil de exemplo do processo em execução especificado pela ID do processo \(PID\).  
  
 Para usar a opção de **Attach** , você deve especificar o método de **Sample** na opção de início.  
  
> [!NOTE]
>  Se a opção de **Start** foi especificada com a opção de **Crosssession** , todas as chamadas a **VSPerfCmd \/Attach** ou a **VSPerfCmd \/Detach** deve também especificar **Crosssession**.  
  
## Sintaxe  
  
```  
VSPerfCmd.exe /Attach:ProcessID [Options]  
```  
  
#### Parâmetros  
 `ProcessID`  
 A ID de O processo \(PID\) do processo em execução.  O PID de um processo em execução é listado na guia os processos do gerenciador de tarefas do windows.  
  
## Opções válidas  
 As seguintes opções de **VSPerfCmd** podem ser combinadas com a opção de **Attach** em uma única linha de comando.  
  
 **Crosssession**  
 Permite analisar aplicativos nas sessões diferentes da sessão de logon.  Obrigatório se a opção de **Start** foi especificada com a opção de **Crosssession** .  
  
 **Start:** `Method`  
 Inicializa a sessão do profiler de linha de comando e defina o método analisando especificado.  
  
 **TargetCLR**  
 Especifica a versão do .NET Framework Common Language Runtime \(CLR\) para analisar quando mais de uma versão é carregada em uma sessão analisando.  Por padrão, a primeira versão carregada é analisado.  
  
 **GlobalOn GlobalOff**  
 Os resumos \(**GlobalOn**\) ou as pausas \(\)**GlobalOff**criação de perfil, mas não terminam a sessão analisando.  
  
 **ProcessOn:** `PID` **ProcessOff:** `PID`  
 Resumos**ProcessOn**\(\) ou pausa \(\)**ProcessOff**criação de perfil para o processo especificado.  
  
## Opções de intervalo  
 Uma das opções de intervalo de amostragem pode ser especificado na linha de comando anexar.  O intervalo de amostragem padrão é 10.000.000 ciclos do relógio do processador.  
  
 **Timer**\[**:**`Cycles`\]**PF**\[**:**`Events`\]**Sys**eventos \[\]**Counter**de**:**\[**:**`Name`,`Reload`,`FriendlyName`\]  
 Especifica o número e o tipo de intervalo de amostragem.  
  
-   **Timer** \- Exemplos ciclos de cada relógio do processador de `Cycles` .  Se `Cycles` não for especificado, 10.000.000 ciclos são usados.  
  
-   **PF** \- Exemplos falhas de cada página de `Events` .  Se `Events` não for especificado, 10 falhas de página são usadas.  
  
-   **Sys** \- Exemplos de cada chamadas de `Events` o sistema operacional.  Se `Events` não for especificado, 10 chamadas do sistema são usados.  
  
-   **Counter** \- Exemplos de cada número de `Reload` do contador de desempenho de CPU especificado por `Name`.  Opcionalmente, `FriendlyName` pode especificar uma cadeia de caracteres para usar como o cabeçalho da coluna no profiler relatórios.  
  
## Exemplo  
 Este exemplo demonstra como anexar a uma instância em execução de um aplicativo com a ID de processo de 12345.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Attach:12345  
```  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)