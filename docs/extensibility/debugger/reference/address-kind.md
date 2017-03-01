---
title: ADDRESS_KIND | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
caps.latest.revision: 8
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
ms.openlocfilehash: 12446992390bbe63b8ced91b730f9721c3e2e5ef
ms.lasthandoff: 02/22/2017

---
# <a name="addresskind"></a>ADDRESS_KIND
Especifica os tipos de endereços.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
typedef DWORD ADDRESS_KIND;  
```  
  
```c#  
public enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
```  
  
## <a name="terms"></a>Termos  
 ADDRESS_KIND_NATIVE  
 Um endereço nativo, representado pelo [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) estrutura.  
  
 ADDRESS_KIND_UNMANAGED_THIS_RELATIVE  
 Um endereço não gerenciado relativo a um `this` (`Me` no Visual Basic) ponteiro e são representados pelo [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) estrutura.  
  
 ADDRESS_KIND_UNMANAGED_PHYSICAL  
 Um endereço físico não gerenciado, representado pelo [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) estrutura.  
  
 ADDRESS_KIND_METHOD  
 Um método de uma classe, representado pelo [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) estrutura.  
  
 ADDRESS_KIND_FIELD  
 Um campo de uma classe, representado pelo [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) estrutura.  
  
 ADDRESS_KIND_LOCAL  
 O endereço é para uma variável local e é representado pelo [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) estrutura.  
  
 ADDRESS_KIND_PARAM  
 Um parâmetro de método ou função, representado pelo [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) estrutura.  
  
 ADDRESS_KIND_ARRAYELEM  
 Um elemento de matriz, representado pelo [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) estrutura.  
  
 ADDRESS_KIND_RETVAL  
 Um valor de retorno, representado pelo [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) estrutura.  
  
## <a name="remarks"></a>Comentários  
 O [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) método retorna o [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) estrutura que contém uma união de estruturas possíveis, o [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) estrutura. O `dwKind` campo o `DEBUG_ADDRESS_UNION` estrutura mantém o `ADDRESS_KIND` valor e descreve como interpretar o campo de união.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
