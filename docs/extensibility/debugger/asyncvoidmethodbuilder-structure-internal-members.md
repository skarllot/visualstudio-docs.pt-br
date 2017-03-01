---
title: Estrutura AsyncVoidMethodBuilder - membros internos | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
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
ms.openlocfilehash: b59c4e233ee0da8465b92b5db7dbbc6890ae94a5
ms.lasthandoff: 02/22/2017

---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>Estrutura AsyncVoidMethodBuilder - membros internos
Este tópico descreve os membros internos da <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>classe.</xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> Para obter informações gerais sobre essa classe, consulte o <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>tópico de referência.</xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>  
  
 **Namespace:**<xref:System.Runtime.CompilerServices?displayProperty=fullName></xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib. dll)  
  
 Porque você não pode acessar esses membros internos do .NET Framework, a sintaxe a seguir é fornecida idioma intermediário comum (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Membros internos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Propriedade ObjectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Obtém um objeto que pode ser usado para identificar com exclusividade este construtor para o depurador.|  
|[campo m_objectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Representa o objeto de inicialização ociosa usado pelo depurador para identificar exclusivamente este construtor.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder></xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [Elementos internos de extensões paralelas para o .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
