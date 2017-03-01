---
title: IDebugContainerField::EnumFields | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
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
ms.openlocfilehash: d0b126d5bc2de796cb9d9afc2e5ff9a832c79bab
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Cria um enumerador para os campos do contêiner.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT EnumFields(   
   FIELD_KIND         dwKindFilter,  
   FIELD_MODIFIERS    dwModifiersFilter,  
   LPCOLESTR          pszNameFilter,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumFields(  
   enum_ FIELD_KIND      dwKindFilter,   
   enum_ FIELD_MODIFIERS dwModifiersFilter,   
   string                pszNameFilter,   
   NAME_MATCH            nameMatch,   
   out IEnumDebugFields  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwKindFilter`  
 [in] Uma combinação de [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) constantes que selecione os campos a serem enumerados. Tipos de campo podem descrever os tipos de armazenamento, como classe ou informações primitivas ou específicas, como local, parâmetro ou ponteiro "this".  
  
 `dwModifiersFilter`  
 [in] Uma combinação de [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) constantes que selecione os campos a serem enumerados. Modificadores de campo podem ser permissões de acesso, como público ou particular ou informações de armazenamento, como virtual, estático ou final.  
  
 `pszNameFilter`  
 [in] O nome do campo a ser enumerado. Isso pode ser um valor nulo se todos os campos devem ser retornados.  
  
 `nameMatch`  
 [in] Um valor a partir de [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) enumeração que controla se a pesquisa diferencia maiusculas de minúsculas ou não.  
  
 `ppEnum`  
 [out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa a lista de campos. Retorna um valor nulo se não houver nenhum campo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, Retorna S_OK ou S_FALSE se nenhum campo. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O `dwKindFilter`, `dwModifiersFilter`, e `pszNameFilter` parâmetros podem ser combinados, por exemplo, para selecionar todos os métodos públicos virtual chamados "MyMethod".  
  
## <a name="see-also"></a>Consulte também  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
