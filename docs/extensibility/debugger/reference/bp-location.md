---
title: BP_LOCATION | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
caps.latest.revision: 11
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
ms.openlocfilehash: a91abf687e12ffaf1f56d45ede59c20a1e72d614
ms.lasthandoff: 02/22/2017

---
# <a name="bplocation"></a>BP_LOCATION
Especifica o tipo de estrutura usada para descrever o local do ponto de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
typedef struct _BP_LOCATION {  
   BP_LOCATION_TYPE bpLocationType;  
   union {  
      BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;  
      BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;  
      BP_LOCATION_CODE_CONTEXT     bplocCodeContext;  
      BP_LOCATION_CODE_STRING      bplocCodeString;  
      BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;  
      BP_LOCATION_DATA_STRING      bplocDataString;  
      BP_LOCATION_RESOLUTION       bplocResolution;  
      DWORD                        unused;  
   } bpLocation;  
} BP_LOCATION;  
```  
  
```c#  
public struct BP_LOCATION {  
   public uint   bpLocationType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public IntPtr unionmember4;  
};  
```  
  
## <a name="members"></a>Membros  
 `bpLocationType`  
 Um valor da [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) enumeração usada para interpretar o `bpLocation` união ou `unionmemberX` membros.  
  
 `bpLocation`.`bplocCodeFileLine`  
 [C++] Contém o [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) estrutura se `bpLocationType`  =  `BPLT_CODE_FILE_LINE`.  
  
 `bpLocation.bplocCodeFuncOffset`  
 [C++] Contém o [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) estrutura se `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET`.  
  
 `bpLocation.bplocCodeContext`  
 [C++] Contém o [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) estrutura se `bpLocationType`  =  `BPLT_CODE_CONTEXT`.  
  
 `bpLocation.bplocCodeString`  
 [C++] Contém o [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) estrutura se `bpLocationType`  =  `BPLT_CODE_STRING`.  
  
 `bpLocation.bplocCodeAddress`  
 [C++] Contém o [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) estrutura se `bpLocationType`  =  `BPLT_CODE_ADDRESS`.  
  
 `bpLocation.bplocDataString`  
 [C++] Contém o [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) estrutura se `bpLocationType`  =  `BPLT_DATA_STRING`.  
  
 `bpLocation.bplocResolution`  
 [C++] Contém o [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) estrutura se `bpLocationType`  =  `BPLT_RESOLUTION`.  
  
 `unionmember1`  
 [Apenas c#] Consulte os comentários sobre como interpretar.  
  
 `unionmember2`  
 [Apenas c#] Consulte os comentários sobre como interpretar.  
  
 `unionmember3`  
 [Apenas c#] Consulte os comentários sobre como interpretar.  
  
 `unionmember4`  
 [Apenas c#] Consulte os comentários sobre como interpretar.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é membro do [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estruturas.  
  
 [Apenas c#] O `unionmemberX` membros são interpretados de acordo com a tabela a seguir. Examine a coluna à esquerda para a `bpLocationType` valor então procure pelas colunas para determinar o que cada `unionmemberX` membro representa e empacotar o `unionmemberX` adequadamente. Veja o exemplo de um modo para interpretar uma parte dessa estrutura no c#.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPLT_CODE_FILE_LINE`|`string`(um contexto)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|  
|`BPLT_CODE_FUNC_OFFSET`|`string`(um contexto)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|  
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|  
|`BPLT_CODE_STRING`|`string`(um contexto)|`string`(expressão condicional)|-|-|  
|`BPLT_CODE_ADDRESS`|`string`(um contexto)|`string`(módulo URL)|`string`(nome da função)|`string`(endereço)|  
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string`(um contexto)|`string`(expressão de dados)|`uint`(número de elementos)|  
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como interpretar o `BP_LOCATION` estrutura em c# para o `BPLT_DATA_STRING` tipo. Esse tipo específico mostra como interpretar os quatro `unionmemberX` membros em todos os formatos possíveis (objeto, cadeia de caracteres e número).  
  
```c#  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(BP_LOCATION bp)  
        {  
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)  
            {  
                 IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);  
                 string context = Marshal.PtrToStringBSTR(bp.unionmember2);  
                 string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)   
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)   
 [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)   
 [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)   
 [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)   
 [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)
