---
title: Comandos, Menus e barras de ferramentas | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: 60
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
ms.openlocfilehash: a4598103b0534c7bcac1bab2ac9cd5d232de078f
ms.lasthandoff: 02/22/2017

---
# <a name="commands-menus-and-toolbars"></a>Barras de ferramentas, Menus e comandos
Menus e barras de ferramentas são que os maneira como os usuários acessam comandos em seu VSPackage. Comandos são funções que realizar tarefas, como imprimir um documento, atualizar uma exibição ou criar um novo arquivo. Menus e barras de ferramentas são maneiras gráficas convenientes para apresentar seus comandos aos usuários. Normalmente, os comandos relacionados são agrupados juntos no mesmo menu ou barra de ferramentas.  
  
-   Normalmente, menus são exibidos como cadeias de caracteres de uma palavra em cluster em uma linha na parte superior do ambiente de desenvolvimento integrado (IDE) ou uma janela de ferramenta. Menus também podem ser exibidos como o resultado de um evento de mouse e são chamados de menus de atalho nesse contexto. Quando clicado, menus expanda para exibir um ou mais comandos. Comandos, quando clicado, podem realizar tarefas ou inicie submenus que contêm comandos adicionais. Alguns nomes de menu conhecidas são arquivo, editar, exibir e janela. Para obter mais informações, consulte [estendendo Menus e comandos](../../extensibility/extending-menus-and-commands.md).  
  
-   Barras de ferramentas normalmente são linhas de botões e outros controles, como caixas de combinação, caixas de listagem, caixas de texto e controladores de menu. Todos os controles de barra de ferramentas são associados a comandos. Quando você clica em um botão da barra de ferramentas, o comando associado está ativado. Botões da barra de ferramentas geralmente têm ícones que sugerem os comandos subjacentes, como uma impressora para um comando de impressão. Em um controle de lista suspensa, cada item na lista está associado um comando diferente. Um controlador de menu é um híbrido no qual um lado do controle é um botão de barra de ferramentas e o outro lado é uma seta para baixo que exibe comandos adicionais quando clicado. Para obter mais informações, consulte [adicionar um controlador de Menu a uma barra de ferramentas](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).  
  
-   Quando você cria um comando, você também deve criar um manipulador de eventos para ele. O manipulador de eventos determina quando o comando é visível ou habilitada, permite que você modifique seu texto e garante que o comando responde adequadamente ("rotas") quando ativado. Na maioria dos casos, o IDE manipula comandos usando o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Comandos no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rota de maneira hierárquica, começando com o contexto do comando interno, com base na seleção de local e prosseguir com o contexto mais externo, com base na seleção global. Os comandos adicionados ao menu principal são imediatamente disponibilizados para scripts. Para obter mais informações, consulte [MenuCommands Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md) e [objetos de contexto de seleção](../../extensibility/internals/selection-context-objects.md).  
  
 Para definir novos menus e barras de ferramentas, você deve descrevê-los em um arquivo de tabela de comando do Visual Studio (VSCT). O modelo de pacote do Visual Studio cria esse arquivo para você, juntamente com os elementos necessários para dar suporte a quaisquer comandos, barras de ferramentas e editores selecionadas no modelo. Como alternativa, você pode escrever seu próprio arquivo. VSCT, usando o esquema xml descrito aqui: [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).  
  
 Para obter mais informações sobre como trabalhar com arquivos. VSCT, consulte [tabela de comando do Visual Studio (. Arquivos VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Os tópicos nesta seção explicam como barras de ferramentas, menus e comandos funcionam no VSPackages.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como os VSPackages adicionar elementos de Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Uma descrição detalhada da especificação de formato de tabela do comando.  
  
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 Descreve uma sintaxe baseada em XML e o compilador para tabelas de comando.  
  
 [Comando padrão, o grupo e o posicionamento da barra de ferramentas](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 Descreve grupos, barras de ferramentas, menus e comandos predefinidos.  
  
 [Grupos, Menus e comandos definidos pelo IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 Especifica o predefinidos de menus, comandos e grupos de comando disponíveis para uso pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Design de comando](../../extensibility/internals/command-design.md)  
 Explica como criar comandos.  
  
 [Otimizando o Menu e comandos da barra de ferramentas](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 Fornece diretrizes para comandos.  
  
 [Disponibilizar comandos](../../extensibility/internals/making-commands-available.md)  
 Explica como tornar os comandos disponíveis para o Visual Studio.  
  
 [Comandos e Menus que usam Assemblies de interoperabilidade](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Explica como implementar comandos que usam assemblies de interoperabilidade.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Roteamento de comando em VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Explica o roteamento de comando em VSPackages.
