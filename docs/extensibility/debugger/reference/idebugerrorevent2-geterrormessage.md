---
title: IDebugErrorEvent2::GetErrorMessage | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: 9
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
ms.openlocfilehash: 310432b8c2c728fa930d0955d5234dd389ff21b0
ms.lasthandoff: 02/22/2017

---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Retorna informações que permite a construção de uma mensagem de erro legível.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```c#  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pMessageType`  
 [out] Retorna um valor a partir de [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) enumeração, que descreve o tipo de mensagem.  
  
 `pbstrErrorFormat`  
 [out] O formato da mensagem para o usuário final (consulte "Comentários" para obter detalhes).  
  
 `hrErrorReason`  
 [out] O código de erro, a mensagem é sobre.  
  
 `pdwType`  
 [out] Gravidade do erro (use as constantes MB_XXX para `MessageBox`; por exemplo, `MB_EXCLAMATION` ou `MB_WARNING`).  
  
 `pbstrHelpFileName`  
 [out] Caminho para um arquivo de Ajuda (definido como um valor nulo se não houver nenhum arquivo de Ajuda).  
  
 `pdwHelpId`  
 [out] ID do tópico da Ajuda para exibir (definido como 0 se não houver nenhum tópico da Ajuda).  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A mensagem de erro deve ser formatada ao longo das linhas de `"What I was doing.  %1"`. O `"%1"` deve ser substituído pelo chamador com a mensagem de erro derivada do código de erro (que é retornado no `hrErrorReason`). O `pMessageType` parâmetro informa o chamador como a mensagem de erro final deve ser exibida.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
