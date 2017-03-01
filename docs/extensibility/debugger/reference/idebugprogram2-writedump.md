---
title: IDebugProgram2::WriteDump | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d1a39ca7e7fffbd00eca424f047ab24dde0559d7
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Grava um despejo de memória em um arquivo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```c#  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `DumpType`  
 [in] Um valor a partir de [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) enumeração que especifica o tipo de despejo de memória, por exemplo, curto ou longo.  
  
 `pszDumpUrl`  
 [in] A URL para gravar o despejo de memória para. Normalmente, isso é na forma de `file://c:\path\filename.ext`, mas pode ser qualquer URL válido.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Um despejo de programa normalmente incluiria o quadro de pilha atual, a pilha em si, uma lista de threads em execução no programa e possivelmente toda a memória que possui o programa.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
