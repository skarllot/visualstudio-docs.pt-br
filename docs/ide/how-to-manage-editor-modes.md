---
title: Como gerenciar modos do editor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- word wrap
- views, virtual space
- line numbers, displaying
- virtual space mode
- line numbers
- Code Editor, view and display options
- full screen mode
- Code Editor, modes
- views, splitting
- views, word wrapping
- fonts and size
- views, creating new windows
- views, line numbers
- views, changing mode
- views, outlining
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 71566f11a069d266ded2aebe02bbf388cf00730e
ms.contentlocale: pt-br
ms.lasthandoff: 05/24/2017

---
# <a name="how-to-manage-editor-modes"></a>Como gerenciar modos do editor
É possível exibir o Editor de Código do Visual Studio em vários modos de exibição.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="enabling-full-screen-mode"></a>Habilitando o modo de tela inteira  
 É possível escolher ocultar todas as janelas de ferramentas e exibir apenas janelas do documento, habilitando o modo de **Tela Inteira**.  
  
#### <a name="to-enable-full-screen-mode"></a>Para habilitar o modo de Tela Inteira  
  
-   Pressione ALT+SHIFT+ENTER para entrar ou sair do modo de **Tela Inteira**.  
  
     --ou--  
  
-   Emita o comando `View.Fullscreen` na janela **Comando**.  
  
## <a name="enabling-virtual-space-mode"></a>Habilitando o modo Espaço virtual  
 No modo **Espaço virtual**, os espaços são inseridos no final de cada linha de código. Selecione essa opção para posicionar comentários em um ponto consistente ao lado do seu código.  
  
#### <a name="to-enable-virtual-space-mode"></a>Para habilitar o modo Espaço virtual  
  
1.  Selecione **Opções** no menu **Ferramentas**.  
  
2.  Expanda a pasta **Editor de Texto** e escolha **Todas as Linguagens** para definir essa opção globalmente ou escolha uma pasta de idioma específico. (Por exemplo, para ativar os números de linha apenas no Visual Basic, escolha as opções Basic, Editor de Texto.)  
  
3.  Selecione as opções **Gerais** e, em **Configurações**, selecione **Habilitar Espaço virtual**.  
  
    > [!NOTE]
    >  O **Espaço virtual** está habilitado no modo **Seleção de Coluna**. Quando o modo **Espaço virtual** não está habilitado, o ponto de inserção é movido do final de uma linha diretamente para o primeiro caractere da próxima.  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando o editor](../ide/customizing-the-editor.md)   
 [Personalizar layouts de janela no Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)   
 [Caixa de diálogo Fontes e Cores, Ambiente, Opções](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)
