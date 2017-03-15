---
title: METADATA_ADDRESS_RETVAL | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
caps.latest.revision: 6
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
ms.openlocfilehash: 7effb37c1f2a654015756bb69c5f4975e9d62949
ms.lasthandoff: 02/22/2017

---
# <a name="metadataaddressretval"></a>METADATA_ADDRESS_RETVAL
Esta estrutura representa um valor de retorno de um método ou função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_RETVAL {  
   _mdToken tokMethod;  
   DWORD    dwCorType;  
   DWORD    dwSigSize;  
   BYTE     rgSig[10];  
} METADATA_ADDRESS_RETVAL;  
```  
  
```c#  
public struct METADATA_ADDRESS_RETVAL {  
   public int    tokMethod;  
   public uint   dwCorType;  
   public uint   dwSigSize;  
   public byte[] rgSig;  
}  
```  
  
## <a name="terms"></a>Termos  
 tokMethod  
 A ID do método esse valor de retorno é para.  
  
 dwCorType  
 O tipo base do valor de retorno. Este é um valor da `CorElementType` enumeração definida no [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] arquivo de corhdr. h SDK.  
  
 dwSigSize  
 O tamanho da assinatura do valor de retorno (conforme armazenado em `rgSig`).  
  
 rgSig  
 Uma matriz de bytes que formam a assinatura do valor de retorno.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é parte da união no [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) estrutura quando o `dwKind` campo o `DEBUG_ADDRESS_UNION` estrutura é definida como `ADDRESS_KIND_RETVAL` (um valor da [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumeração).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
