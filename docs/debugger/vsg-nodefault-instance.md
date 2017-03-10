---
title: "VSG_NODEFAULT_INSTANCE | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSG_NODEFAULT_INSTANCE
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Define por sua presença se uma instância padrão de [Classe VsgDbg](../debugger/vsgdbg-class.md) classe fornece que a captura programático interface\- é fornecida.  
  
## Sintaxe  
  
```cpp  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## Valor  
 Um símbolo de pré\-processador que por sua presença ou ausência determina se uma instância padrão da classe de `VsgDbg` é fornecida.  Se esse símbolo é definido, nenhuma instância padrão da classe de `VsgDbg` é fornecida; caso contrário, uma instância padrão será fornecida e inicializada antes que o programa seja executado.  
  
 A interface programática de captura é fornecida por meio de um ponteiro que têm o escopo global, `g_pVsgDbg`.  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## Comentários  
 A instância padrão é geralmente suficiente, mas para usar a interface programática de captura dentro de uma DLL quando o dispositivo de D3D a parte externa foi criada que o DLL, você deve criar e gerenciar sua própria instância da classe de `VsgDbg` .  Se você estiver gerenciando a sua própria interface captura programático à API dessa maneira, desabilite a instância padrão definindo `VSG_NODEFAULT_INSTANCE` para evitar a sobrecarga.  
  
 Se a instância padrão não for desabilitada, é inicializada automaticamente antes que o programa executado e é destruído automaticamente quando seu programa será encerrado.  Não é necessário inicializar ou não inicializar essa instância explicitamente.  
  
 Para desabilitar a instância padrão, você deve definir `VSG_NODEFAULT_INSTANCE` antes que você inclua `vsgcapture.h` em seu programa.  
  
## Exemplo  
 Este exemplo mostra como desabilitar a instância padrão:  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```