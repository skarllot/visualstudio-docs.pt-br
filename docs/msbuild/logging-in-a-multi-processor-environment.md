---
title: "Registrando em logs em um ambiente multiprocessador | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, log"
  - "MSBuild, log de vários processadores"
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Registrando em logs em um ambiente multiprocessador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A capacidade do MSBuild de usar vários processadores pode reduzir bastante tempo de compilação do projeto, mas também adiciona a complexidade ao log.  Em um ambiente de único processador, o registador pode manipular eventos de entrada, mensagens, avisos, e erros de forma previsível, sequencial.  No entanto, em um ambiente de processadores, eventos de várias fontes podem chegar simultaneamente ou fora da sequência.  MSBuild fornece um novo registador multi\-processador\- ciente e permite a criação de “de registadores personalizados transmissão.”  
  
## Compilações de vários processador de log  
 Quando você cria um ou vários projetos em um sistema de processadores ou de vários principais, eventos de compilação do MSBuild para todos os projetos são gerados simultaneamente.  Uma avalancha de dados do evento pode chegar no registador ao mesmo tempo ou fora da sequência.  Isso pode oprimir o registador e hora gerados causa de compilação, a saída de registador incorretas, ou mesmo uma compilação quebrada.  Para resolver esses problemas, o registador do MSBuild pode processar de eventos para fora de sequência e correlacionar eventos e suas fontes.  
  
 Você pode melhorar a eficiência de log ainda mais criando um registador personalizado de transferência.  Um registador de transmissão de atua como um filtro deixando o escolha, antes de criar, os eventos que você deseja monitorar.  Quando você usa um registador personalizado de transferência, os eventos indesejáveis não oprimem o registador, não desordenam os logs, ou não desacelerar tempo de compilação.  
  
### Modelo central de log  
 Para compilações multiprocessadores, MSBuild “usa um modelo central do log.” No modelo central de log, uma instância de MSBuild.exe atua como o processo de compilação primária, ou “o nó central.” As instâncias secundários de MSBuild.exe, ou “os nós colaterais,” são anexados ao nó central.  Todos os registadores baseados ILogger\- anexados ao nó central são conhecidos como “os registadores centrais” e o registadores anexados a nós secundários são conhecidos como “registadores secundários”.  
  
 Quando uma compilação ocorre, os registadores secundários roteiam o tráfego de eventos a registadores central.  Porque os eventos são originados em vários nós colaterais, os dados chegam no nó central simultaneamente mas intercalaram.  Para resolver evento\-à\- projeto e referências de evento\-à\- destino, os argumentos de evento incluem informações de contexto extra do evento compilação.  
  
 Embora apenas <xref:Microsoft.Build.Framework.ILogger> é necessário ser implementado pelo registador central, recomendamos que você também implementa <xref:Microsoft.Build.Framework.INodeLogger> se você desejar que o registador central para inicializar com o número de nós que estão participando na compilação.  A seguir sobrecarga do método de <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> é chamada quando o mecanismo inicializa o registador:  
  
```  
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
### O modelo de log  
 No modelo central do log, também tráfego de mensagem de entrada, como quando vários projetos criados imediatamente, pode oprimir o nó central, que força o sistema e move o desempenho de compilação.  
  
 Para reduzir esse problema, MSBuild também permite que um “modelo distribuído de log” que estende o modelo central de log deixando o criar registadores de transferência.  Um registador de transferência é anexado a um nó new e recebem eventos de entrada de compilação do nó.  O registador de transferência é apenas como um registador normal exceto que pode filtrar os eventos e então encaminhar somente desejado ao nó central.  Isso reduz o tráfego de mensagem no nó central e permite portanto o melhor desempenho.  
  
 Você pode criar um registador de transferência implementando a interface de <xref:Microsoft.Build.Framework.IForwardingLogger> , que deriva de <xref:Microsoft.Build.Framework.ILogger>.  A interface é definida como:  
  
```  
public interface IForwardingLogger: INodeLogger  
{  
    public IEventRedirector EventRedirector { get; set; }  
    public int NodeId { get; set; }  
}  
```  
  
 Para encaminhar eventos em um registador de transferência, chame o método de <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> de interface de <xref:Microsoft.Build.Framework.IEventRedirector> .  Passar <xref:Microsoft.Build.Framework.BuildEventArgs>apropriado, ou um derivada, como o parâmetro.  
  
 Para obter mais informações, consulte [Criando agentes de log de encaminhamento](../msbuild/creating-forwarding-loggers.md).  
  
### Anexando um registador distribuído  
 Para anexar um registador distribuído em uma construção de linha de comando, use a opção de `/distributedlogger` \(ou, `/dl` para breve\).  O formato para especificar os nomes de registador tipos e classes são as mesmas que essas para a opção de `/logger` , exceto que um registador distribuído é composto de duas classes de log: um registador de transferência e um registador central.  A seguir está um exemplo de anexar um registador distribuído:  
  
```  
msbuild.exe *.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,  
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,  
Culture=neutral  
```  
  
 Um asterisco \(\*\) separa os dois nomes de registador no opção de `/dl` .  
  
## Consulte também  
 [Agentes de log de compilação](../msbuild/build-loggers.md)   
 [Criando agentes de log de encaminhamento](../msbuild/creating-forwarding-loggers.md)