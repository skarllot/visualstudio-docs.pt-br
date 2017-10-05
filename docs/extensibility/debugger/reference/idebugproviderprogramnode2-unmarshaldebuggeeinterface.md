---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 1801f2df2dfff7667e8a9991892b3218dc3bb71a
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Obtém uma interface especificada nos limites do processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```csharp  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `riid`  
 [in] GUID da interface para obter.  
  
 `ppvObject`  
 [out] Retorna o objeto que implementa a interface desejada. [C++] isso pode ser convertido diretamente para o tipo de interface desejado. [C#] usam o <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> método para obter a interface desejada.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é usado quando o mecanismo de depuração estiver em execução no [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] espaço de processo e o programa que está sendo depurado está em execução em seu próprio espaço de processo.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
