---
title: Agentes de Build | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: ee5db285c55dc3969bd21fe722d7e4bacdcb6f3c
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="build-loggers"></a>Agentes de log de build
Agentes fornecem uma maneira de personalizar a saída do build e exibir mensagens, erros ou avisos em resposta a eventos de build específicos. Cada agente é implementado como uma classe .NET que implementa a interface <xref:Microsoft.Build.Framework.ILogger>, que é definida no assembly Microsoft.Build.Framework.dll.  
  
 Há duas abordagens que você pode usar ao implementar um agente:  
  
-   Implemente a interface <xref:Microsoft.Build.Framework.ILogger> diretamente.  
  
-   Derive sua classe da classe do auxiliar, <xref:Microsoft.Build.Utilities.Logger>, que é definida no assembly Microsoft.Build.Utilities.dll. O <xref:Microsoft.Build.Utilities.Logger> implementa o <xref:Microsoft.Build.Framework.ILogger> e fornece implementações padrão de alguns membros do <xref:Microsoft.Build.Framework.ILogger>.  
  
 Este tópico explicará como escrever um agente simples que deriva de <xref:Microsoft.Build.Utilities.Logger> e exibe mensagens no console em resposta a determinados eventos de build.  
  
## <a name="registering-for-events"></a>Registrar-se em eventos  
 A finalidade de um agente é reunir informações sobre o andamento do build quando ele for relatado pelo mecanismo de build e, em seguida, relatar informações de maneira útil. Todos os agentes devem substituir o método <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>, que é onde o agente se registra para eventos. Neste exemplo, o agente registra-se nos eventos <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> e <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]  
  
## <a name="responding-to-events"></a>Respondendo a eventos  
 Agora que o agente está registrado para eventos específicos, ele precisa lidar com esses eventos quando eles ocorrem. Para os eventos <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> e <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>, o agente simplesmente escreve uma frase curta e o nome do arquivo de projeto envolvido no evento. Todas as mensagens do agente são gravadas na janela do console.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]  
  
## <a name="responding-to-logger-verbosity-values"></a>Respondendo a valores de detalhamento do agente  
 Em alguns casos, você talvez queira registrar informações de um evento somente se a opção MSBuild.exe **/verbosity** contiver um determinado valor. Neste exemplo, o manipulador de eventos <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> registrará no log apenas uma mensagem se a propriedade <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A>, que é definida pela opção **/verbosity**, for igual a <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed`.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]  
  
## <a name="specifying-a-logger"></a>Especificando um agente  
 Depois que o agente for compilado em um assembly, você precisará informar ao [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para usar esse agente durante builds. Isso é feito usando a opção **/logger** com MSBuild.exe. Para obter mais informações sobre as opções disponíveis para MSBuild.exe, consulte [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md).  
  
 A linha de comando a seguir compila o projeto `MyProject.csproj` e usa a classe de agente implementada em `SimpleLogger.dll`. A opção **/nologo** oculta a faixa e a mensagem de direitos autorais e a opção **/noconsolelogger** desabilita o agente de console [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] padrão.  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll  
```  
  
 A linha de comando a seguir compila o projeto com o mesmo agente, mas com um nível `Verbosity` de `Detailed`.  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll /verbosity:Detailed  
```  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir contém o código completo do agente.  
  
### <a name="code"></a>Código  
 [!code-csharp[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]  
  
### <a name="comments"></a>Comentários  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir mostra como implementar um agente que grava o log de um arquivo em vez de exibi-lo na janela do console.  
  
### <a name="code"></a>Código  
 [!code-csharp[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]  
  
### <a name="comments"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [Obtaining Build Logs (Obtendo logs de build)](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)
