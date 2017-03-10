---
title: "Animar objetos no XAML Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Animar objetos no XAML Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode criar animações curtas que mover objetos ou \-los e desapareçam.  
  
 Para começar, crie um *storyboard*. Um storyboard contém um ou mais *cronogramas*. Definir *quadros chave* em um cronograma para marcar as alterações de propriedade. Em seguida, quando você executar a animação, o Blend interpola as alterações de propriedade durante o período de tempo designado. O resultado é uma transição suave. Você pode animar qualquer propriedade que pertence a um objeto, mesmo propriedades não visuais.  
  
 A ilustração a seguir mostra um storyboard denominado **Mover para cima**. A linha do tempo contém quadros\-chave que marca a posição X e Y de um retângulo. Quando essa animação é executada, o retângulo move de uma posição para outra sem problemas.  
  
 ![](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png "982f031a\-74a3\-414a\-abc2\-a0f41a741075")  
  
 Saiba como criar animações assistindo estes vídeos.  
  
|Assista a um vídeo curto:|Saiba como:|  
|-------------------------------|-----------------|  
|![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Criar linhas do tempo](http://www.popscreen.com/v/6A4eF/Microsoft-Expression-Blend-Creating-Timelines)|Crie uma linha do tempo e trabalhar com objetos na linha do tempo.|  
|![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Adicionar quadros\-chave e repetir a animação](http://www.popscreen.com/v/6A4fi/Microsoft-Expression-Blend-Adding-Keyframes-and-Repeating-an-Animation)|Adicionar quadros\-chave e definir propriedades em cada quadro\-chave. Em seguida, execute os objetos de animação e assista suavemente transição entre eles.|  
|![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Adicionar gatilhos de evento para interatividade](http://www.popscreen.com/v/6A4e4/Microsoft-Expression-Blend-Adding-Event-Triggers-for-Interactivity)|Inicie uma animação quando ocorre um evento. Por exemplo, inicie um quando a janela é carregada.|  
|![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Animar cores](http://www.popscreen.com/v/6A4gv/Microsoft-Expression-Blend-Animating-Colors)|Use uma animação para alterar a cor de um objeto.|  
|![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Criar e modificar as trajetórias de animação](http://www.popscreen.com/v/6A4fX/Microsoft-Expression-Blend-Creating-and-Modifying-Motion-Paths)|Anime objetos ao longo de um caminho.|  
|![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Facilidade quadros\-chave](http://www.popscreen.com/v/6A4dM/Microsoft-Expression-Blend-Easing-Keyframes)|Aumentar ou diminuir uma animação próximo ao início \(*atenuação em*\) ou próximo do final \(*fora de atenuação*\) de uma animação.|  
|![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Animar o botão](http://www.popscreen.com/v/6A4fK/Microsoft-Expression-Blend-Animating-a-Button)|Crie efeitos interessantes que aparecem em um botão quando o usuário aponta para ele.|  
|![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Animação de criar e trabalhar com a atenuação](https://www.youtube.com/watch?v=mAJXYrwxGYo)|Anime efeitos que aparecem quando um usuário pressiona um botão a imagem de uma calculadora.|  
  
## Consulte também  
 [Criando uma interface de usuário usando o Blend para Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)