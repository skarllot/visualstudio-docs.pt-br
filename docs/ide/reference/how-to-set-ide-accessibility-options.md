---
title: "Como definir opções de acessibilidade do IDE| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
caps.latest.revision: 21
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
ms.openlocfilehash: b1a0cd94892c74e583d8e2c4740d5ec800594770
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-set-ide-accessibility-options"></a>Como definir opções de acessibilidade IDE
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] contém recursos que facilitam a leitura para pessoas com deficiência visual e a escrita para pessoas com destreza limitada. Esses recursos incluem alterar o tamanho e a cor do texto em editores, alterar o tamanho do texto e de botões em barras de ferramentas e o preenchimento automático para métodos e parâmetros, entre outros.  
  
 Além disso, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dá suporte a layouts de teclado Dvorak, que tornam os caracteres digitados com maior frequência mais acessíveis. Você também pode personalizar as teclas de atalho padrão disponíveis com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para obter mais informações, consulte [Identificando e personalizando atalhos de teclado](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="editors-dialogs-and-tool-windows"></a>Editores, caixas de diálogo e janelas de ferramentas  
 Por padrão, caixas de diálogo e janelas de ferramentas no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usam o mesmo tamanho da fonte e as mesmas cores do sistema operacional. As configurações de cor do quadro do IDE, das caixas de diálogo, das barras de ferramentas e das janelas de ferramentas são baseadas em um esquema de cores: clara ou escuro. É possível alterar o tema da cor atual em [Geral, Ambiente, caixa de diálogo Opções](../../ide/reference/general-environment-options-dialog-box.md).  
  
 Também é possível exibir janelas pop-up no modo de exibição de Código do editor. Essas janelas podem fornecer membros disponíveis no objeto atual e os parâmetros para concluir uma função ou instrução. Essas janelas podem ser úteis se você tiver dificuldades para digitar. No entanto, elas interferem no foco do editor de código, o que pode ser um problema para alguns usuários. É possível desligar essas janelas abrindo a caixa de diálogo Opções e desmarcando **Listar membros automaticamente** e **Informações do parâmetro** no **Editor de Texto**, **Todos os Idiomas**, página **Geral**, na caixa de diálogo **Opções**. Para obter mais informações, consulte [Como definir opções gerais do Editor](http://msdn.microsoft.com/en-us/704e4a7b-2162-4bed-8a47-f4f6ffec98c2).  
  
 É possível reorganizar as janelas no IDE (ambiente de desenvolvimento integrado) para se adequar melhor à maneira como você trabalha. Você pode encaixar, derivar, ocultar ou ocultar automaticamente cada janela de ferramentas.  
  
 Para obter mais informações sobre como alterar os layouts das janelas, consulte [Personalizando layouts de janela](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
### <a name="changing-the-size-of-text"></a>Alterando o tamanho do texto  
 É possível alterar as configurações de janelas de ferramentas baseadas em texto, como as janelas **Comando**, **Imediato** e de **Saída**, no painel **Fontes e Cores** das opções **Ambiente** na caixa de diálogo **Ferramentas**. Quando **[Todas as janelas de ferramentas de texto]** é selecionado na lista suspensa **Mostrar configurações de**, a configuração padrão é listada como **Padrão** nas listas suspensas **Primeiro plano do item** e **Tela de fundo do item**. Também é possível alterar as configurações de como o texto é exibido no editor.  
  
##### <a name="to-change-the-size-of-text-in-text-based-tool-windows-and-editors"></a>Para alterar o tamanho do texto em editores e janelas de ferramentas baseadas em texto  
  
1.  No menu **Ferramentas**, escolha **Opções**.  
  
2.  Escolha **Fontes e Cores** na pasta **Ambiente**.  
  
3.  Selecione uma opção no menu suspenso **Mostrar configurações de**.  
  
     Para alterar o tamanho da fonte do texto em um editor, escolha **Editor de Texto**.  
  
     Para alterar o tamanho da fonte do texto em janelas de ferramentas baseadas em texto, escolha **[Todas as janelas de ferramentas de texto]**.  
  
     Para alterar o tamanho da fonte do texto das Dicas de Ferramentas de um editor, escolha **Dica de Ferramenta do Editor**.  
  
     Para alterar o tamanho da fonte do texto em pop-ups de preenchimento de declaração, escolha **Preenchimento de declaração**.  
  
4.  Em **Exibir Itens**, selecione **Texto sem formatação**.  
  
5.  Em **Fonte**, selecione um novo tipo de fonte.  
  
6.  Em **Tamanho**, selecione um novo tamanho da fonte.  
  
    > [!NOTE]
    >  Para redefinir o tamanho do texto em editores e janelas de ferramentas baseadas em texto, escolha **Usar Padrões**.  
  
7.  Escolha **OK**.  
  
### <a name="changing-the-colors-used-in-the-ide"></a>Alterando as cores usadas no IDE  
 Você também pode optar por alterar as cores padrão de texto, indicadores de margem, espaços em branco e elementos de código no editor.  
  
> [!NOTE]
>  Para usar cores de alto contraste para todas as janelas de aplicativo no sistema operacional, pressione Esquerda **ALT +** Esquerda **SHIFT + PRINT SCREEN**. Se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] estiver aberto, feche e reabra [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para implementar completamente as cores de alto contraste.  
  
##### <a name="to-change-the-color-of-items-in-the-editor"></a>Para alterar a cor de itens no editor  
  
1.  No menu **Ferramentas**, escolha **Opções**.  
  
2.  Escolha **Fontes e Cores** na pasta **Ambiente**.  
  
3.  Em **Mostrar configurações de**, escolha **Editor de Texto**.  
  
4.  Em **Exibir Itens**, selecione um item cuja exibição você precisa alterar, como **Texto sem formatação**, **Margem de Indicadores**, **Espaço em branco visível**, **Nome do Atributo HTML** ou **Atributo XML**.  
  
5.  Selecione configurações de exibição entre as opções a seguir: **Primeiro plano do item**, **Tela de fundo do item** e **Negrito**.  
  
6.  Escolha **OK**.  
  
## <a name="toolbars"></a>Barras de ferramentas  
 Para melhorar a acessibilidade e a usabilidade da barra de ferramentas, você pode adicionar texto a botões da barra de ferramentas.  
  
#### <a name="to-assign-text-to-toolbar-buttons"></a>Para atribuir texto a botões da barra de ferramentas  
  
1.  No menu **Ferramentas**, escolha **Personalizar**.  
  
2.  Na caixa de diálogo **Personalizar**, selecione a guia **Comandos**.  
  
3.  Selecione **Barra de ferramentas** e escolha o nome da barra de ferramentas que contém o botão para o qual você pretende exibir texto.  
  
4.  Na lista, selecione o comando que deseja alterar.  
  
5.  Escolha **Modificar seleção**.  
  
6.  Escolha **Imagem e Texto**.  
  
#### <a name="to-modify-the-buttons-displayed-text"></a>Para modificar o texto do botão exibido  
  
1.  Selecione **Modificar seleção** novamente.  
  
2.  Ao lado de **Nome**, forneça uma nova legenda para o botão selecionado.  
  
## <a name="see-also"></a>Consulte também  
 [Recursos de Acessibilidade do Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)   
 [Recursos para projetar aplicativos acessíveis](../../ide/reference/resources-for-designing-accessible-applications.md)
