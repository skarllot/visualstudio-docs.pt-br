---
title: "Comando Inspeção Rápida | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
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
ms.openlocfilehash: d92e70d02530f8b4f4e8437fe3fca6323a88dcb7
ms.lasthandoff: 02/22/2017

---
# <a name="quick-watch-command"></a>Comando Inspeção Rápida
Exibe o texto selecionado ou especificado no campo Expressão da [Caixa de diálogo QuickWatch](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md). Você pode usar essa caixa de diálogo para calcular o valor atual de uma variável ou expressão reconhecida pelo depurador ou o conteúdo de um registro. Além disso, você pode alterar o valor de qualquer variável não const ou o conteúdo de qualquer registro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.QuickWatchq [text]  
```  
  
## <a name="arguments"></a>Arguments  
 `text`  
 Opcional. O texto a ser adicionado à caixa de diálogo **Inspeção Rápida**.  
  
## <a name="remarks"></a>Comentários  
 Se `text` for omitido, o texto selecionado atualmente ou a palavra no cursor é adicionada à janela Inspeção.  
  
## <a name="example"></a>Exemplo  
  
```  
>Debug.QuickWatch  
```  
  
## <a name="see-also"></a>Consulte também  
 [Como usar a caixa de diálogo QuickWatch](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
