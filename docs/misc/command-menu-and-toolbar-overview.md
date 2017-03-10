---
title: "Vis&#227;o geral da barra de ferramentas, menus e comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "conceitos básicos do menu [SDK do Visual Studio]"
  - "Fundamentos da barra de ferramentas [Visual Studio SDK]"
ms.assetid: cbdaceaa-7dd3-4a56-aea6-b759e48d83d6
caps.latest.revision: 19
caps.handback.revision: 19
manager: "douge"
---
# Vis&#227;o geral da barra de ferramentas, menus e comando
Menus e barras de ferramentas fornecem uma maneira gráfica conveniente para os usuários acessarem o VSPackage comandos. Comandos são funções que realizar tarefas, como imprimir um documento, atualizar uma exibição ou criar um novo arquivo. Menus e barras de ferramentas são maneiras gráficas convenientes para apresentar seus comandos aos usuários. Normalmente, os comandos relacionados são agrupados juntos no mesmo menu ou barra de ferramentas.  
  
-   Normalmente, menus são exibidos como cadeias de caracteres de uma palavra em cluster em uma linha na parte superior do ambiente de desenvolvimento integrado \(IDE\) ou uma janela de ferramenta. Menus também podem ser exibidos como o resultado de um evento de mouse e são chamados de menus de atalho nesse contexto. Quando clicado, menus expanda para exibir um ou mais comandos. Comandos, quando clicado, podem realizar tarefas ou inicie submenus que contêm comandos adicionais. Alguns nomes de menu conhecidas são arquivo, editar, exibir e janela. Para obter mais informações, consulte [Estendendo Menus e comandos](../extensibility/extending-menus-and-commands.md).  
  
-   Barras de ferramentas normalmente são linhas de botões e outros controles, como caixas de combinação, caixas de listagem, caixas de texto e controladores de menu. Todos os controles de barra de ferramentas são associados a comandos. Quando você clica em um botão da barra de ferramentas, o comando associado está ativado. Botões da barra de ferramentas geralmente têm ícones que sugerem os comandos subjacentes, como uma impressora para um comando de impressão. Em um controle de lista suspensa, cada item na lista está associado um comando diferente. Um controlador de menu é um híbrido no qual um lado do controle é um botão de barra de ferramentas e o outro lado é uma seta para baixo que exibe comandos adicionais quando clicado. Para obter mais informações, consulte [Como: criar barras de ferramentas para janelas de ferramenta](../misc/how-to-create-toolbars-for-tool-windows.md) e [Adicionando ícones a comandos de Menu](../extensibility/adding-icons-to-menu-commands.md).  
  
-   Quando você cria um comando, você também deve criar um manipulador de eventos para ele. O manipulador de eventos determina quando o comando é visível ou habilitada, permite que você modifique seu texto e garante que o comando responde adequadamente \("rotas"\) quando ativado. Na maioria dos casos, o IDE manipula comandos usando o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Comandos no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rota de maneira hierárquica, começando com o contexto do comando interno, com base na seleção de local e prosseguir com o contexto mais externo, com base na seleção global. Os comandos adicionados ao menu principal são imediatamente disponibilizados para scripts. Para obter mais informações, consulte [MenuCommands Vs. OleMenuCommands](../misc/menucommands-vs-olemenucommands.md) e [Objetos de contexto da seleção](../extensibility/internals/selection-context-objects.md).  
  
 Para definir novos menus e barras de ferramentas, você deve descrevê\-los em um arquivo de tabela de comando do Visual Studio \(VSCT\). O modelo de pacote do Visual Studio cria esse arquivo para você, juntamente com os elementos necessários para dar suporte a quaisquer comandos, barras de ferramentas e editores selecionadas no modelo. Como alternativa, você pode escrever seu próprio arquivo. VSCT, usando o esquema xml descrito aqui: [Referência de esquema XML VSCT](../extensibility/vsct-xml-schema-reference.md).  
  
 Para obter mais informações sobre como trabalhar com arquivos. VSCT, consulte [Tabela de comando do Visual Studio \(. Arquivos de VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md), ou tente um do [Explicações passo a passo para elementos de Interface do usuário](../misc/walkthroughs-for-user-interface-elements.md).  
  
 Para obter uma visão mais detalhada de menus e barras de ferramentas, consulte [Design de comando](../extensibility/internals/command-design.md).  
  
## Consulte também  
 [Estendendo Menus e comandos](../extensibility/extending-menus-and-commands.md)   
 [Barras de ferramentas, Menus e comandos](../extensibility/internals/commands-menus-and-toolbars.md)   
 [VSPackages](../extensibility/internals/vspackages.md)