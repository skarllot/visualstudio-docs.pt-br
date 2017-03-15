---
title: IDebugProgramNode2::DetachDebugger_V7 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
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
ms.openlocfilehash: ea8843a824eb5e1cd0c7bcd658908d7cdaac98ce
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7
PRETERIDO. NÃO USE.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```c#  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Uma implementação deve retornar sempre `E_NOTIMPL`.  
  
## <a name="remarks"></a>Comentários  
  
> [!WARNING]
>  Como de [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)], esse método não é mais usado e deve retornar sempre `E_NOTIMPL`.  
  
 Esse método é chamado quando o depurador fecha inesperadamente. Quando esse método é chamado, o DE deve continuar o programa como se o usuário desanexado dele. Nenhum evento de depuração mais deve ser enviado. O programa deve estar em um estado onde ele é anexável de outra instância do depurador.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
