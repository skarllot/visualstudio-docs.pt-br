---
title: "Comando Avaliar Instrução | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 12
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
ms.openlocfilehash: fa07b38fabc17f7cc3d18e1accd3cfce4e5de4ab
ms.lasthandoff: 02/22/2017

---
# <a name="evaluate-statement-command"></a>Comando Avaliar Instrução
Avalia e exibe a instrução fornecida.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.EvaluateStatement text   
```  
  
## <a name="arguments"></a>Arguments  
 `text`  
 Necessário. A instrução a ser avaliada.  
  
## <a name="remarks"></a>Comentários  
 A janela usada para inserir o comando **EvaluateStatement** determina se um sinal de igual (=) é interpretado como um operador de comparação ou um operador de atribuição.  
  
 Na janela **Comando**, um sinal de igual (=) é interpretado como um operador de comparação. Dessa forma, por exemplo, se os valores das variáveis `a` e `b` forem diferentes, o comando  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 retornará um valor de `false`.  
  
 Na janela **Imediato**, por outro lado, um sinal de igual (=) é interpretado como um operador de atribuição. Assim, por exemplo, o comando  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 atribuirá à variável `a` o valor da variável `b`.  
  
## <a name="example"></a>Exemplo  
  
```  
>Debug.EvaluateStatement(a+b)  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comando Imprimir](../../ide/reference/print-command.md)   
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
