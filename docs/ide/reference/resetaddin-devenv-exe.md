---
title: -ResetAddin (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 5
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 826740ff2c56f50426d51e91fe9ccf8cdcb99081
ms.contentlocale: pt-br
ms.lasthandoff: 05/24/2017

---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
Remove comandos e comando da interface do usuário associado ao Suplemento especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>Arguments  
 `AddIn`  
 Opcional. O nome de comando do Suplemento.  
  
## <a name="remarks"></a>Comentários  
 Por padrão, o nome do comando do suplemento é igual a *\<AddInSolutionName>*.Connect*.\<AddInSolutionName>* e aparece no Connect.cs como o parâmetro `commandName` do método `Exec`. Você também pode verificar o nome do comando começando a digitar o nome do suplemento na janela Comandos no Visual Studio e usando o IntelliSense para preencher o restante.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir inicia o Visual Studio e impede o suplemento `MyAddin` de ser executado na inicialização.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>Consulte também  
 [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)
