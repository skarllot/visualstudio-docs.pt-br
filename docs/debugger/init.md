---
title: "Init | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Init
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Prepara o componente no aplicativo de diagnóstico de gráficos para capturar e registrar as informações de gráficos em um arquivo de log de gráfico ativamente.  
  
## Sintaxe  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### Parâmetros  
 `vsgLogGetter`  
 Uma entidade que pode ser chamada — como uma função, o ponteiro de função, a lambda ou o objeto de função — que usa como parâmetros o comprimento de um buffer composto de `wchar_t` e um ponteiro para esse buffer e retorna `void`. Quando invocada, a entidade que pode ser chamada determina o nome do arquivo que será usado para registrar informações de gráficos e grava o buffer especificado antes de retornar.  
  
## Comentários  
 O `Init` função é chamada automaticamente quando uma instância do `VsgDbg` classe for construída, especificando o `bDefaultInit` parâmetro do construtor como `true`; caso contrário, `Init` deve ser chamado explicitamente antes de capturar ativamente e gravar informações de gráficos.  
  
 Finalizar e fechar os ativos gráficos de log arquivo chamando `UnInit`, e, em seguida, capturar e registrar mais informações de gráficos para um novo arquivo de log de gráficos chamando `Init` novamente. Você pode repetir isso quantas vezes você deseja criar o gráfico independente de vários arquivos de log usando o mesmo `VsgDbg` instância.  
  
## Consulte também  
 [UnInit](../debugger/init.md)