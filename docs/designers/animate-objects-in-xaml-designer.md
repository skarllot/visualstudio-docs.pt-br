---
title: Animar objetos no Designer XAML | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9be2375898fc9e7293fd2db5308a69e427f95cf4
ms.lasthandoff: 02/22/2017

---
# <a name="animate-objects-in-xaml-designer"></a>Animar objetos no XAML Designer
É possível criar animações curtas que movem objetos ou fazer com que eles esmaeçam.  
  
 Para começar, crie um *storyboard*. Um storyboard contém uma ou mais *linhas do tempo*. Defina os *quadros chave* em uma linha do tempo para marcar as alterações de propriedade. Depois, ao executar a animação, o Blend interpolará as alterações de propriedade durante o período de tempo designado. O resultado é uma transição suave. É possível animar qualquer propriedade que pertença a um objeto, mesmo propriedades não visuais.  
  
 A ilustração a seguir mostra um storyboard denominado **MoveUp**. A linha do tempo contém quadros chave que marcam as posições X e Y de um retângulo. Quando essa animação é executada, o retângulo move de uma posição para outra sem problemas.  
  
 ![](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png "982f031a-74a3-414a-abc2-a0f41a741075")  
  
 Saiba como criar animações assistindo a esses vídeos.  
  
|Assista a um breve vídeo:|Saiba como:|  
|--------------------------|-------------------|  
|![Configurar Recursos Instalados](~/docs/designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon")[Criar linhas do tempo](http://www.popscreen.com/v/6A4eF/Microsoft-Expression-Blend-Creating-Timelines)|Crie uma linha do tempo e trabalhe com objetos nela.|  
|![Configurar Recursos Instalados](~/docs/designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Adicionar quadros chave e repetir a animação](http://www.popscreen.com/v/6A4fi/Microsoft-Expression-Blend-Adding-Keyframes-and-Repeating-an-Animation)|Adicione quadros chave e defina propriedades em cada um deles. Em seguida, execute a animação e assista à transição suave entre os objetos.|  
|![Configurar Recursos Instalados](~/docs/designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Adicionar gatilhos de evento para obter interatividade](http://www.popscreen.com/v/6A4e4/Microsoft-Expression-Blend-Adding-Event-Triggers-for-Interactivity)|Inicie uma animação quando ocorrer um evento. Por exemplo, inicie uma animação quando a janela for carregada.|  
|![Configurar Recursos Instalados](~/docs/designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon")[Animar cores](http://www.popscreen.com/v/6A4gv/Microsoft-Expression-Blend-Animating-Colors)|Use uma animação para alterar a cor de um objeto.|  
|![Configurar Recursos Instalados](~/docs/designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon")[Criar e modificar trajetórias de animação](http://www.popscreen.com/v/6A4fX/Microsoft-Expression-Blend-Creating-and-Modifying-Motion-Paths)|Anime objetos ao longo de um caminho.|  
|![Configurar Recursos Instalados](~/docs/designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon")[Suavizar quadros chave](http://www.popscreen.com/v/6A4dM/Microsoft-Expression-Blend-Easing-Keyframes)|Aumente ou diminua a velocidade de uma animação no início (*suavização de entrada*) ou no final (*suavização de saída*) de uma animação.|  
|![Configurar Recursos Instalados](~/docs/designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon")[Animar o botão](http://www.popscreen.com/v/6A4fK/Microsoft-Expression-Blend-Animating-a-Button)|Crie efeitos interessantes que aparecem em um botão quando o usuário aponta para ele.|  
|![Configurar Recursos Instalados](~/docs/designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon")[Criar animação e trabalhar com a suavização](https://www.youtube.com/watch?v=mAJXYrwxGYo)|Anime efeitos que aparecem quando um usuário pressiona um botão na imagem de uma calculadora.|  
  
## <a name="see-also"></a>Consulte também  
 [Criando uma interface do usuário usando o Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
