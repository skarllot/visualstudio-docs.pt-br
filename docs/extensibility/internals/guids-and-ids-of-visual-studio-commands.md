---
title: GUIDs e IDs de comandos do Visual Studio | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 67624e4710470c14f867f9b63ee96a96a55cd991
ms.lasthandoff: 02/22/2017

---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUIDs e IDs de comandos do Visual Studio
Os valores GUID e ID os comandos incluídos no ambiente de desenvolvimento integrado (IDE) do Visual Studio são definidos em arquivos. VSCT que são instalados como parte do SDK do Visual Studio. Para obter mais informações, consulte [IDE-Defined comandos, Menus e grupos](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Para obter mais informações sobre como trabalhar com objetos IDE que são definidos em arquivos. VSCT, consulte [estendendo Menus e comandos](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="finding-a-command-definition"></a>Localizando uma definição de comando  
 Como o Visual Studio define mais de mil comandos, não é prático para listá-las todas aqui. Em vez disso, siga estas etapas para localizar a definição de um comando.  
  
#### <a name="to-locate-a-command-definition"></a>Para localizar uma definição de comando  
  
1.  No Visual Studio, abra os arquivos a seguir no *caminho de instalação do SDK do Visual Studio*pasta \VisualStudioIntegration\Common\Inc\: SharedCmdDef.vsct, ShellCmdDef.vsct, VsDbgCmdUsed.vsct, Venusmenu.vsct.  
  
     A maioria dos comandos do Visual Studio são definidos em SharedCmdDef.vsct e ShellCmdDef.vsct. VsDbgCmdUsed.vsct define comandos que pertencem ao depurador e Venusmenu.vsct define comandos que são específicos para desenvolvimento na Web.  
  
2.  Se o comando é um item de menu, observe o texto exato do item de menu. Se o comando é um botão na barra de ferramentas, observe o texto de dica de ferramenta que aparece quando você pausa nele.  
  
3.  Pressione CTRL + F para abrir o **localizar** caixa de diálogo.  
  
4.  No **localizar** , digite o texto que você anotou na etapa 2.  
  
5.  Verifique **todos os documentos abertos** é exibido no **examinar** caixa.  
  
6.  Clique o **Localizar próximo** botão até que o texto é selecionado no `<Strings>` seção de um [elemento Button](../../extensibility/button-element.md).  
  
     O `<Button>` que o comando é exibido no elemento é a definição de comando.  
  
 Ao localizar a definição de comando, você pode colocar uma cópia do comando em outro menu ou barra de ferramentas, criando uma [CommandPlacement elemento](../../extensibility/commandplacement-element.md) que tem o mesmo `guid` e `id` valores como o comando. Para obter mais informações, consulte [criando reutilizável grupos de botões](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
### <a name="special-cases"></a>Casos especiais  
 Nestes casos, o texto de menu ou o texto de dica de ferramenta pode não corresponder exatamente o que está na definição de comando.  
  
-   Itens de menu que incluem um caractere de sublinhado, como o **impressão** comando o **arquivo** menu, em que o P é sublinhado.  
  
     Caracteres que são precedidos pelo caractere '< /' em nomes de item de menu são exibidos como sublinhado. No entanto, os arquivos. VSCT são gravados em XML, que usa o caractere '< /' para indicar caracteres especiais e requer um e comercial que deve ser exibidas deve ser esclarecido como&amp;'. Portanto, em um arquivo. VSCT, o **P**comando Imprimir aparece como '&amp;impressão '.  
  
-   Comandos que têm texto dinâmico, como **salvar** *Filename atual*e gerado dinamicamente os itens de menu, como os itens no **arquivos recentes** lista.  
  
     Não há nenhuma maneira confiável para pesquisar texto dinâmico. Em vez disso, localizar um grupo que hospeda o comando desejado consultando [GUIDs e IDs do Visual Studio Menus](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) ou [GUIDs e IDs do Visual Studio barras de ferramentas](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)e procure a ID do grupo. Se a definição do comando não tem o grupo como seu [elemento pai](../../extensibility/parent-element.md), SharedCmdPlace.vsct e ShellCmdPlace.vsct (ou VsDbgCmdPlace.vsct para comandos de depurador) de pesquisa para um `<CommandPlacement>` elemento que define o pai do comando. AndVsDbgCmdPlace.vsct SharedCmdPlace.vsct, ShellCmdPlace.vsct, estão no *caminho de instalação do SDK do Visual Studio*\VisualStudioIntegration\Common\Inc\ pasta.  
  
## <a name="see-also"></a>Consulte também  
 [MenuCommands Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referência de esquema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
