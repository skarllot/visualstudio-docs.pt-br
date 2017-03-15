---
title: -ResetSkipPkgs (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 3
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
ms.openlocfilehash: eb71419d10744143d246a0c0753a545fd9d8400f
ms.lasthandoff: 02/22/2017

---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
Limpa todas as opções para ignorar o carregamento adicionadas a VSPackages por usuários que desejam evitar o carregamento de VSPackages com problemas, e inicia o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Devenv /ResetSkipPkgs  
```  
  
## <a name="remarks"></a>Comentários  
 A presença de uma marcação SkipLoading desabilita o carregamento de um VSPackage; limpar a marcação habilita novamente o carregamento do VSPackage.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir limpa todas as marcas SkipLoading.  
  
```  
Devenv.exe /ResetSkipPkgs  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)
