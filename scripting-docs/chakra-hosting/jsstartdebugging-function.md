---
title: "Função JsStartDebugging | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsStartDebugging
helpviewer_keywords:
- JsStartDebugging function
ms.assetid: c48ba02d-6d47-466f-a970-02f087d525f3
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: bd9b7e3deb407d1a1e9d16db38e17c85ccc8c797
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsstartdebugging-function"></a>Função JsStartDebugging
Inicia a depuração de perfil no contexto atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsStartDebugging();  
  
// Legacy mode signature  
STDAPI_(JsErrorCode)  JsStartDebugging(  
   _In_ IDebugApplication *debugApplication  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `debugApplication`  
 O aplicativo de depuração a ser usado para depuração.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 O host deve garantir que `CoInitializeEx` seja chamado com `COINIT_MULTITHREADED` ou `COINIT_APARTMENTTHREADED` pelo menos uma vez antes de usar essa API  
  
 O parâmetro `debugApplication` não tem suporte no modo de borda. Para obter mais informações sobre como usar essa API no modo de borda, consulte [Borda de destino vs. mecanismos herdados](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
