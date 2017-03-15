---
title: IDebugProgramHost2::GetHostName | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 10
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
ms.openlocfilehash: 119f1929ff1f5295da195b3195df175bdaa174ac
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Obtém o título, nome amigável ou nome de arquivo do processo de hospedagem desse programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```c#  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwType`  
 [in] Um valor a partir de [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) enumeração.  
  
 `pbstrHostName`  
 [out] Retorna o nome solicitado do processo de hospedagem.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Em uma implementação típica desse método, o `dwType` parâmetro será ignorado e um nome amigável do computador host é retornado. Outro possível implementação é passar o `dwType` parâmetro a uma chamada para o [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) método para obter o nome.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
