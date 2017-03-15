---
title: Gerenciando os VSPackages | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 35
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
ms.openlocfilehash: 32e4aa4302f7871e71907d094c12038b00d7e6bb
ms.lasthandoff: 02/22/2017

---
# <a name="managing-vspackages"></a>Gerenciando os VSPackages
Na maioria dos casos você não precisa se preocupar em gerenciar os VSPackages, desde que os modelos de projeto e item registrar e carregar o pacote automaticamente. No entanto, em algumas circunstâncias você precisará aprender um pouco mais para gerenciar seu pacote.  
  
## <a name="using-the-experimental-instance"></a>Usando a instância experimental  
 Para obter mais informações sobre a instância experimental, consulte [a instância Experimental](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>VSPackages registrar e cancelar o registro  
 Para saber como registrar e cancelar o registro VSPackages e outros tipos de extensão, consulte [Registrando e Cancelando o registro VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Carregar um VSPackage  
 Os VSPackages pode ser definidos como autoload quando um determinado que CMDUICONTEXT GUID está ativado. Para obter mais informações, consulte [VSPackages Carregando](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Usando AsyncPackage para carregar os VSPackages em segundo plano  
 A classe AsyncPackage permite que o pacote de carregamento em um thread em segundo plano para melhor capacidade de resposta da interface do usuário no Visual Studio. Para obter mais informações, consulte [como: Use AsyncPackage a carga VSPackages no plano de fundo](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Contexto de interface de usuário baseada em regras para extensões  
 Com base em regras de contextos de interface do usuário permite que os autores de extensão definir as condições precisas sob o qual um contexto de interface do usuário é ativado e carregados VSPackages associados. Para obter mais informações, consulte [como: contexto de interface de usuário baseada em regras de uso de extensões do Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="diagnosing-extension-performance"></a>Diagnóstico de desempenho de extensão  
Extensões podem afetar o desempenho de carga de inicialização e a solução. Saiba como o impacto de extensão do Visual Studio é calculado e como ele pode ser analisado localmente para testar se uma extensão pode ser mostrada como um impacto sobre a extensão de desempenho. Para obter mais informações, consulte [como: diagnosticar extensão desempenho](how-to-diagnose-extension-performance.md). 
  
## <a name="troubleshooting-vspackages"></a>Os VSPackages de solução de problemas  
 Descubra as técnicas para VSPackages que não carregam ou está com problemas de solução de problemas: [VSPackages de solução de problemas](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Consulte também  
 [VSPackages](../extensibility/internals/vspackages.md)
