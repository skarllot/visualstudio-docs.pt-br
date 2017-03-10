---
title: "UnInit | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# UnInit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Finaliza o arquivo de log de gráficos, fecha e libera os recursos que foram usados enquanto o aplicativo estava gravando ativamente informações gráficas.  
  
## Sintaxe  
  
```cpp  
void UnInit();  
```  
  
## Comentários  
 `UnInit` é chamado automaticamente quando uma instância do `VsgDbg` classe é destruída. Se o `VsgDbg` instância não estava gravando ativamente informações gráficas, isso não tem efeito.  
  
 Depois de `UnInit` foi chamado em uma instância do `VsgDbg` classe, uma gráfico novo arquivo de log pode ser criado chamando `Init` e finalização, chamando `UnInit`. Você pode repetir isso quantas vezes você deseja usar o mesmo `VsgDbg` instância para criar o gráfico independente de vários arquivos de log.  
  
## Consulte também  
 [Init](../debugger/init.md)