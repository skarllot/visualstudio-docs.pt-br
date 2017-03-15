---
title: Classe base Task | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 6c3f6238-b9f0-4325-b8b0-de61090bd0a2
caps.latest.revision: 6
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 0855e7f8eaaf26b804fbf5d10203f888cb0195fd
ms.lasthandoff: 02/22/2017

---
# <a name="task-base-class"></a>Classe base Task
Muitas tarefas, em última análise, herdam a classe <xref:Microsoft.Build.Utilities.Task>. Essa classe adiciona vários parâmetros para as tarefas que derivam dela. Esses parâmetros são listados neste documento.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros dessa classe base.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Parâmetro opcional <xref:Microsoft.Build.Framework.IBuildEngine>.<br /><br /> Especifica a interface do mecanismo de build disponível para as tarefas. O mecanismo de build automaticamente define esse parâmetro para permitir que as tarefas retornem a chamada para ela.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Parâmetro opcional <xref:Microsoft.Build.Framework.IBuildEngine2>.<br /><br /> Especifica a interface do mecanismo de build disponível para as tarefas. O mecanismo de build automaticamente define esse parâmetro para permitir que as tarefas retornem a chamada para ela.<br /><br /> Esta é uma propriedade de conveniência para que os autores da tarefa herdados desta classe não precisem converter o valor de `IBuildEngine` para `IBuildEngine2`.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Parâmetro opcional<xref:Microsoft.Build.Framework.IBuildEngine3>.<br /><br /> Especifica a interface de mecanismo de build disponível para tarefas.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskHost>.<br /><br /> Especifica a instância do objeto de host (pode ser nula). O mecanismo de build define essa propriedade se o IDE do host associou um objeto de host com essa tarefa em particular.|  
|<xref:Microsoft.Build.Utilities.Task.Log%2A>|Parâmetro de somente leitura opcional <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.<br /><br /> O objeto auxiliar de registro em log.|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Tarefas](../msbuild/msbuild-tasks.md)
