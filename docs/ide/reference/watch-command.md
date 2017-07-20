---
title: "Comando de Inspeção | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 11
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
ms.openlocfilehash: bf91686a212551ef4b760d5bb2740a14f8495a1b
ms.contentlocale: pt-br
ms.lasthandoff: 05/24/2017

---
# <a name="watch-command"></a>Comando Inspecionar
Cria e abre uma instância especificada de uma janela **Inspeção**. Você pode usar uma janela **Inspeção** para calcular os valores de variáveis, expressões e registros, para editar esses valores e para salvar os resultados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.Watch[index]  
```  
  
## <a name="arguments"></a>Arguments  
 `index`  
 Necessário. O número de instância da janela Inspeção.  
  
## <a name="remarks"></a>Comentários  
 O `index` deve ser um inteiro. Os valores válidos são 1, 2, 3 ou 4.  
  
## <a name="example"></a>Exemplo  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>Consulte também  
 [Janelas automáticas e locais](../../debugger/autos-and-locals-windows.md)   
 [Definir uma inspeção nas variáveis usando as janelas Inspeção e QuickWatch no Visual Studio](../../debugger/watch-and-quickwatch-windows.md)   
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
