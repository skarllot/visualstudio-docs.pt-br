---
title: MODULE_FLAGS | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
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
ms.openlocfilehash: 31c3782eb1d6cc82a4ffea5b5b6f98c5f2829470
ms.lasthandoff: 02/22/2017

---
# <a name="moduleflags"></a>MODULE_FLAGS
Usado para descrever um módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
typedef DWORD MODULE_FLAGS;  
```  
  
```c#  
public enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
```  
  
## <a name="members"></a>Membros  
 MODULE_FLAG_NONE  
 Não especifica que nenhum módulo.  
  
 MODULE_FLAG_SYSTEM  
 Especifica um módulo do sistema.  
  
 MODULE_FLAG_SYMBOLS  
 Especifica um módulo de símbolo.  
  
 MODULE_FLAG_64BIT  
 Especifica um módulo de 64 bits.  
  
 MODULE_FLAG_OPTIMIZED  
 Especifica que o módulo foi otimizado. Esse estado é refletido no **módulos** janela.  
  
 MODULE_FLAG_UNOPTIMIZED  
 Especifica que o módulo não foi otimizado. Esse estado é refletido no **módulos** janela. Este é o estado padrão.  
  
## <a name="remarks"></a>Comentários  
 Usado para o `m_dwModuleFlags` membro do [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) estrutura.  
  
 Esses sinalizadores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
