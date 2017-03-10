---
title: "TargetCLR | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# TargetCLR
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A opção de **TargetCLR** especifica a versão do Common Language Runtime \(CLR\) para analisar quando mais de uma versão do CLR é carregada em um aplicativo.  
  
 Por padrão, o destino de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ferramentas de Criação de Perfil a primeira versão do CLR que é carregada pelo aplicativo.  
  
## Sintaxe  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### Parâmetros  
 `ClrVersion`  
 O número da versão do CLR.  Use o formato **vN.N.NNNNN**de versão.  
  
## Opções necessárias  
 A opção de **TargetCLR** só pode ser usada com as opções de **Launch** ou de **Attach** .  
  
 **Launch:** `AppName`  
 Inicia o aplicativo e inicia especificados analisar.  
  
 **Attach:** `PID`  
 O é iniciada para analisar o processo especificado.  
  
## Exemplo  
 Neste exemplo, a opção de TargetCLR é usada para garantir que a versão 4.0.11003 de CLR é analisada.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```