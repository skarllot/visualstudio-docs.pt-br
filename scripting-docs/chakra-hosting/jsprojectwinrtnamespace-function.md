---
title: "Função JsProjectWinRTNamespace | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8a23c154-df4b-4ce3-9fef-f41f90acdb87
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 04ecff41550219cdda5ea5d57f34fc440865bc99
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsprojectwinrtnamespace-function"></a>Função JsProjectWinRTNamespace
Projetar um namespace do WinRT.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode)  
   JsProjectWinRTNamespace(  
   _In_z_ const wchar_t *namespaceName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `namespaceName`  
 O namespace do WinRT a ser projetado.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
 Essa API tem suporte apenas no modo de Borda.  
  
> [!NOTE]
>  WinRT era o nome da plataforma antes do UWP (Plataforma Universal do Windows).  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
