---
title: Configurar destinos e tarefas | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
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
ms.openlocfilehash: f56c9e92e1e0cdd0d703fdd0a624081be1f9b7a4
ms.lasthandoff: 02/22/2017

---
# <a name="configuring-targets-and-tasks"></a>Configurando destinos e tarefas
Você pode configurar destinos do MSBuild e tarefas para execução fora de processo com o MSBuild para que você possa direcionar contextos diferentes daqueles que você está executando. Por exemplo, você pode direcionar um aplicativo do .NET Framework 2.0 de 32 bits, enquanto o computador de desenvolvimento está em execução em um sistema de operacional de 64 bits do .NET Framework 4.5. Você também pode direcionar os computadores que executam o .NET Framework 4 ou anterior. A combinação de 32 ou 64 bits e a versão específica do .NET Framework é conhecida como o *contexto de destino*.  
  
## <a name="installation"></a>Instalação  
 O .NET Framework 4.5 e 4.5.1 substitui o CLR (Common Language Runtime), os destinos, as tarefas e as ferramentas do .NET Framework 4 sem renomeá-los. O .NET Framework 4.5.1 é instalado como parte do [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)].  
  
 Se desejar instalar o MSBuild separadamente do Visual Studio, baixe o pacote de instalação em [Download do MSBuild](http://go.microsoft.com/fwlink/?LinkId=309745). Você também deve instalar as versões do .NET Framework que deseja usar.  
  
## <a name="targets-and-tasks"></a>Destinos e tarefas  
 O MSBuild executa certas tarefas de build fora do processo para destinar para um conjunto maior de contextos.  Por exemplo, um MSBuild de 32 bits pode executar uma tarefa de build em um processo de 64 bits para destinar um computador de 64 bits. Isso é controlado pelos argumentos `UsingTask` e parâmetros `Task`. Os destinos instalados pelo .NET Framework 4.5 definem esses parâmetros e argumentos e nenhuma alteração é necessária para compilar aplicativos para os vários contextos de destino.  
  
 Se quiser criar seu próprio contexto de destino, você deverá definir esses parâmetros e argumentos adequadamente. Examine o arquivo Microsoft.Common.targets do .NET Framework 4.5 e o arquivo Microsoft.Common.Tasks para obter exemplos.  Para obter informações sobre como criar uma tarefa personalizada que possa trabalhar com vários contextos de destino ou modificar tarefas existentes, consulte [Como configurar destinos e tarefas](../msbuild/how-to-configure-targets-and-tasks.md).  
  
## <a name="see-also"></a>Consulte também  
 [Multiplataforma](../msbuild/msbuild-multitargeting-overview.md)
