---
title: IDebugPortEx2::LaunchSuspended | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
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
ms.openlocfilehash: cc2c2ec3817e738bbdd3f47a6560f2a5542ee57e
ms.lasthandoff: 02/22/2017

---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
Um arquivo executável é iniciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT LaunchSuspended(   
   LPCOLESTR        pszExe,  
   LPCOLESTR        pszArgs,  
   LPCOLESTR        pszDir,  
   BSTR             bstrEnv,  
   DWORD            hStdInput,  
   DWORD            hStdOutput,  
   DWORD            hStdError,  
   IDebugProcess2** ppPortProcess  
);  
```  
  
```c#  
int LaunchSuspended(   
   string             pszExe,  
   string             pszArgs,  
   string             pszDir,  
   string             bstrEnv,  
   uint               hStdInput,  
   uint               hStdOutput,  
   uint               hStdError,  
   out IDebugProcess2 ppPortProcess  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszExe`  
 [in] O nome do executável a ser iniciado. Isso pode ser um caminho completo ou relativo para o diretório de trabalho especificado no `pszDir` parâmetro.  
  
 `pszArgs`  
 [in] Os argumentos para passar para o executável. Pode ser um valor nulo se não houver nenhum argumento.  
  
 `pszDir`  
 [in] O nome do diretório de trabalho usado pelo executável. Pode ser um valor nulo se nenhum diretório de trabalho é necessário.  
  
 `bstrEnv`  
 [in] Bloco de ambiente de cadeias de caracteres terminada em nulo, seguido por um terminador nulo adicional.  
  
 `hStdInput`  
 [in] Identificador para um fluxo de entrada alternativo. Pode ser 0 se o redirecionamento não é necessário.  
  
 `hStdOutput`  
 [in] Identificador para um fluxo de saída alternativo. Pode ser 0 se o redirecionamento não é necessário.  
  
 `hStdError`  
 [in] Identificador para um fluxo de saída de erro alternativa. Pode ser 0 se o redirecionamento não é necessário.  
  
 `ppPortProcess`  
 [out] Retorna um [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) objeto que representa o processo iniciado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método deve iniciar o processo de forma que ele está suspenso e não executar qualquer código. O [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) método é chamado para continuar o processo.  
  
 Um programa também pode ser iniciado de um mecanismo de depuração. Para obter detalhes, consulte [iniciando um programa](../../../extensibility/debugger/launching-a-program.md).  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [Iniciando um programa](../../../extensibility/debugger/launching-a-program.md)
