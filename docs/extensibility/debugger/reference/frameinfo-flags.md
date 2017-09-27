---
title: FRAMEINFO_FLAGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
caps.latest.revision: 12
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
ms.openlocfilehash: d0b9ae5b6b9139715cd28b40dd8eae2294c507a7
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
Especifica as informações para recuperar de um objeto de quadro de pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
typedef DWORD FRAMEINFO_FLAGS;  
```  
  
```csharp  
public enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
```  
  
## <a name="members"></a>Membros  
 FIF_FUNCNAME  
 Inicializar/usar o `m_bstrFuncName` campo.  
  
 FIF_RETURNTYPE  
 Inicializar/usar o `m_bstrReturnType` campo.  
  
 FIF_ARGS  
 Inicializar/usar o `m_bstrArgs` campo.  
  
 FIF_LANGUAGE  
 Inicializar/usar o `m_bstrLanguage` campo.  
  
 FIF_MODULE  
 Inicializar/usar o `m_bstrModule` campo.  
  
 FIF_STACKRANGE  
 Inicializar/usar o `m_addrMin` e `m_addrMax` campos (intervalo de pilha).  
  
 FIF_FRAME  
 Inicializar/usar o `m_pFrame` campo.  
  
 FIF_DEBUGINFO  
 Inicializar/usar o `m_fHasDebugInfo` campo.  
  
 FIF_STALECODE  
 Inicializar/usar o `m_fStaleCode` campo.  
  
 FIF_ANNOTATEDFRAME  
 Inicializar/usar o `m_fAnnotatedFrame` campo.  
  
 FIF_DEBUG_MODULEP  
 Inicializar/usar o `m_pModule` campo.  
  
 FIF_FUNCNAME_FORMAT  
 Formata o nome da função. O resultado é retornado no `m_bstrFunName` e não há outros campos são preenchidos.  
  
 FIF_FUNCNAME_RETURNTYPE  
 Adiciona o tipo de retorno para o `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_ARGS  
 Adiciona os argumentos para o `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_LANGUAGE  
 Adiciona o idioma para o `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_MODULE  
 Adiciona o nome do módulo para o `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_LINES  
 Adiciona o número de linhas para o `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_OFFSET  
 Adiciona o `m_bstrFuncName` campo o deslocamento em bytes do início da linha se `FIF_FUNCNAME_LINES` for especificado. Se `FIF_FUNCNAME_LINES` não for especificado, ou se os números de linha não estiverem disponíveis, adiciona o deslocamento em bytes do início da função.  
  
 FIF_FUNCNAME_ARGS_TYPES  
 Adiciona o tipo de cada argumento de função para o `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_ARGS_NAMES  
 Adiciona o nome de cada argumento de função para o `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_ARGS_VALUES  
 Adiciona o valor de cada argumento de função para o `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_ARGS_ALL  
 Adiciona o tipo, o nome e o valor de todos os argumentos para o `m_bstrFuncName` campo.  
  
 FIF_ARGS_TYPES  
 Os tipos de argumento são recuperados e formatados.  
  
 FIF_ARGS_NAMES  
 Os nomes de argumento são recuperados e formatados.  
  
 FIF_ARGS_VALUES  
 Os valores de argumento são recuperados e formatados.  
  
 FIF_ARGS_ALL  
 Recuperar e formate o tipo, o nome e o valor de todos os argumentos.  
  
 FIF_ARGS_NOFORMAT  
 Especifica que os argumentos não são formatadas (por exemplo, não adicione abrindo e fechando a lista de argumentos entre parênteses nem adicionar um separador entre argumentos).  
  
 FIF_ARGS_NO_FUNC_EVAL  
 Especifica que a avaliação de função (propriedade) não deve ser usada ao recuperar valores de argumento.  
  
 FIF_FILTER_NON_USER_CODE  
 O mecanismo de depuração é filtrar quadros de código não-usuário para que eles não são incluídos.  
  
 FIF_ARGS_NO_TOSTRING  
 Não permitir `ToString()` formatação ao retornar argumentos de função ou avaliação de função.  
  
 FIF_DESIGN_TIME_EXPR_EVAL  
 Informações de quadro devem ser obtidas de domínio de aplicativo hospedado em vez do processo de hospedagem.  
  
## <a name="remarks"></a>Comentários  
 Esses sinalizadores são passados para o [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) e [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) métodos para indicar quais campos devem ser inicializados no [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estrutura ou estruturas.  
  
 Esses sinalizadores também são usados para indicar quais campos do [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estrutura são válidos e usadas quando a estrutura é retornada. Esses valores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
