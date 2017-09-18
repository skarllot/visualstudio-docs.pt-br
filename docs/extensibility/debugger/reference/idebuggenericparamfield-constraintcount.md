---
title: IDebugGenericParamField::ConstraintCount | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ConstraintCount
- IDebugGenericParamField::ConstraintCount
ms.assetid: 76bef0cb-8a3c-4ce5-87cc-1809de229f33
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
ms.openlocfilehash: c3fc025d7f85ff8b999608a9f9b3b6bad4972bec
ms.lasthandoff: 02/22/2017

---
# <a name="idebuggenericparamfieldconstraintcount"></a>IDebugGenericParamField::ConstraintCount
Retorna o número de restrições que estão associados esse parâmetro genérico.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT ConstraintCount(  
   ULONG32* pcConst  
);  
```  
  
```c#  
int ConstraintCount(  
   ref uint pcConst  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pcConst`  
 [no, out] Número de restrições que estão associados esse campo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um **CDebugGenericParamFieldType** objeto expõe o [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) interface.  
  
```cpp#  
HRESULT CDebugGenericParamFieldType::ConstraintCount(ULONG32* pcConst)  
{  
    HRESULT hr = S_OK;  
    CComPtr<IMetaDataImport> pMetadata;  
    CComPtr<IMetaDataImport2> pMetadata2;  
    HCORENUM hEnum = 0;  
    ULONG cConst = 0;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::ConstraintCount );  
  
    IfFalseGo(pcConst, E_INVALIDARG );  
    *pcConst = 0;  
    IfFailGo( m_spSH->GetMetadata( m_idModule, &pMetadata ) );  
    IfFailGo( pMetadata->QueryInterface(IID_IMetaDataImport2, (void**)&pMetadata2) );  
    IfFailGo( pMetadata2->EnumGenericParamConstraints( &hEnum,  
              m_tokParam,  
              NULL,  
              0,  
              &cConst) );  
    IfFailGo( pMetadata->CountEnum(hEnum, &cConst) );  
    pMetadata->CloseEnum(hEnum);  
    hEnum = NULL;  
  
    *pcConst = cConst;  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::ConstraintCount, hr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
