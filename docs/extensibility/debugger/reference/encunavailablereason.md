---
title: EncUnavailableReason | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
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
ms.openlocfilehash: db9d76add958ecac1b97479da544a1515e2ca385
ms.lasthandoff: 02/22/2017

---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!`Representa os motivos que **editar e continuar** não está disponível.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```c#  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 ENCUN_NONE  
 Nenhum motivo específico por que editar e continuar não está disponível.  
  
 ENCUN_INTEROP  
 Editar e continuar não está disponível durante uma chamada de interoperabilidade.  
  
 ENCUN_SQLCLR  
 Editar e continuar não está disponível durante uma chamada de procedimento SQL que usa o tempo de execução do CLR (Common Language).  
  
 ENCUN_MINIDUMP  
 Editar e continuar não está disponível durante o processamento de um minidespejo.  
  
 ENCUN_EMBEDDED  
 Editar e continuar não está disponível durante o processamento de código inserido.  
  
 ENCUN_ATTACH  
 Editar e continuar não está disponível porque a sessão foi anexada ao, não é iniciado pelo depurador.  
  
 ENCUN_WIN64  
 Editar e continuar não está disponível durante o processamento de código de 64 bits do Windows.  
  
## <a name="remarks"></a>Comentários  
 Essa enumeração é para uso interno apenas por [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]. O [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) e [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) métodos conforme implementado por um fornecedor de porta personalizada devem retornar sempre `E_NOTIMPL`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.idl  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
