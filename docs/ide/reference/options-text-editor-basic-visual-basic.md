---
title: "Opções, Editor de Texto, Básico (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
caps.latest.revision: 15
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
ms.openlocfilehash: 6264c76532796a480753b18120d547c2cd807c0c
ms.lasthandoff: 02/22/2017

---
# <a name="options-text-editor-basic-visual-basic"></a>Opções, Editor de Texto, Básico (Visual Basic)
A página de propriedades **Específico do VB**, na pasta **Básico** da pasta **Editor de Texto** da caixa de diálogo **Opções** (menu **Ferramentas**) contém as seguintes propriedades:  
  
 **Inserção automática de constructos finais**  
 Quando você digita, por exemplo, a primeira linha de uma declaração de procedimento, `Sub Main—`e pressiona ENTER, o editor de texto adiciona uma linha `End Sub` correspondente. Da mesma forma, se você adicionar um loop [For](/dotnet/visual-basic/language-reference/statements/for-next-statement), o editor de texto adicionará uma instrução `Next` correspondente. Quando essa opção é selecionada, o editor de código adiciona automaticamente o constructo final.  
  
 **Reformatação automática de código**  
 O editor de texto reformata seu código conforme apropriado. Quando essa opção é selecionada, o editor de códigos:  
  
-   Alinhará seu código com a posição correta de guia  
  
-   Redefinirá as maiúsculas e minúsculas de palavras-chave, variáveis e objetos para o formato correto  
  
-   Adicionará um `Then` ausente a uma instrução `If...Then`  
  
-   Adicionará parênteses a chamadas de função  
  
-   Adicionará aspas finais faltando a cadeias de caracteres  
  
-   Reformatará notação exponencial  
  
-   Reformatará datas  
  
 **Habilitar modo de estrutura de tópicos**  
 Ao abrir um arquivo no editor de código, você pode exibir o documento no modo de estrutura de tópicos. Consulte [Estrutura de Tópicos](../../ide/outlining.md) para obter mais informações. Quando essa opção é selecionada, o recurso de estrutura de tópicos é ativado quando você abre um arquivo.  
  
 **Inserção automática de membros Interface e MustOverride**  
 Quando você confirma uma instrução `Implements` ou uma instrução `Inherits` para uma classe, o editor de texto insere protótipos para os membros que devem ser implementados ou substituídos, respectivamente.  
  
 **Mostrar separadores de linha do procedimento**  
 O editor de texto indica o escopo visual dos procedimentos. Uma linha é desenhada nos arquivos de origem .vb do seu projeto nos locais listados na tabela a seguir:  
  
|Local no arquivo de origem .vb|Exemplo de local da linha|  
|---------------------------------|------------------------------|  
|Após o encerramento de um constructo de declaração de bloco|–   No final de uma classe, estrutura, módulo, interface ou enumeração<br />–   Depois de uma propriedade, função ou sub<br />–   Não entre cláusulas get e set em uma propriedade|  
|Depois de um conjunto de constructos de linha única|–   Depois das instruções de importação, antes de uma definição de tipo em um arquivo de classe<br />–   Depois de variáveis declaradas em uma classe, antes de qualquer procedimento|  
|Depois de declarações de linha única (declarações de nível não de bloco)|–   Após instruções de importação, instruções de herdar, declarações de variável, declarações de evento, declarações de delegado e instruções de declaração DLL|  
  
 **Habilitar sugestões para correção de erros**  
 O editor de texto pode sugerir soluções para erros comuns e permitir selecionar a correção apropriada, que então é aplicada ao seu código.  
  
 **Habilitar realce de referências e palavras-chave**  
 O editor de texto pode realçar todas as instâncias de um símbolo ou todas as palavras-chave em uma cláusula como `If..Then`, `While...End While` ou `Try...Catch...Finally`. Você pode navegar entre referências realçadas ou palavras-chave pressionando CTRL+SHIFT+SETA PARA BAIXO ou CTRL+SHIFT+SETA PARA CIMA.  
  
## <a name="see-also"></a>Consulte também  
 [Caixa de diálogo Geral, Ambiente, Opções](../../ide/reference/general-environment-options-dialog-box.md)   
 [Opções, Editor de Texto, Todas as Linguagens, Guias](../../ide/reference/options-text-editor-all-languages-tabs.md)
