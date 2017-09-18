---
title: IDebugMethodField::EnumLocals | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
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
ms.openlocfilehash: bce049a0aa69bcdbbcd16688dc811a49fd595857
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Cria um enumerador para variáveis locais selecionados do método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT EnumLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pAddress`  
 [in] Um [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objeto que representa o endereço de depuração que seleciona o contexto ou escopo do qual obter os locais.  
  
 `ppLocals`  
 [out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa uma lista das locais; caso contrário, retornará um valor nulo se não houver nenhum locais.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, Retorna S_OK ou retorna S_FALSE se não houver nenhum locais. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Somente as variáveis definidas dentro do bloco que contém o endereço de depuração determinado são enumeradas. Se todos os locais, incluindo qualquer locais geradas pelo compilador são necessários, chame o [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) método.  
  
 Um método pode conter vários contextos ou blocos de escopo. Por exemplo, o seguinte método forçado contém três escopos, os dois blocos internos e o corpo do método em si.  
  
```c#  
public void func(int index)  
{  
    // Method body scope  
    int a = 0;  
    if (index == 1)  
    {  
        // Inner scope 1  
        int temp1 = a;  
    }  
    else  
    {  
        // Inner scope 2  
        int temp2 = a;  
    }  
}  
```  
  
 O [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) objeto representa o `func` método em si. Chamando o `EnumLocals` método com um [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) definido como o `Inner Scope 1` endereço retorna uma enumeração que contém o `temp1` variável, por exemplo.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
