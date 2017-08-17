---
title: "Função JsRunSerializedScriptWithCallback | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0608d778-f65b-4dc5-a745-364aac57ef59
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: ce51c9473100e71831dd53cc6572d9740790ffa0
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsrunserializedscriptwithcallback-function"></a>Função JsRunSerializedScriptWithCallback
Executa um script serializado.     Fornece a capacidade de efetuar carregamento lento da fonte de script somente se/quando necessário.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsRunSerializedScriptWithCallback(  
  _In_ JsSerializedScriptLoadSourceCallback scriptLoadCallback,  
  _In_ JsSerializedScriptUnloadCallback scriptUnloadCallback,  
  _In_ BYTE *buffer,  
  _In_ JsSourceContext sourceContext,  
  _In_z_ const wchar_t *sourceUrl,  
  _Out_opt_ JsValueRef *result  
);  
  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `scriptLoadCallback`  
 Retorno de chamada chamado quando o código-fonte do script deve ser carregado.  
  
 `scriptUnloadCallback`  
 Retorno de chamada chamado quando o script serializado e o código-fonte não são mais necessários.  
  
 `buffer`  
 O script serializado.  
  
 `sourceContext`  
 Um cookie identificando o script que pode ser usado por contextos de script depuráveis.     Esse contexto será passado para scriptLoadCallback e scriptUnloadCallback.  
  
 `sourceUrl`  
 O local de onde o script veio.  
  
 `result`  
 O resultado da execução do script, se houver. Este parâmetro pode ser nulo.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esta API ainda não está disponível para Aplicativos da Windows Store.  
  
 Exige um contexto de script ativo.  
  
 O tempo de execução permanecerá com o buffer até que todas as instâncias de todas as funções criadas do buffer tenham sido coletadas como lixo.  Em seguida, ele chamará scriptUnloadCallback para informar o chamador que é seguro fazer a liberação.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
