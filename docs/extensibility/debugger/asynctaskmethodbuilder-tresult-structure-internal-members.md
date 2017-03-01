---
title: AsyncTaskMethodBuilder&lt;TResult&gt; estrutura - membros internos | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
caps.latest.revision: 4
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
ms.openlocfilehash: 23e64a602f074a13785934ca21048991ae3828f9
ms.lasthandoff: 02/22/2017

---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder&lt;TResult&gt; estrutura - membros internos
Este tópico descreve os membros internos da <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>classe.</xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> Para obter informações gerais sobre essa classe, consulte o <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>tópico de referência.</xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>  
  
 **Namespace:**<xref:System.Runtime.CompilerServices?displayProperty=fullName></xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib. dll)  
  
 Porque você não pode acessar esses membros internos do .NET Framework, a sintaxe a seguir é fornecida idioma intermediário comum (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Membros internos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Propriedade ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Obtém um objeto que pode ser usado para identificar com exclusividade este construtor para o depurador.|  
|[campo m_task](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Representa a inicialização ociosa criado a tarefa.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601></xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>   
 [Elementos internos de extensões paralelas para o .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
