---
redirect_url: /visualstudio/csharp-ide/refactoring-csharp
title: "Como restaurar trechos de refatoração C# | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unsafe expansion
- expansions, unsafe
ms.assetid: 12114273-7f2f-43d0-abcb-2d4711a3a68d
caps.latest.revision: 20
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
ms.sourcegitcommit: a4721d8bbd5dd6ec29f555ee8d4848ef3660243f
ms.openlocfilehash: 87ecb3149443bc90c2398b67158df35b193bcfe1
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-restore-c-refactoring-snippets"></a>Como restaurar trechos de refatoração C#
Operações de refatoração C# dependem de trechos de código encontrados no seguinte diretório:  
  
 *Diretório de instalação*\Microsoft Visual Studio 14.0\VC#\Snippets\\*ID de idioma*\Refactoring  
  
 Se esse diretório de Refatoração, ou quaisquer arquivos nesse diretório, for excluído ou corrompido, as operações de refatoração C# poderão não funcionar no IDE. Os procedimentos a seguir podem ajudá-lo a restaurar trechos de código de refatoração C#.  
  
### <a name="to-verify-c-refactoring-snippets-are-available-through-the-code-snippet-manager"></a>Para verificar se trechos de refatoração C# estão disponíveis por meio do Gerenciador de Trechos de Código  
  
1.  No menu **Ferramentas**, selecione **Gerenciador de Trecho de Código**.  
  
2.  Na caixa de diálogo **Gerenciador de Trecho de Código**, selecione **Visual C#** na lista suspensa **Linguagem**.  
  
     A pasta **Refatoração** deve aparecer na lista de pastas do modo de exibição de árvore.  
  
### <a name="to-restore-refactoring-see-comment-in-code-snippet-manager"></a>Para restaurar a refatoração, consulte o comentário no Gerenciador de Trechos de Código  
  
1.  Se a pasta **Refatoração** não aparecer na lista de pastas do modo de exibição de árvore do Gerenciador de Trechos de Código, use este procedimento para adicionar trechos de refatoração de volta ao Gerenciador de Trechos de Código.  
  
2.  No menu **Ferramentas**, selecione **Gerenciador de Trecho de Código**.  
  
3.  Na caixa de diálogo **Gerenciador de Trecho de Código**, selecione **Visual C#** na lista suspensa **Linguagem**.  
  
4.  Clique em **Adicionar**. A caixa de diálogo **Diretório de Trechos de Código**, que ajuda a localizar e especificar o diretório a adicionar de volta ao Gerenciador de Trechos de Código, é exibida.  
  
5.  Localize a pasta **Refatoração** cujo caminho de diretório é:  
  
     *Diretório de instalação*\Microsoft Visual Studio 14.0\VC#\Snippets\\*ID de idioma*\Refactoring  
  
     O caminho real é semelhante ao seguinte para uma instalação padrão:  
  
     C:\Program Files\Microsoft Visual Studio 14.0\VC#\Snippets\1033\Refactoring.  
  
6.  Clique em **Abrir** na caixa de diálogo **Diretório de Trechos de Código** e clique em **OK** no Gerenciador de Trechos de Código.  
  
## <a name="see-also"></a>Consulte também  
 [Trechos de código do Visual C#](../ide/visual-csharp-code-snippets.md)   
 [Refatoração (C#)](../csharp-ide/refactoring-csharp.md)   
 [Trechos de código](../ide/code-snippets.md)
