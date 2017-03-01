---
title: IDebugDefaultPort2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
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
ms.openlocfilehash: 5c163cfad314274218b09c5efed4cf25de52d829
ms.lasthandoff: 02/22/2017

---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Essa interface fornece vários métodos para acessar o servidor de uma porta e recursos de notificação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O Visual Studio implementa essa interface para representar a porta de depuração para acessar os programas. Um fornecedor de porta personalizada também pode implementar essa interface se ele lida com a depuração remota.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Um argumento para métodos de [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interface fornece essa interface. Chamando [QueryInterface](/visual-cpp/atl/queryinterface) em uma [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interface também pode obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Além dos métodos definidos no [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), essa interface implementa os seguintes métodos:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Obtém a interface de notificação de porta desta porta.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Obtém a interface para o servidor que hospeda essa porta.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Determina se a porta está em execução na máquina local.|  
  
## <a name="remarks"></a>Comentários  
 O nome "`IDebugDefaultPort2`" é uma designação incorreta, pois ele não representa uma porta padrão. Ele pode ser chamado "IDebugPort3".  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
