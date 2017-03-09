---
title: Comando Ir para | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 10
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
ms.openlocfilehash: f977d4e63b015ec83ed0a189642caf2e74fcbb20
ms.lasthandoff: 02/22/2017

---
# <a name="go-to-command"></a>Comando Ir para
Move o cursor para a linha especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Edit.GoTo [linenumber]  
```  
  
## <a name="arguments"></a>Arguments  
 `linenumber`  
 Opcional. Um inteiro que representa o número da linha para a qual ir.  
  
## <a name="remarks"></a>Comentários  
 A numeração de linha começa em um. Se o valor de `linenumber` for menor que um, a primeira linha será exibida. Se o valor de `linenumber` for maior que o número da última linha, a última linha será exibida.  
  
 Se um valor para `linenumber` não for especificado, a caixa de diálogo **Ir para a Linha** será exibida.  
  
 O alias para esse comando é GoToLn.  
  
## <a name="example"></a>Exemplo  
  
```  
>Edit.GoTo 125  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
