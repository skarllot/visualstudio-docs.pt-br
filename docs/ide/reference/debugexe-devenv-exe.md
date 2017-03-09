---
title: -DebugExe (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 4
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
ms.openlocfilehash: d949dbd34e98e7480824ab3990093b5cd66955fb
ms.lasthandoff: 02/22/2017

---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
Abre o arquivo executável especificado a ser depurado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## <a name="arguments"></a>Arguments  
 `ExecutableFile`  
 Necessário. O caminho e o nome de um arquivo .exe.  
  
 Se o arquivo .exe não for encontrado ou não existir, nenhum aviso nem erro será exibido, e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] iniciará normalmente.  
  
## <a name="remarks"></a>Comentários  
 Quaisquer cadeias de caracteres após o parâmetro `ExecutableFile` são passadas para esse arquivo como argumentos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir abre o arquivo `MyApplication.exe` para depuração.  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)
