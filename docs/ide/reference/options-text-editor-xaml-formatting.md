---
title: "Opções, Editor de Texto, XAML, Formatação | Microsoft Docs"
ms.custom: 
ms.date: 01/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.XAML.Miscellaneous
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.Spacing
helpviewer_keywords:
- element spacing, XAML view settings
- attribute spacing, XAML view settings
- XAML view settings, auto-formatting events
- auto-formatting events, XAML view settings
- XAML view settings, tag wrapping
- XAML view settings, auto insert
- quotation mark style, XAML view settings
- XAML formatting, WPF Designer
- XAML view settings, Toolbox
- XAML view settings, element spacing
- default view, XAML view settings
- auto insert, XAML view settings
- XAML view settings, default view
- XAML view settings, quotation mark style
- tag wrapping, XAML view settings
- WPF Designer, XAML formatting
- XAML view settings, attribute spacing
ms.assetid: ad3820b1-0d94-4807-a74c-c3467ed973a2
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 0d087d735f3db1f1d8fa7f37f049b6208e5242c0
ms.contentlocale: pt-br
ms.lasthandoff: 05/30/2017

---
# Opções, Editor de Texto, XAML, Formatação
<a id="options-text-editor-xaml-formatting" class="xliff"></a>
Use a página de propriedades **Formatação** para especificar como elementos e atributos são formatados nos documentos XAML. Para abrir a caixa de diálogo **Opções**, clique no menu **Ferramentas** e clique em **Opções**. Para acessar a página de propriedades de **Formatação**, expanda o nó **Editor de Texto**, **XAML**, **Formatação**.  

> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  

## Eventos de Formatação Automática
<a id="auto-formatting-events" class="xliff"></a>  
 Formatação automática pode ocorrer quando qualquer um dos eventos a seguir é detectado.  

-   Preenchimento de uma marcação de fim ou de uma marcação simples.  

-   Preenchimento de uma marcação de início.  

-   Colando da área de transferência.  

-   Comandos de teclado de formatação.  

 Você pode especificar os eventos que causam formatação automática.  

|||  
|-|-|  
|**Ao preencher a marcação de fim ou der marca simples**|Formatação automática ocorre quando você termina de digitar uma marcação de fim ou uma marcação simples. Uma marcação simples não tem atributos, por exemplo `<Button />`.|  
|**Ao preencher uma marcação de início**|Formatação automática ocorre quando você termina de digitar uma marcação de início.|  
|**Ao colar da área de transferência**|Formatação automática ocorre quando você cola XAML da área de transferência para a exibição XAML.|  

## Estilo de Aspas
<a id="quotation-mark-style" class="xliff"></a>  
 Essa configuração indica se os valores de atributo são colocados entre aspas simples ou duplas. O formatador automático e o preenchimento automático IntelliSense usam essa configuração.  

 Ao definir essa opção, apenas atributos subsequentemente adicionados usando o designer ou manualmente na exibição XAML são afetados.  

|||  
|-|-|  
|**Aspas duplas (")**|Valores de atributos são colocados entre aspas duplas.<br /><br /> `<Button Name="button1">Hello</Button>`|  
|**Aspas simples (')**|Valores de atributos são colocados entre aspas simples.<br /><br /> `<Button Name='button1'>Hello</Button>`|  

## Automática de marca
<a id="tag-wrapping" class="xliff"></a>  
 Você pode especificar um comprimento de linha para disposição de marcação. Quando a disposição de marcação está habilitada, qualquer XAML adicionado posteriormente usando o designer será disposto adequadamente.  

|||  
|-|-|  
|**Encapsular marcações que excedam o comprimento especificado**|Especifica se as linhas são dispostas no comprimento de linha especificado por **Comprimento**.|  
|**Comprimento**|O número de caracteres que uma linha pode conter. Se necessário, algumas linhas XAML poderão exceder o comprimento de linha especificado.|  

## Espaçamento de Atributos
<a id="attribute-spacing" class="xliff"></a>  
 Use essa configuração para controlar como os atributos são organizados no documento XAML  

|||  
|-|-|  
|**Preservar novas linhas e espaços entre atributos**|Novas linhas e espaços entre atributos não são afetados por formatação automática.<br /><br /> `<Button Height="23"   Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  
|**Inserir um espaço único entre os atributos**|Atributos ocupam uma linha, com um espaço separando atributos adjacentes. Configurações de disposição de marcação são aplicadas.<br /><br /> `<Button Height="23" Name="button1" Width="75">Hello</Button>`|  
|**Posicionar cada atributo em uma linha separada**|Cada atributo ocupa sua própria linha. Isso é útil quando existem muitos atributos.<br /><br /> `<Button`<br /><br /> `Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  
|**Posicionar primeiro atributo na mesma linha que a marcação de início**|Quando essa opção está marcada, o primeiro atributo aparece na mesma linha que a marcação de início do elemento.<br /><br /> `<Button Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  

## Espaçamento de Elementos
<a id="element-spacing" class="xliff"></a>  
 Use essa configuração para controlar como os elementos são organizados no documento XAML  

|||  
|-|-|  
|**Preservar novas linhas no conteúdo**|Linhas vazias no conteúdo do elemento não são removidas.<br /><br /> `<Grid>`<br /><br /> ``<br /><br /> ``<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> ``<br /><br /> `</Grid>`|  
|**Recolher várias linhas vazias no conteúdo para uma linha única**|Linhas vazias no conteúdo do elemento são recolhidas em uma única linha.<br /><br /> `<Grid>`<br /><br /> ``<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> ``<br /><br /> `</Grid>`|  
|**Remover linhas vazias no conteúdo**|Todas as linhas vazias no conteúdo do elemento são removidas.<br /><br /> `<Grid>`<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> `</Grid>`|  

## Seção Diversos, Inserção Automática
<a id="miscellaneous-section-auto-insert" class="xliff"></a>  
 Use essa configuração para controlar quando marcas e aspas são geradas automaticamente.  

|||  
|-|-|  
|**Marcas de fechamento**|Especifica se a marcação de fechamento de um elemento é gerada automaticamente ao você fechar a marcação de abertura com o caractere de maior que (>).|  
|**Aspas de atributo**|Especifica se as aspas de fechamento são geradas quando um valor de atributo é selecionado na lista suspensa de preenchimento de declaração.|  
|**Chaves de fechamento para MarkupExtensions**|Especifica se uma chave de fechamento (}) de uma extensão de marcação é gerada automaticamente ao digitar o caractere de chave de abertura ({).|  
|**Vírgulas para separar parâmetros MarkupExtension**|Especifica se vírgulas são geradas quando você digita mais de um parâmetro em uma extensão de marcação.|  

## Consulte também
<a id="see-also" class="xliff"></a>  
 [XAML no WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)   
 [Como alterar as configurações do modo de exibição XAML](http://msdn.microsoft.com/en-us/aee87c79-ca01-4f84-8fb7-a9e47048ee47)   
 [Passo a passo do Code e XAML](http://msdn.microsoft.com/en-us/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)

