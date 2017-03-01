---
title: IPropertyProxyEESide::GetManagedViewerCreationData | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
caps.latest.revision: 12
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
ms.openlocfilehash: 221d26b43f57c5519747ef04e9ccc17fc9fad10e
ms.lasthandoff: 02/22/2017

---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Recupera informações sobre o visualizador para esse tipo de propriedade para instanciar esse visualizador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetManagedViewerCreationData(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  className,  
   ASSEMBLYLOCRESOLUTION* alr,  
   BOOL*                  replacementOk  
);  
```  
  
```c#  
int GetManagedViewerCreationData(  
   out string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     className,  
   out enum_ASSEMBLYLOCRESOLUTION alr,  
   out int                        replacementOk  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `assemName`  
 [out] Retorna o nome do assembly que contém esse objeto.  
  
 `assemBytes`  
 [out] Retorna um [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto que contém os bytes de assembly do objeto (esse é um valor nulo se nenhum byte estiver disponível).  
  
 `assemPdb`  
 [out] Retorna um `IEEDataStorage` objeto que contém o símbolo de armazena informações para esse objeto (esse é um valor nulo se nenhum armazenamento de símbolo estiver disponível).  
  
 `className`  
 [out] Retorna o nome da classe que contém este objeto.  
  
 `alr`  
 [out] Retorna um valor a partir de [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) enumeração que indica o local do assembly.  
  
 `replacementOk`  
 [out] Retorna zero (`TRUE`) se o valor do objeto pode ser alterado; zero (`FALSE`) se o objeto for somente leitura.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é usado por visualizadores de tipo para instanciar um visualizador gerenciado.  
  
## <a name="see-also"></a>Consulte também  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
