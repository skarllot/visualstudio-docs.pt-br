---
title: IDebugComPlusSymbolProvider::GetArrayTypeFromAddress | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetArrayTypeFromAddress
- IDebugComPlusSymbolProvider::GetArrayTypeFromAddress
ms.assetid: cc0c53f1-8c0f-49fa-8dbe-bc155e9ce0ef
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
ms.openlocfilehash: af2f33990d0545534ba50f198451b0cb227241a2
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcomplussymbolprovidergetarraytypefromaddress"></a>IDebugComPlusSymbolProvider::GetArrayTypeFromAddress
Recupera informações sobre a matriz especificada, dada seu endereço de depuração de tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[C++]  
HRESULT GetArrayTypeFromAddress(  
   IDebugAddress* pAddress,  
   BYTE*          pSig,  
   DWORD          dwSigLength,  
   IDebugField**  ppField  
);  
```  
  
```  
[C#]  
int GetArrayTypeFromAddress(  
   IDebugAddress   pAddress,  
   int[]           pSig,  
   uint            dwSigLength,  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pAddress`  
 [in] O endereço de depuração é representado por um [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.  
  
 `pSig`  
 [in] A matriz para examinar.  
  
 `dwSigLength`  
 [in] Comprimento em bytes da `pSig` matriz.  
  
 `ppField`  
 [out] Retorna o tipo de matriz, conforme representado por um [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) interface.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um **CDebugSymbolProvider** objeto expõe o [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interface.  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetArrayTypeFromAddress(  
    IDebugAddress *pAddress,  
    BYTE *pSig,  
    DWORD dwSigLength,  
    IDebugField **ppField)  
{  
    HRESULT hr = E_FAIL;  
    CDEBUG_ADDRESS da;  
    CDebugGenericParamScope* pGenScope = NULL;  
  
    METHOD_ENTRY( CDebugDynamicFieldSymbol::GetArrayTypeFromAddress );  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidWritePtr(ppField, IDebugField*));  
  
    IfFailGo( pAddress->GetAddress(&da) );  
  
    if ( S_OK == hr )  
    {  
        IfNullGo( pGenScope = new CDebugGenericParamScope(da.GetModule(), da.tokClass, da.GetMethod()), E_OUTOFMEMORY );  
  
        IfFailGo( this->CreateType((const COR_SIGNATURE*)(pSig), dwSigLength, da.GetModule(), mdMethodDefNil, pGenScope, ppField) );  
    }  
  
Error:  
  
    METHOD_EXIT( CDebugDynamicFieldSymbol::GetArrayTypeFromAddress, hr );  
    RELEASE( pGenScope );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
