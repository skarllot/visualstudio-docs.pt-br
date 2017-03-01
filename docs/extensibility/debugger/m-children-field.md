---
title: m_children campo | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 58bad54ce978e6572529f8ff72746775d77ad1cf
ms.lasthandoff: 02/22/2017

---
# <a name="mchildren-field"></a>m_children campo
A lista de tarefas filho que estão registrados com essa tarefa.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName></xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib. dll)  
  
 Porque você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida idioma intermediário comum (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Comentários  
 Enquanto a tarefa estiver em execução, somente o thread que executa a tarefa deve acessar essa matriz.  
  
 Se a tarefa for concluída, outros threads podem acessar este campo enquanto não adiciona nada a ele ou remover nada dela.  
  
## <a name="see-also"></a>Consulte também  
 [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)
