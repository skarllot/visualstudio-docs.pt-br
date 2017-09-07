---
title: METADATA_TYPE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
caps.latest.revision: 7
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
ms.openlocfilehash: f2fd53d0e6a0b92a3c8c7b030d503578aa9d2f98
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="metadatatype"></a>METADATA_TYPE
Essa estrutura Especifica informações sobre um tipo de campo obtido de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _tagTYPE_METADATA {  
   ULONG32  ulAppDomainID;  
   GUID     guidModule;  
   _mdToken tokClass;  
} METADATA_TYPE;  
```  
  
```csharp  
public struct METADATA_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public int  tokClass;  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 ulAppDomainID  
 ID do aplicativo do qual o símbolo foi originada. Isso é usado para identificar exclusivamente uma instância do aplicativo.  
  
 guidModule  
 O GUID do módulo que contém esse campo.  
  
 tokClass  
 A ID do token metadados desse tipo.  
  
 [C++] `_mdToken` é um `typedef` para 32 bits `int`.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é exibido como parte da união no [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) estrutura quando o `dwKind` campo do `TYPE_INFO` estrutura é definida como `TYPE_KIND_METADATA` (um valor da [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) enumeração).  
  
 O `tokClass` valor é um token de metadados que identifica exclusivamente um tipo. Para obter detalhes sobre como interpretar os bits superiores da ID do token de metadados, consulte o `CorTokenType` enumeração no arquivo corhdr no [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
