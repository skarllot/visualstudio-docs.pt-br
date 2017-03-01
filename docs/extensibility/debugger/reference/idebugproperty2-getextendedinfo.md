---
title: IDebugProperty2::GetExtendedInfo | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
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
ms.openlocfilehash: 4810a99bb42c8688c4cf1ee6a26f5494f5369d2b
ms.lasthandoff: 02/22/2017

---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
Obtém informações estendidas de propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```c#  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `guidExtendedInfo`  
 [in] GUID que determina o tipo de informações estendidas a serem recuperados. Consulte comentários para obter detalhes.  
  
 `pExtendedInfo`  
 [out] Retorna um `VARIANT` (C++) ou objeto (c#) que pode ser usado para recuperar as informações de propriedade estendida. Por exemplo, esse parâmetro pode retornar um `IUnknown` interface que pode ser consultada por um [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) interface. Consulte comentários para obter detalhes.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna o código de erro. Retorna `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` se não houver nenhuma informação estendida para recuperar.  
  
## <a name="remarks"></a>Comentários  
 Este método existe para fins de recuperação de informações que não se prestam para ser recuperado chamando o [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método.  
  
 Os GUIDs seguir normalmente são reconhecidos por esse método (os valores GUID são especificados para c# desde que o nome não está disponível em qualquer assembly). GUIDs adicionais podem ser criados para uso interno.  
  
|Nome|GUID|Descrição|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Retorna um `IUnknown` interface para o documento. Normalmente, o [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) interface pode ser obtida a partir dessa `IUnknown` interface.|  
|guidCodeContext|{e2fc65e-56ce -&11;d&1;-b528-00aax004a8797}|Retorna um `IUnknown` interface para o contexto do documento. Normalmente, o [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interface pode ser obtida a partir dessa `IUnknown` interface.|  
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Retorna uma cadeia de caracteres que contém o CLSID de um visualizador personalizado, implementado por um avaliador de expressão.|  
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Retorna um número de 32 bits que representa o número de slot desejado se esta propriedade representa um endereço local do código gerenciado.|  
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Retorna uma cadeia de caracteres que contém a assinatura da variável associada ao objeto de propriedade.|  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
