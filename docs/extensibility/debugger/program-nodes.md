---
title: "Nós de programa | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
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
ms.openlocfilehash: 9ceb7ab91ff6671f408046888088256415fd0f26
ms.lasthandoff: 02/22/2017

---
# <a name="program-nodes"></a>Nós de programa
Em termos de arquitetura do depurador, uma **nó programa**:  
  
-   É uma descrição simples de um programa.  
  
-   Pode identificar em si e o processo está executando e podem ser anexado para ser desconectado da e descrevem o mecanismo de depuração (DE) que criou, se houver.  
  
-   É representado por um [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) geralmente criado por uma porta ou DE interface. Nós de programa são adicionados a uma porta chamando [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Quando um nó do programa é adicionado a uma porta, ele é adicionado ao processo que contém o programa que representa este nó do programa.  
  
 Em algum momento depois de uma sessão de depuração é iniciada, dependendo da implementação do pacote de depuração, nós de programa são usados para criar programas correspondentes. Quando um processo é consultado para seus programas, os programas são enumerados, uma para cada nó do programa.  
  
 Antes de um programa é conectado, o IDE precisa de apenas uma descrição simples do programa. Essas informações podem ser obtidas a partir do nó do programa. Depois que o programa é conectado, o IDE precisa exibir informações mais detalhadas, como uma lista de todos os threads em execução no programa. Essas informações são obtidas do próprio programa.  
  
## <a name="see-also"></a>Consulte também  
 [Programas](../../extensibility/debugger/programs.md)   
 [Processos](../../extensibility/debugger/processes.md)   
 [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
