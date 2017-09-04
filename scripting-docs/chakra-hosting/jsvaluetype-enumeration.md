---
title: "Enumeração JsValueType | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsValueType
helpviewer_keywords:
- JsValueType enumeration
ms.assetid: 6645e723-e554-41fc-b622-ab54ee044b3d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: df4f61cf9118c19a0fc35e7505af422b812d0b43
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsvaluetype-enumeration"></a>Enumeração JsValueType
O tipo de JavaScript de um JsValueRef.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
enum JsValueType {  
    JsUndefined      = 0,  
    JsNull           = 1,  
    JsNumber         = 2,  
    JsString         = 3,  
    JsBoolean        = 4,  
    JsObject         = 5,  
    JsFunction       = 6,  
    JsError          = 7,  
    JsArray          = 8,  
    JsSymbol         = 9,  
    JsArrayBuffer    = 10,  
    JsTypedArray     = 11,  
    JsDataView       = 12,  
};  
```  
  
## <a name="members"></a>Membros  
  
### <a name="values"></a>Valores  
  
|Nome|Descrição|  
|----------|-----------------|  
|`JsUndefined`|O valor é o valor `undefined`.|  
|`JsNull`|O valor é o valor `null`.|  
|`JsNumber`|O valor é um valor numérico de JavaScript.|  
|`JsString`|O valor é um valor de cadeia de caracteres de JavaScript.|  
|`JsBoolean`|O valor é um valor booliano de JavaScript.|  
|`JsObject`|O valor é um valor de objeto de JavaScript.|  
|`JsFunction`|O valor é um valor de objeto de função de JavaScript.|  
|`JsError`|O valor é um valor de objeto de erro de JavaScript.|  
|`JsArray`|O valor é um valor de objeto de matriz de JavaScript.|  
|`JsSymbol`|O valor é um valor de símbolo de JavaScript.<br /><br /> Este valor de enumeração tem suporte somente no modo de borda.|  
|`JsArrayBuffer`|O valor é um valor de objeto `ArrayBuffer` de JavaScript.<br /><br /> Este valor de enumeração tem suporte somente no modo de borda.|  
|`JsTypedArray`|O valor é um valor de objeto de matriz tipada de JavaScript.<br /><br /> Este valor de enumeração tem suporte somente no modo de borda.|  
|`JsDataView`|O valor é um valor de objeto `DataView` de JavaScript.<br /><br /> Este valor de enumeração tem suporte somente no modo de borda.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
