---
title: IDebugProgramPublisher2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 242221c8cc3ffad51fa21f71d6209208b58ae6e6
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Essa interface permite que um mecanismo de depuração (DE) ou fornecedores de porta personalizada para registrar os programas de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugProgramPublisher2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O Visual Studio implementa essa interface para registrar os programas que está sendo depurados para torná-las visíveis para depuração entre vários processos.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chame COM `CoCreateInstance` funcionar com `CLSID_ProgramPublisher` obter interface (veja o exemplo). Um fornecedor de porta personalizada ou um DE usa essa interface para registrar nós de programa que representam os programas que estiverem sendo depurados.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Essa interface implementa os métodos a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Disponibiliza um nó de programa para DEs e a sessão de depuração manager (SDM).|  
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Remove um nó de programa para que ele não está mais disponível.|  
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Disponibiliza um programa para DEs e o SDM.|  
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Remove um programa para que ele não está mais disponível.|  
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Define um sinalizador que indica que um depurador está presente.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface disponibiliza programas e nós de programa (ou seja, "publique") para uso por DEs e o Gerenciador de sessão de depuração (SDM). Para acessar programas publicados e nós de programa, use o [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interface. Este é o único modo que o Visual Studio pode reconhecer que um programa está sendo depurado.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como instanciar o Editor de programa e registrar um nó de programa. Isso é obtido do Tutorial, [publicando o nó de programa](http://msdn.microsoft.com/en-us/d0100e02-4e2b-4e72-9e90-f7bc11777bae).  
  
```cpp  
// This is how m_srpProgramPublisher is defined in the class definition:  
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.  
  
void CProgram::Start(IDebugEngine2 * pEngine)  
{  
    m_spEngine = pEngine;  
  
    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);  
    if ( FAILED(hr) )  
    {  
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);  
        return;  
    }  
  
    // Register ourselves with the program publisher. Note that  
    // CProgram implements the IDebgProgramNode2 interface, hence  
    // the static cast on "this".  
    hr = m_srpProgramPublisher->PublishProgramNode(  
        static_cast<IDebugProgramNode2*>(this));  
    if ( FAILED(hr) )  
    {  
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);  
        m_srpProgramPublisher.Release();  
        return;  
    }  
  
    ATLTRACE("Added program node.\n");  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
