---
title: IDebugGenericParamField::GetIndex | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugGenericParamField::GetIndex
ms.assetid: 8e0bdb26-1247-44d9-8d80-ec6e35187fb4
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
ms.openlocfilehash: f39817507e85fe61b075dd46e6478d5683f7de63
ms.lasthandoff: 02/22/2017

---
# <a name="idebuggenericparamfieldgetindex"></a>IDebugGenericParamField::GetIndex
Recupera o índice do parâmetro genérico.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetIndex(  
   DWORD* pIndex  
);  
```  
  
```c#  
int GetIndex(  
   out uint pIndex  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pIndex`  
 [out] Valor de índice do parâmetro genérico.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Por exemplo, para Dictionary(K,V), K é o índice 0, V é o índice 1.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um **CDebugGenericParamFieldType** objeto expõe o [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) interface.  
  
```cpp#  
HRESULT CDebugGenericParamFieldType::GetIndex(DWORD* pIndex)  
{  
    HRESULT hr = S_OK;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::GetIndex );  
  
    IfFalseGo(pIndex, E_INVALIDARG );  
    IfFailGo( this->LoadProps() );  
    *pIndex = m_index;  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::GetIndex, hr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
