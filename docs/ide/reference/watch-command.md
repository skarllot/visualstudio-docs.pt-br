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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: bdca63e08a164afe507b9c3964356593839b6987
ms.lasthandoff: 02/22/2017

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
 [Como editar um valor em uma janela variável](../Topic/How%20to:%20Edit%20a%20Value%20in%20a%20Variable%20Window.md)   
 [Como usar a caixa de diálogo QuickWatch](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
