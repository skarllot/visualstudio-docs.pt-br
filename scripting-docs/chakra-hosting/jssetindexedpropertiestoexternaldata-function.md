---
title: "Função JsSetIndexedPropertiesToExternalData | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: cee2d86d-ed42-4acb-86ef-95a67e63d0d6
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 7180c5e233cfd5e448bc9f0d3eb1895e5dfd4aa8
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jssetindexedpropertiestoexternaldata-function"></a>Função JsSetIndexedPropertiesToExternalData
Define as propriedades indexadas de um objeto para dados externos. Os dados externos serão usados como repositório de backup para as propriedades indexadas do objeto e acessadas como uma matriz tipada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsSetIndexedPropertiesToExternalData(  
   _In_ JsValueRef object,  
   _In_ void* data,  
   _In_ JsTypedArrayType arrayType,  
   _In_ unsigned int elementLength  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `object`  
 O objeto no qual operar.  
  
 `data`  
 Os dados externos a serem usados como repositório de backup para as propriedades indexadas do objeto.  
  
 `arrayType`  
 O tipo de elemento de matriz em dados externos.  
  
 `elementLength`  
 O número de elementos da matriz em dados externos.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
 Essa API tem suporte apenas no modo de Borda.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
