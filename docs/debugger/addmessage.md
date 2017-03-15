---
title: "AddMessage | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# AddMessage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Adiciona uma mensagem personalizada a diagnósticos *HUD* dos gráficos \(exibição de início \- Acima\).  
  
## Sintaxe  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### Parâmetros  
 `szMessage`  
 A mensagem a ser adicionada a HUD.  
  
## Comentários  
 O diagnóstico HUD dos gráficos são exibidos no canto superior esquerdo do aplicativo que está em execução no diagnóstico de gráficos.  Exibe informações de tempo de execução sobre o aplicativo e sobre a captura de informações de gráficos, e as mensagens que são adicionadas chamando essa função.  
  
 Para adicionar uma mensagem a HUD, você não precisa capturar ativamente gráficos \- seja, uma mensagem poderá ser adicionado por meio de uma instância da classe de `VsgDbg` , mas a função de membro de [Init](../debugger/init.md) não é chamada primeiro.  As mensagens são exibidas apenas em HUD, elas não são registradas no arquivo de log dos gráficos.