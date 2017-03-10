---
title: "Criando agentes de log de encaminhamento | Microsoft Docs"
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
  - "MSBuild, encaminhando agentes de log"
  - "MSBuild, log"
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Criando agentes de log de encaminhamento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Registradores de encaminhamento de melhoram a eficiência do registro, permitindo que você escolha os eventos que você deseja monitorar ao construir projetos em um sistema com vários processadores.  Habilitando o encaminhamento de registradores, você pode impedir que eventos indesejados de sobrecarregar o agente de log central, diminuindo o tempo de compilação e sobrecarregam o seu registro.  
  
 Para criar um agente de log de encaminhamento, você pode tanto implementar a <xref:Microsoft.Build.Framework.IForwardingLogger> de interface e implementar seus métodos manualmente ou usar o <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> classe e seus métodos pré\-configurados.  \(Este último será suficiente para a maioria dos aplicativos.\)  
  
## Registro de eventos e responder a elas  
 Um agente de log de encaminhamento reúne informações sobre eventos de compilação, conforme eles são relatados pelo mecanismo de compilação secundário, que é um processo de trabalho é criado pelo processo de compilação principal durante uma compilação em um sistema com vários processadores.  Em seguida, o agente de log de encaminhamento seleciona eventos para encaminhar para o agente de log central, com base nas instruções que tenha dado a ele.  
  
 Você deve registrar os registradores de encaminhamento para manipular os eventos que você deseja monitorar.  Para registrar eventos, registradores devem substituir o <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> método.  Esse método inclui agora um parâmetro opcional, `nodecount`, que pode ser definida como o número de processadores no sistema.  \(Por padrão, o valor é 1\).  
  
 São exemplos de eventos, você pode monitorar <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, e <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.  
  
 Em um ambiente com vários processadores, mensagens de evento serão provável que sejam recebidos fora de ordem.  Portanto, você deve avaliar os eventos usando o manipulador de eventos em que o agente de log de encaminhamento e programá\-lo para determinar quais eventos para passar para o redirecionador para encaminhamento para o agente de log central.  Para fazer isso, você pode usar o <xref:Microsoft.Build.Framework.BuildEventContext> classe, o qual está associada a cada mensagem, para ajudar a identificar os eventos que você deseja encaminhar, e, em seguida, passar os nomes dos eventos para o <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> classe \(ou uma subclasse dela\).  Quando você usa esse método, sem outros específicos codificação é necessária para encaminhar eventos.  
  
## Especifique um agente de log de encaminhamento  
 Depois que o agente de log de encaminhamento tiver sido compilado em um assembly, você deve informar o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para usá\-lo durante a construção.  Para fazer isso, use o `/FileLogger`, `/FileLoggerParameters`, e `/DistributedFileLogger` switches junto com o MSBuild. exe.  O `/FileLogger` opção faz com que MSBuild. exe que o agente de log está diretamente conectado. O `/DistributedFileLogger` opção significa que há um arquivo de log por nó.  Para definir os parâmetros do agente de log de encaminhamento, use o `/FileLoggerParameters` alternar.  Para obter mais informações sobre essas e outras opções do MSBuild. exe, consulte [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md).  
  
## Registradores de multi\-processador\-Aware  
 Quando você cria um projeto em um sistema com vários processadores, as mensagens de compilação de cada processador não são intercaladas automaticamente em uma seqüência unificada.  Em vez disso, você deve estabelecer uma mensagem de prioridade de agrupamento, usando o <xref:Microsoft.Build.Framework.BuildEventContext> classe que está associada a cada mensagem.  Para obter mais informações sobre como criar vários processadores, consulte [Registrando em logs em um ambiente multiprocessador](../msbuild/logging-in-a-multi-processor-environment.md).  
  
## Consulte também  
 [Obtendo logs de compilação](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Agentes de log de compilação](../msbuild/build-loggers.md)   
 [Registrando em logs em um ambiente multiprocessador](../msbuild/logging-in-a-multi-processor-environment.md)