---
title: IPropertyProxyEESide::CreateReplacementObject | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
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
ms.openlocfilehash: 3f718b13d24b576ecf86d5701d3a13dec056b358
ms.lasthandoff: 02/22/2017

---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Cria uma cópia de um objeto de dados específicas para o avaliador de expressão (EE).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```c#  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dataIn`  
 [in] Um [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto contém os dados a serem copiados.  
  
 `dataOut`  
 [out] Retorna um novo `IEEDataStorage` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método recebe um [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto que representa uma matriz de bytes. Normalmente, esse objeto de dados de entrada não é implementado pelo EE. No entanto, o objeto retornado por esse método sempre é implementado pela EE, que permite que o implemente EE o `IEEDataStorage` interface em qualquer classe for desejada.  
  
 Observe que os dados fornecidos pela entrada `IEEDataStorage` objeto deve ser os mesmos dados em que a saída `IEEDataStorage` objeto.  
  
## <a name="see-also"></a>Consulte também  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
