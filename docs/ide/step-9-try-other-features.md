---
title: 'Etapa 9: Experimentar outros recursos | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
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
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: 9d5e8a86d71cf1f6aa47853b862a4668dea05633
ms.lasthandoff: 02/22/2017

---
# <a name="step-9-try-other-features"></a>Etapa 9: Experimentar outras funcionalidades
Para aprender mais, tente alterar os ícones e as cores, adicionar um temporizador de jogo e adicionar sons. Para tornar o jogo mais desafiador, tente aumentar o tabuleiro e ajustar o temporizador.  
  
 Para baixar uma versão completa do exemplo, consulte [Complete Matching Game tutorial sample (Exemplo de tutorial completo de jogo da memória)](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).  
  
### <a name="to-try-other-features"></a>Para testar outros recursos  
  
-   Substitua os ícones e as cores pelos de sua preferência.  
  
    > [!TIP]
    >  Tente observar a propriedade [Forecolor](http://msdn.microsoft.com/library/system.windows.forms.control.forecolor.aspx) do rótulo.  
  
-   Adicione um temporizador de jogo que controla em quanto tempo o jogador ganha uma partida.  
  
    > [!TIP]
    >  Para isso, você pode adicionar um rótulo para exibir o tempo decorrido no formulário acima de TableLayoutPanel e adicionar outro temporizador ao formulário para controlar o tempo. Use código para iniciar o temporizador quando o jogador começar o jogo e para interromper o temporizador depois que os dois últimos ícones forem encontrados.  
  
-   Adicione um som para quando o jogador encontrar um par, outro som para quando o jogador selecionar dois ícones que são diferentes e um terceiro som para quando o programa ocultar os ícones novamente.  
  
    > [!TIP]
    >  Para reproduzir sons, você pode usar o namespace System.media. Consulte [Reproduzir sons no aplicativo Windows Forms (C# .NET)](http://youtu.be/qOh4ooHg1UU) ou [Como reproduzir áudio no Visual Basic](http://youtu.be/-4oPDeQrtMs) para obter mais informações.  
  
-   Torne o jogo mais difícil aumentando o tamanho do tabuleiro.  
  
    > [!TIP]
    >  Você precisará fazer mais do que apenas adicionar linhas e colunas ao TableLayoutPanel; você também precisará considerar o número de ícones criados.  
  
-   Torne o jogo mais desafiador ocultando o primeiro ícone se o jogador demorar demais para reagir e não escolher o segundo ícone antes do término de um determinado tempo.  
  
### <a name="to-continue-or-review"></a>Para continuar ou revisar  
  
-   Se você estiver com dificuldades ou tiver dúvidas quanto à programação, tente publicar sua dúvida em um dos fóruns do MSDN. Consulte [Fórum do Visual Basic](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral) e [Fórum do Visual C#](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral).  
  
-   Há recursos de aprendizagem por vídeo excelentes e gratuitos disponíveis para você. Para saber mais sobre programação no Visual Basic, consulte [Visual Basic Fundamentals: Development for Absolute Beginners (Conceitos básicos do Visual Basic: desenvolvimento para iniciantes absolutos)](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Para saber mais sobre programação no Visual C#, consulte [C# Fundamentals: Development for Absolute Beginners (Conceitos básicos do C#: desenvolvimento para iniciantes absolutos)](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).  
  
-   Para retornar à etapa anterior do tutorial, consulte [Etapa 8: Adicionar um método para verificar se o jogador ganhou](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
