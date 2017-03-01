---
title: Estrutura AsyncTaskMethodBuilder - membros internos | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: 5
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
ms.openlocfilehash: b81aebf18d9e52d9dba51ac05a3880d146e3cddc
ms.lasthandoff: 02/22/2017

---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>Estrutura AsyncTaskMethodBuilder - membros internos
Este tópico descreve os membros internos da <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>classe.</xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> Para obter informações gerais sobre essa classe, consulte o <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>tópico de referência.</xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>  
  
 **Namespace:**<xref:System.Runtime.CompilerServices?displayProperty=fullName></xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib. dll)  
  
 Porque você não pode acessar esses membros internos do .NET Framework, a sintaxe a seguir é fornecida idioma intermediário comum (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Membros internos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Propriedade ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Obtém um objeto que pode ser usado para identificar com exclusividade este construtor para o depurador.|  
|[campo m_builder](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Representa o objeto construtor genérico ao qual essa instância não-genérica delegados.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder></xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [Elementos internos de extensões paralelas para o .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
