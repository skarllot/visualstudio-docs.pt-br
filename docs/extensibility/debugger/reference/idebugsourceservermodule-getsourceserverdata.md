---
title: IDebugSourceServerModule::GetSourceServerData | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugSourceServerModule::GetSourceServerData
ms.assetid: f15d86aa-1bd9-4b16-a64a-21b01c27db2e
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
ms.openlocfilehash: 2c285bb3edd258e5a354883e81074589b0abce86
ms.lasthandoff: 02/22/2017

---
# <a name="idebugsourceservermodulegetsourceserverdata"></a>IDebugSourceServerModule::GetSourceServerData
Recupera uma matriz de informações do servidor de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetSourceServerData(  
   ULONG* pDataByteCount,   
   BYTE** ppData  
);  
```  
  
```c#  
public int GetSourceServerData(  
   out uint  pDataByteCount,   
   out int[] ppData  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pDataByteCount`  
 [out] Número de bytes na matriz de dados.  
  
 `ppData`  
 [out] Referência para a matriz de dados.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um **CModule** objeto expõe o [IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md) interface.  
  
```cpp#  
HRESULT CModule::GetSourceServerData(ULONG* pDataByteCount, BYTE** ppData)  
{  
    HRESULT hr = S_OK;  
    CComPtr<ISymUnmanagedReader> pSymReader;  
    CComPtr<ISymUnmanagedSourceServerModule> pSourceServerModule;  
  
    IfFalseGo( pDataByteCount && ppData, E_INVALIDARG );  
    *pDataByteCount = 0;  
    *ppData = NULL;  
  
    IfFailGo( this->GetUnmanagedSymReader( &pSymReader ) );  
    IfFailGo( pSymReader->QueryInterface( &pSourceServerModule ) );  
  
    IfFailGo( pSourceServerModule->GetSourceServerData( pDataByteCount, ppData ) );  
  
Error:  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)
