---
title: "IDiaStackWalkHelper | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Interface IDiaStackWalkHelper2"
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Facilita a movimentar a pilha usando o arquivo de banco de dados \(. PDB\) de depuração do programa.  
  
## Sintaxe  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## Métodos na ordem de VTable  
 A tabela abaixo mostra os métodos de `IDiaStackWalkHelper`:  
  
|Método|Descrição|  
|------------|---------------|  
|[IDiaStackWalkHelper::get\_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|Recupera o valor de um registrador.|  
|[IDiaStackWalkHelper::put\_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Define o valor de um registrador.|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Lê um bloco de dados de imagem do executável na memória.|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Pesquisa o quadro de pilhas especificado para o endereço de retorno de função mais próximo.|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../Topic/IDiaStackWalkHelper::searchForReturnAddressStart.md)|Pesquisa o quadro de pilhas especificado para um endereço de remetente ou próximo o endereço especificado de pilha.|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Recupera o quadro de pilha que contém o endereço virtual especificado.|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Recupera o símbolo que contém o endereço virtual especificado. **Note:**  Símbolo deve ter o tipo `SymTagFunctionType` \(um valor a partir do [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) enumeração\).|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Retorna o bloco de dados PDATA associado ao endereço virtual especificado.|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Recupera o endereço virtual inicial de um executável, fornecido um endereço virtual em algum lugar no espaço de memória do executável.|  
  
## Comentários  
 Essa interface é chamada pelo código do DIA para obter informações sobre o executável para construir uma lista de quadros de pilha durante a execução do programa.  
  
## Observações para chamadores  
 Um aplicativo cliente implementa essa interface para oferecer suporte a movimentar a pilha durante a execução do programa.  Uma instância desta interface é passada para o [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) ou [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) métodos.  
  
## Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Consulte também  
 [Interfaces \(SDK de Acesso à Interface de Depuração\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)