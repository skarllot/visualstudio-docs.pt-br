---
title: "Eventos (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Eventos (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A opção de VSPerfCmd.exe **Events** controla o registro em log de Rastreamento de Eventos do Windows \(ETW\).  Os dados do ETW são salvos em um arquivo de .etl que está separado do arquivo de dados do profiler.  Os dados podem ser exibidos em um relatório usando o comando [VSPerfReport](../profiling/vsperfreport.md) \/summary:etw.  
  
 A opção de **Events** pode ser chamada a qualquer hora antes que o comando de VSPerfCmd **Shutdown** ser chamado parar de analisar.  
  
## Sintaxe  
  
```  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### Parâmetros  
 **On**&#124;**Off**  
 Inicia ou interrompe a coleta de dados do evento.  
  
 `Guid`  
 O GUID do controle do provedor.  
  
 `ProviderName`  
 O nome do provedor que é registrado com Windows management instrumentation \(WMI\).  
  
 `Flags`  
 Um “0x” \- os sinalizadores hexadecimais prefixados valor definido pelo provedor de eventos.  
  
 `Level`  
 Especifica a quantidade de dados coletados.  `Level` é definido pelo provedor de eventos.  
  
 A opção de **Events** inclui os seguintes palavras\-chave do kernel como nomes de provedor:  
  
 **Process**  
 Eventos de processamento  
  
 **Thread**  
 Eventos do thread  
  
 **Image**  
 Imagem para carregar e descarregar eventos  
  
 **Disk**  
 Eventos de E\/S de disco  
  
 **File**  
 Eventos de E\/S de Arquivo  
  
 **Hardfault**  
 Falhas de página de hardware  
  
 **Pagefault**  
 Falhas de página flexíveis  
  
 **Network**  
 Eventos de rede  
  
 **Registry**  
 Eventos de acesso do Registro  
  
 Observe que o provedor de kernel só pode ser habilitado.  Não pode ser desabilitado, nem os sinalizadores podem ser alterados, até que o monitor é desligado.  
  
## Comentários  
  
> [!NOTE]
>  Quando os eventos de CLR ETW estão habilitados, os dados de inicialização adicionais são coletados também no relatório de exibição de rastreamento.  Para excluir eventos de inicialização de aparecer no relatório, use o seguinte comando:  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
>  Se você não exclui os eventos de inicialização, então porque esses eventos não são listados no arquivo gerenciado \(MOF\) de formato do objeto, aparecem como GUIDs no relatório.  Para obter mais informações, consulte essa página no site da Microsoft: [Formato MOF exemplo \(MOF\) Arquivo do objeto](http://go.microsoft.com/fwlink/?linkid=37118).  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)