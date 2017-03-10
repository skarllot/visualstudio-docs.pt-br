---
title: "Iniciar | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Iniciar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A opção de **Launch** inicia o profiler usando o método de amostragem e também inicia o aplicativo especificado.  
  
 Para usar a opção de **Launch** , você deve especificar o método de **Sample** na opção de **Start** .  
  
## Sintaxe  
  
```  
VSPerfCmd.exe /Launch:AppName [Options]  
```  
  
#### Parâmetros  
 `AppName`  
 O nome do aplicativo iniciar.  Os caminhos completo e parciais do diretório atual têm suporte.  
  
## Opções válidas  
 As seguintes opções de VSPerfCmd podem ser combinadas com a opção de **Launch** em uma única linha de comando.  
  
 **Start:** `Method`  
 Inicializa a sessão do profiler de linha de comando e defina o método analisando especificado.  
  
 **GlobalOn**e **GlobalOff**  
 Os resumos \(**GlobalOn**\) ou as pausas \(\)**GlobalOff**criação de perfil, mas não terminam a sessão analisando.  
  
 **ProcessOn:** `PID` e **ProcessOff**:`PID`  
 Resumos**ProcessOn**\(\) ou pausa \(\)**ProcessOff**criação de perfil para o processo especificado.  
  
 **TargetCLR**  
 Especifica a versão do .NET Framework Common Language Runtime \(CLR\) para analisar quando mais de uma versão é carregada em uma sessão analisando.  Por padrão, a primeira versão carregada é analisado.  
  
## Opções exclusivas  
 As seguintes opções só podem ser usadas com a opção de **Launch** .  
  
 **Console**  
 Inicia o aplicativo especificado de linha de comando em uma nova janela.  
  
 **Args:** `ArgList`  
 Especifica a lista de argumentos para passar para o aplicativo.  
  
 **LineOff**  
 Desabilita a coleção de dados de perfil de dados de nível.  
  
## Opções de amostragem  
 Uma das opções de intervalo de amostragem pode ser especificado na linha de comando de **Launch** .  O intervalo de amostragem padrão é 10.000.000 ciclos do relógio do processador.  
  
 **Timer**\[**:**`Cycles`\]**PF**\[**:**`Events`\]**Sys**\[**:**`Events`\]**Counter**\[**:**`Name`,`Reload`,`FriendlyName`\]**GC**\[:**allocation**&#124;**lifetime**\]  
 Especifica o número e o tipo de intervalo de amostragem.  
  
-   **Timer** \- Exemplos de cada `Cycles` não paralisou ciclos do relógio do processador.  Se `Cycles` não for especificado, 10.000.000 ciclos são usados.  
  
-   **PF** \- Exemplos falhas de cada página de `Events` .  Se `Events` não for especificado, 10 falhas de página.  
  
-   **Sys** \- Exemplos de cada chamadas de `Events` o sistema operacional.  Se `Events` não for especificado, 10 chamadas do sistema são usados.  
  
-   **Counter** \- Exemplos de cada número de `Reload` do contador de desempenho de CPU especificado por `Name`.  Opcionalmente, `FriendlyName` pode especificar uma cadeia de caracteres para usar como o cabeçalho da coluna no profiler relatórios.  
  
-   **GC** \- coleta dados de memória do .NET.  Por**allocation**\(padrão\), os dados são coletados em cada evento de alocação de memória.  Quando o parâmetro de **lifetime** for especificado, os dados são coletados também em cada evento de coleta de lixo.  
  
## Exemplo  
 Este exemplo demonstra o uso de **Launch** iniciar um aplicativo.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)