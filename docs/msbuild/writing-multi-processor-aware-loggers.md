---
title: "Escrevendo agentes de log com reconhecimento de multiprocessador | Microsoft Docs"
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
  - "agentes de log, proc múltiplo"
  - "msbuild, agentes de log com reconhecimento de proc múltiplo"
  - "agentes de log de proc múltiplo"
ms.assetid: ff987d1b-1798-4803-9ef6-cc8fcc263516
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Escrevendo agentes de log com reconhecimento de multiprocessador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A capacidade de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] de aproveitar de múltiplos processadores pode diminuir tempo de compilação do projeto, mas também adiciona a complexidade para compilar o log de eventos.  Em um ambiente de único processador, eventos, as mensagens, avisos, e os erros chegam no registador de forma previsível, sequencial.  No entanto, em um ambiente de processadores, os eventos de fontes diferentes podem chegar ao mesmo tempo ou fora da sequência.  Para prever isso, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fornece um registador multi\-processador\- ciente e um novo modelo de log, e permite que você crie de “registadores personalizados transmissão.”  
  
## Desafios de log multiprocessadores  
 Quando você cria um ou vários projetos em um sistema de processadores ou de vários principais, eventos de compilação de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para todos os projetos são gerados ao mesmo tempo.  Uma avalancha de mensagens do evento pode chegar no registador ao mesmo tempo ou fora da sequência.  Como um registador de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2,0 não é criado para tratar essa situação, pode oprimir o registador e hora gerados causa de compilação, a saída de registador incorretas, ou mesmo uma compilação quebrada.  Para resolver esses problemas, o registador \(começando em [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3,5\) pode processar de eventos para fora de sequência e correlacionar eventos e suas fontes.  
  
 Você pode melhorar a eficiência de log ainda mais criando um registador personalizado de transferência.  Um registador personalizado de transferência atua como um filtro deixando o escolha, antes de criar, somente os eventos você deseja monitorar.  Quando você usa um registador personalizado de transferência, os eventos não podem não oprimir o registador, não desordenam os logs, ou não desacelerar tempo de compilação.  
  
## Modelos de log multiprocessadores  
 Para prever problemas relacionados multi\-processador\- de compilação, suporte de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] dois modelos de log, central e distribuído.  
  
### Modelo central de log  
 No modelo central de log, uma única instância de MSBuild.exe atua como “o nó central,” e instâncias filhos do anexo central do nó nós secundários \(“”\) para o nó central para ajudá\-lo a executar tarefas de compilação.  
  
 ![Modelo de agente de log central](../msbuild/media/centralnode.png "CentralNode")  
  
 Os registadores de vários tipos que anexa ao nó central são conhecidos como “registadores central.” Apenas uma instância de cada tipo de registador pode ser anexado ao nó central ao mesmo tempo.  
  
 Quando uma compilação ocorre, os nós secundários roteiam seus eventos de compilação para o nó central.  O nó central de roteamento todos os seus eventos, e também são de nós colaterais, a um ou mais dos registadores central anexados.  Os registadores criam nos arquivos de log que são baseados nos dados de entrada.  
  
 Embora apenas <xref:Microsoft.Build.Framework.ILogger> é necessário ser implementado pelo registador central, recomendamos que você também implementa <xref:Microsoft.Build.Framework.INodeLogger> de modo que o registador central inicializa com o número de nós que estão participando na compilação.  A seguir sobrecarga do método de <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> chama quando o mecanismo inicializa o registador.  
  
