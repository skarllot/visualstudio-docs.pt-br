---
title: "A instância Experimental | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 36
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
ms.openlocfilehash: 74c15636cd5a6d91bddcdc606de2a194d71c99e5
ms.lasthandoff: 02/22/2017

---
# <a name="the-experimental-instance"></a>A instância Experimental
Para proteger seu ambiente de desenvolvimento do Visual Studio de aplicativos não testados que alterá-la, o VSSDK fornece um espaço experimental que você pode usar para testar. Desenvolver novos aplicativos usando o Visual Studio como de costume, mas você pode executá-los usando essa instância experimental.  
  
 Cada aplicativo que tenha um pacote VSIX inicia a instância experimental do Visual Studio no modo de depuração.  
  
 Se você deseja iniciar a instância experimental do Visual Studio fora de uma solução específica, execute o seguinte comando na janela de comando:  
  
 "*\<Caminho de instalação do visual studio >*\Common7\IDE\devenv.exe" RootSuffix Exp  
  
> [!NOTE]
>  A instância experimental é gravada no registro sob o `<version number>Exp` e `<version number>Exp_Config` nós. Por exemplo é a área de registro experimental do Visual Studio 2015  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` e `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 É recomendável que você execute sua extensão na instância experimental enquanto ele estiver sendo desenvolvido. Quando você implanta a extensão, ele é executado na instância de desenvolvimento. Para obter mais informações sobre o registro de aplicativos, consulte [VSPackages registrar](../extensibility/internals/registering-vspackages.md).
