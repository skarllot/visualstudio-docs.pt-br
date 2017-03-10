---
title: "Disabling the Visual Studio Debugger for Windows Workflow Foundation (Legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "workflows, disabling debugger"
  - "debugging workflows, disabling debugger"
  - "workflow debugger, disabling"
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Disabling the Visual Studio Debugger for Windows Workflow Foundation (Legacy)
Este tópico descreve como desativar o depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que usa o arquivo de configuração para criar aplicativos de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] em [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]herdado.  Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Por padrão, o depurador de [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] para [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] é habilitado para um processo host.  Para desativar a depuração de fluxo de trabalho, você deve explicitamente desativá\-la adicionando um elemento de **\<switches\>** de entrada de “DisableWorkflowDebugging a seção” de **\<system.diagnostics\>** do arquivo de configuração do host.  
  
 O exemplo a seguir mostra como modificar o arquivo de configuração do host para desativar a depuração de fluxo de trabalho.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="DisableWorkflowDebugging" value="true"/>  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## Consulte também  
 [Invoking the Visual Studio Debugger for Windows Workflow Foundation \(Legacy\)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Debugging Legacy Workflows](../workflow-designer/debugging-legacy-workflows.md)