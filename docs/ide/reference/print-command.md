---
title: Comando Print | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
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
ms.openlocfilehash: 78a29b7c2b1de14afd8241ffe516357c6a71b9d6
ms.lasthandoff: 02/22/2017

---
# <a name="print-command"></a>Comando Imprimir
Avalia uma expressão ou exibe o texto especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>Arguments  
 `text`  
 Necessário. A expressão a ser avaliada ou o texto a ser exibido.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar o ponto de interrogação (?) como um alias para esse comando. Assim, por exemplo, o comando  
  
```  
>Debug.Print expA  
```  
  
 também podem ser gravado  
  
```  
>? expA  
```  
  
 As duas versões desse comando retornarão o valor atual da expressão `expA`.  
  
## <a name="example"></a>Exemplo  
  
```  
>Debug.Print varA  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comando Evaluate Statement](../../ide/reference/evaluate-statement-command.md)   
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
