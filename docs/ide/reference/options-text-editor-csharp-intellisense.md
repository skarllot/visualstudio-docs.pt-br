---
title: "Opções, Editor de Texto, C#, IntelliSense | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Intellisense
helpviewer_keywords:
- IntelliSense [J#], options
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
caps.latest.revision: 25
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
ms.openlocfilehash: 029f33f42611ed1c6671c6d3080dbff5b02e3870
ms.lasthandoff: 02/22/2017

---
# <a name="options-text-editor-c-intellisense"></a>Opções, Editor de Texto, C#, IntelliSense
Use a página de propriedades **IntelliSense** para modificar as configurações que afetam o comportamento do IntelliSense no Visual C#. É possível acessar a página de propriedades **IntelliSense** clicando em **Opções** no menu **Ferramentas**, clicando em **C#** na pasta **Editor de Texto** e, em seguida, em **IntelliSense.**  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 A página de propriedades **IntelliSense** contém as seguintes propriedades:  
  
## <a name="completion-lists"></a>Listas de Conclusão  
 **Mostrar lista de preenchimento depois que um caractere é digitado**  
 Quando essa opção estiver selecionada, o IntelliSense exibirá automaticamente a lista de preenchimento quando você começar a digitar. Quando essa opção não estiver selecionada, o IntelliSense ainda estará disponível no menu **IntelliSense** ou pressionando CTRL+ESPAÇO.  
  
 **Colocar palavras-chave em listas de preenchimento**  
 Quando essa opção estiver selecionada, o IntelliSense adicionará palavras-chave do C#, por exemplo, [classe](/dotnet/csharp/language-reference/keywords/class), à lista de preenchimento.  
  
 **Colocar trechos de código em listas de preenchimento**  
 Quando essa opção estiver selecionada, o IntelliSense adicionará aliases de trechos de código C# à lista de preenchimento. Caso o alias do trecho de código seja igual a uma palavra-chave, por exemplo, [classe](/dotnet/csharp/language-reference/keywords/class), a palavra-chave será substituída pelo atalho. Para obter mais informações, consulte [Trechos de código do Visual C#](../../ide/visual-csharp-code-snippets.md).  
  
## <a name="selection-in-completion-lists"></a>Seleção em listas de preenchimento  
 **Confirmado pela digitação dos seguintes caracteres:**  
 Especifica todos os caracteres que executam o preenchimento automático do IntelliSense para o item selecionado na lista de preenchimento, depois de ele ser digitado.  
  
 **Confirmado pressionando a barra de espaço**  
 Especifica para incluir a ação de pressionar a barra de espaço para executar o preenchimento automático do IntelliSense para o item selecionado na lista de preenchimento.  
  
 **Adicionar uma nova linha ao pressionar Enter após o fim da palavra totalmente digitada**  
 Especifica que, se você digitar todos os caracteres de uma entrada na lista de preenchimento e, em seguida, pressionar ENTER, uma nova linha será criada automaticamente e o cursor será movido para a nova linha.  
  
 Por exemplo, se você digitar `else` e pressionar ENTER, isto será exibido no editor:  
  
 `else`  
  
 `|` (local do cursor)  
  
 No entanto, se você digitar apenas `el` e pressionar ENTER, isto será exibido no editor:  
  
 `else|` (local do cursor)  
  
## <a name="intellisense-member-selection"></a>Seleção de Membro IntelliSense  
 **Pré-seleciona o membro usado mais recentemente**  
 Quando essa opção estiver selecionada, o IntelliSense pré-selecionará os membros selecionados recentemente na caixa pop-up Listar Membros do preenchimento automático de nome de objeto durante a sessão atual no IDE (ambiente de desenvolvimento integrado). O histórico dos membros mais usados recentemente é limpo entre cada sessão no IDE. Para obter mais informações, consulte [IntelliSense para membros usados mais recentemente](../../misc/intellisense-for-most-recently-used-members.md).  
  
## <a name="see-also"></a>Consulte também  
 [Caixa de diálogo Geral, Ambiente, Opções](../../ide/reference/general-environment-options-dialog-box.md)   
 [Comentários da documentação XML](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)   
 [Usando o IntelliSense](../../ide/using-intellisense.md)
