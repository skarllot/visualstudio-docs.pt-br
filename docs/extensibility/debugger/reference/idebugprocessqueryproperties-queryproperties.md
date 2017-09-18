---
title: IDebugProcessQueryProperties::QueryProperties | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugProcessQueryProperties::QueryProperties
ms.assetid: 976a9962-b689-45bb-afb6-16b2c5dbc3b8
caps.latest.revision: 5
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
ms.openlocfilehash: c54b8bd91150296640d4491d02e1cd0e55e5e0c4
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprocessquerypropertiesqueryproperties"></a>IDebugProcessQueryProperties::QueryProperties
Essa consulta método um valores de propriedade especificada do processo de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT QueryProperties(  
   ULONG                  celt,  
   PROCESS_PROPERTY_TYPE *rgdwPropTypes,  
   VARIANT               *rgtPropValues);  
```  
  
```c#  
int QueryProperties(  
   uint                       celt,  
   enum_PROCESS_PROPERTY_TYPE rgdwPropTypes,  
   out object[ ]              rgtPropValues);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 [in] Tamanho das matrizes que contém as definições de propriedade e valores de propriedade.  
  
 `dwPropType`  
 [in] Uma matriz que contém as definições das propriedades consultadas. Os valores possíveis são:  
  
-   PROCESS_PROPERTY_COMMAND_LINE = 1  
  
-   PROCESS_PROPERTY_CURRENT_DIRECTORY = 2  
  
-   PROCESS_PROPERTY_ENVIRONMENT_VARIABLES = 3  
  
 `pvarPropValue`  
 [out] Uma matriz que contém os valores de propriedade.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é usado raramente.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProcessQueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties.md)