```  
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
 Todos os registadores baseado em passos existentes de <xref:Microsoft.Build.Framework.ILogger>podem atuar como registadores central e pode anexar à compilação.  No entanto, os registadores central escritos sem suporte explícito para cenários de log multiprocessadores e eventos fora de ordem podem quebrar uma compilação ou produzir saída sem sentido.  
  
### O modelo de log  
 No modelo central do log, também tráfego de mensagem de entrada pode oprimir o nó central, por exemplo, quando vários projetos criados ao mesmo tempo.  Isso pode forçar recursos do sistema e diminuir o desempenho de compilação.  Para facilitar esse problema, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] suporta um modelo distribuído de log.  
  
 ![Modelo de log distribuído](../msbuild/media/distnode.png "DistNode")  
  
 O modelo distribuído de log estende o modelo central de log deixando o criar um registador de transferência.  
  
#### Registadores de transferência  
 Um registador de transferência é um registador new, leve que tenha um filtro do evento que os anexa a um nó new e recebem eventos de entrada de compilação do nó.  Filtra os eventos de entrada e encaminha somente aqueles que você especifica para o nó central.  Isso reduz o tráfego de mensagem que é enviado ao nó central e melhora o desempenho geral de compilação.  
  
 Há duas maneiras de usar o log distribuído, como segue:  
  
-   Personalizar o registador pré\-fabricado de transferência chamado <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger>.  
  
-   Escreva seu próprio registador personalizado de transferência.  
  
 Você pode alterar ConfigurableForwardingLogger para atender suas necessidades.  Para fazer isso, chame o registador na linha de comando usando MSBuild.exe, e lista os eventos de compilação que você deseja que o registador para encaminhar ao nó central.  
  
 Como alternativa, você pode criar um registador personalizado de transferência.  Criando um registador personalizado de transferência, você pode ajustar o comportamento de registador.  No entanto, criar um registador personalizado de transferência é mais complexa do que apenas personalizando o ConfigurableForwardingLogger.  Para obter mais informações, consulte [Criando agentes de log de encaminhamento](../msbuild/creating-forwarding-loggers.md).  
  
## Usando o ConfigurableForwardingLogger para o log distribuído simples  
 Para anexar um ConfigurableForwardingLogger ou um registador personalizado de transferência, use a opção de `/distributedlogger` \(`/dl` para breve\) em uma construção de linha de comando MSBuild.exe.  O formato para especificar os nomes de tipos e as classes de registador é o mesmo que para a opção de `/logger` , exceto que um registador distribuído sempre tem duas classes de log em vez de uma, o registador de transferência e o registador central.  A seguir está um exemplo de como anexar um registador personalizado chamado XMLForwardingLogger de transferência.  
  
```  
msbuild.exe myproj.proj/distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral  
```  
  
> [!NOTE]
>  Um asterisco \(\*\) deve separar os dois nomes de registador no opção de `/dl` .  
  
 Usar o ConfigurableForwardingLogger é como usar de qualquer outro registador \(de acordo com [Obtendo logs de compilação](../msbuild/obtaining-build-logs-with-msbuild.md)\), exceto que você anexe o registador de ConfigurableForwardingLogger em vez de registador típico de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] e você especifica como parâmetros os eventos que você deseja que o ConfigurableForwardingLogger para passar sobre o nó central.  
  
 Por exemplo, se você desejar ser notificado somente quando inicia e extremidades de uma compilação, e quando ocorre um erro, você deve `BUILDSTARTEDEVENT`, `BUILDFINISHEDEVENT`, e `ERROREVENT` como parâmetros.  Vários parâmetros podem ser passados separando\-os com dois\-pontos semi\-confiáveis.  O código a seguir é um exemplo de como usar o ConfigurableForwardingLogger para encaminhar somente `BUILDSTARTEDEVENT`, `BUILDFINISHEDEVENT`, e eventos de `ERROREVENT` .  
  
```  
msbuild.exe myproj.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT  
```  
  
 Segue uma lista de parâmetros disponíveis de ConfigurableForwardingLogger.  
  
|Parâmetros de ConfigurableForwardingLogger|  
|------------------------------------------------|  
|BUILDSTARTEDEVENT|  
|BUILDFINISHEDEVENT|  
|PROJECTSTARTEDEVENT|  
|PROJECTFINISHEDEVENT|  
|TARGETSTARTEDEVENT|  
|TARGETFINISHEDEVENT|  
|TASKSTARTEDEVENT|  
|TASKFINISHEDEVENT|  
|ERROREVENT|  
|WARNINGEVENT|  
|HIGHMESSAGEEVENT|  
|NORMALMESSAGEEVENT|  
|LOWMESSAGEEVENT|  
|CUSTOMEVENT|  
|COMMANDLINE|  
|PERFORMANCESUMMARY|  
|NOSUMMARY|  
|SHOWCOMMANDLINE|  
  
## Consulte também  
 [Criando agentes de log de encaminhamento](../msbuild/creating-forwarding-loggers.md)