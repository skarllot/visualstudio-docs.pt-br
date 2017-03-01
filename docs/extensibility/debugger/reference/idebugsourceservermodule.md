---
title: IDebugSourceServerModule | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
caps.latest.revision: 8
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
ms.openlocfilehash: bf1fa0fac00835c92dbd8dbbbc8d495368014477
ms.lasthandoff: 02/22/2017

---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Representa as informações do servidor de origem que estão contidas em um arquivo PDB.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugSourceServerModule : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada pelos mecanismos de depurador e consumido pelo depurador da interface do usuário.  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir mostra os métodos de `IDebugSourceServerModule`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Recupera uma matriz de informações do servidor de origem.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
