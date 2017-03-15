---
title: "IDiaFrameData::execute | Microsoft Docs"
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
  - "Método IDiaFrameData::execute"
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Executa o desenrolamento de pilha e retorna resultados em uma interface de quadro de movimentação de pilha.  
  
## Sintaxe  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### Parâmetros  
 `frame`  
 \[in\] Um [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) o objeto que contém o estado de registradores de quadro.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  A tabela a seguir mostra os valores de retorno possíveis para esse método.  
  
|Valor|Descrição|  
|-----------|---------------|  
|E\_DIA\_INPROLOG|Não é possível executar um quadro de pilha no código de prólogo.|  
|E\_DIA\_SYNTAX|Erro encontrado no programa de quadro de análise.|  
|E\_DIA\_FRAME\_ACCESS|Não é possível registradores de acesso ou de memória.|  
|E\_DIA\_VALUE|Erro no cálculo de um valor \(por exemplo, a divisão por zero\).|  
  
## Comentários  
 Este método é chamado durante a depuração desenrolar a pilha.  O [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) objeto é implementado pelo aplicativo cliente para receber atualizações para os registradores e fornecer métodos usados pelo `execute` método.  
  
## Consulte também  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)