---
title: "ToggleHUD | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ToggleHUD
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ativa o \/desativar ou desativado coberto *de HUD* de diagnóstico dos gráficos \(exibição de início \- Acima\).  
  
## Sintaxe  
  
```cpp  
void ToggleHUD();  
```  
  
## Comentários  
 O diagnóstico HUD dos gráficos são exibidos no canto superior esquerdo do aplicativo que está em execução no diagnóstico de gráficos.  Exibe informações de tempo de execução sobre o aplicativo e sobre a captura de informações de gráficos, e as mensagens que são adicionadas chamando a função de membro de [AddMessage](../debugger/addmessage.md) .  
  
 Para ativar \/desativar HUD, você não precisa capturar ativamente gráficos \- seja, ele pode ser ativado \/desativar por uma instância da classe de `VsgDbg` , mas a função de membro de [Init](../debugger/init.md) não tem que ser chamada primeiro.