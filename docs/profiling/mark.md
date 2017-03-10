---
title: "Marca | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Marca
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A opção de VSPerfCmd.exe **Mark** insere as informações especificadas no arquivo de dados de perfil.  A marca pode ser listada em um relatório separado de VSPerfReport ou na visualização de relatório da marca do profiler interface do usuário.  **Mark** pode ser usado para especificar os pontos de início e término em filtros de relatório e exibição.  
  
 A opção de **Mark** deve ser a única opção especificada na linha de comando.  
  
## Sintaxe  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]   
```  
  
#### Parâmetros  
 `MarkID`  
 Um inteiro definido pelo usuário que é listado como a ID da marca no profiler e exibe relatórios.  `MarkID` não precisa ser exclusivo.  
  
 `MarkName`  
 \(Opcional\) Uma cadeia de caracteres definida pelo usuário que é listada como o nome da marca no profiler e exibe relatórios.  Se `MarkName` não for especificado, o campo de nome de uma marca de listagem da marca está vazia.  Incluir as cadeias de caracteres que contêm espaços ou barras \(“\/"\) entre aspas.  
  
## Exemplo  
 Este exemplo insere identificar por meio de ID de 123 e um nome de marca de TestMark “”.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)