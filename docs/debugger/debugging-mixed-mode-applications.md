---
title: "Depurando aplicativos de modo misto | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurando [Visual Studio], modo misto"
  - "modo misto de depuração, avaliação de propriedade"
  - "janela de Pilha de Chamadas"
  - "depuração de modo misto"
  - "Janela de pilha de chamadas de modo misto de depuração"
  - "depuração código gerenciado, código misto"
  - "modo misto de depuração, pilha de chamadas"
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurando aplicativos de modo misto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Um aplicativo de modo misto é qualquer aplicativo que combine código nativo \(C\+\+\) com código gerenciado \(como Visual Basic, Visual c\# ou C\+\+ que é executado no common language runtime\). Depuração de aplicativos de modo misto é amplamente transparente no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]; não é muito diferente da depuração de um aplicativo de modo único. No entanto, há algumas considerações especiais.  
  
## Ativar a edição de C\+\+ e continuar a depuração de modo misto  
  
-   Para usar o editar e continuar do C\+\+ no Visual Studio 2013, você precisa reverter para o mecanismo de depuração herdado. Consulte [Alternar para o modo de compatibilidade gerenciado no Visual Studio 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx) no blog do Microsoft Application Lifecycle Management.  
  
## Avaliação da propriedade em aplicativos de modo misto  
 Em um aplicativo de modo misto, a avaliação das propriedades pelo depurador é uma operação cara. Como resultado, a depuração operações como depurar parecer lenta. Para obter mais informações, consulte [revisão](http://msdn.microsoft.com/pt-br/8791dac9-64d1-4bb9-b59e-8d59af1833f9). Se você tiver um desempenho ruim em depuração de modo misto, convém desativar a avaliação da propriedade nas janelas do depurador.  
  
> [!NOTE]
>  Caixas de diálogo e comandos de menu que você vê podem diferir daqueles descritos na Ajuda, dependendo de suas configurações ativas ou edição. Para alterar suas configurações, escolha **Import and Export Settings** sobre o **ferramentas** menu. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
#### Para desativar a avaliação da propriedade  
  
1.  No menu **Ferramentas**, selecione **Opções**.  
  
2.  No **opções** caixa de diálogo, abra o **depuração** pasta e selecione o **geral** categoria.  
  
3.  Limpar o **Habilitar avaliação de propriedades e outras chamadas de função implícitas** caixa de seleção.  
  
 Como pilha de chamadas nativas e pilhas de chamadas gerenciadas diferem, o depurador não pode sempre fornecer pilha de chamadas completa para código misto. Quando código nativo chama código gerenciado, você poderá observar algumas discrepâncias. Para obter mais informações, consulte [código misto e informações ausentes na janela de pilha de chamada](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).  
  
## Consulte também  
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)