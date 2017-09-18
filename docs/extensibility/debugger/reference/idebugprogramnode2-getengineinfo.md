---
title: IDebugProgramNode2::GetEngineInfo | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
caps.latest.revision: 13
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
ms.openlocfilehash: 9edcd91399a2557e7d674ff56d6dc9531c07262e
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
Obtém o nome e o identificador do mecanismo de depuração (DE) executando um programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetEngineInfo (   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```c#  
int GetEngineInfo(  
   out string pbstrEngine,   
   out Guid pguidEngine  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrEngine`  
 [out] Retorna o nome do DE execução do programa (específico do C++: isso pode ser um ponteiro nulo, indicando que o chamador não está interessado no nome do mecanismo).  
  
 `pguidEngine`  
 [out] Retorna o identificador global exclusivo do DE execução do programa (específico do C++: isso pode ser um ponteiro nulo, indicando que o chamador não está interessado no GUID do mecanismo de).  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
