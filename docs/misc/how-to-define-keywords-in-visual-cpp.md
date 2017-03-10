---
title: "Como definir palavras-chave no Visual C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "palavras-chave do usuário"
  - "palavras reservadas, palavras-chave definidas pelo usuário"
  - "palavras-chave definidas pelo usuário"
  - "palavras-chave reservadas, definido pelo usuário"
  - "usertype.dat"
  - "palavras-chave [C++], definido pelo usuário"
ms.assetid: 2dfcf343-e861-4bde-b5a4-7deb6773d9c8
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Como definir palavras-chave no Visual C++
Palavras\-chave são identificadores reservados predefinidos com significados especiais. Eles não podem ser usados como identificadores em um programa. No entanto, você pode definir sua próprias palavras\-chave para usar no Visual C\+\+, e você pode atribuir cores para as palavras\-chave personalizadas de sintaxe. Coloração de sintaxe fornece indicações visuais sobre a estrutura e o estado do seu código.  
  
### Para definir sua próprias palavras\-chave do Visual C\+\+  
  
1.  Usar o Visual Studio [código e Editor de texto](http://msdn.microsoft.com/pt-br/508e1f18-99d5-48ad-b5ad-d011b21c6ab1) ou Notepad.exe para criar um arquivo somente de texto chamado `usertype.dat`.  
  
2.  Em `usertype.dat`, digite cada palavra\-chave definidas pelo usuário em uma linha separada.  
  
3.  Salvar `usertype.dat` no diretório que contém devenv.exe. Por padrão, o caminho do diretório é *\< unidade \>*: \\Program Files\\[!INCLUDE[TLA#tla_visualstu](../misc/includes/tlasharptla_visualstu_md.md)] *\< número da versão menor \>*\\Common7\\[!INCLUDE[TLA2#tla_ide](../misc/includes/tla2sharptla_ide_md.md)].  Como esse diretório é somente leitura por padrão, você precisa de credenciais administrativas para salvar `usertype.dat`.  
  
4.  Sair do Visual Studio e reiniciá\-lo.  
  
    > [!NOTE]
    >  Não é possível renomear ou recarregar a `usertype.dat` porque ele é lido durante a inicialização de arquivo durante uma sessão de edição. Tudo definido anteriormente configurações de cores têm precedência porque o mecanismo de cores de sintaxe verifica o `usertype.dat` último arquivo.  
  
5.  No menu **Ferramentas**, clique em **Opções**. No **opções** caixa de diálogo, clique em **ambiente**, em seguida, clique em **fontes e cores**, e, em seguida, no **Exibir itens:** lista, clique em **palavras\-chave de usuário de C\/C\+\+**.  
  
6.  Definir as propriedades de fonte e cor palavras\-chave definidas pelo usuário, conforme descrito em [Caixa de diálogo Fontes e Cores, Ambiente, Opções](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Para obter mais informações, consulte [Palavras\-chave C\+\+](/visual-cpp/cpp/keywords-cpp).  
  
## Consulte também  
 [Executando como um membro do grupo de usuários](/visual-cpp/top/running-as-a-member-of-the-users-group)   
 [Atalhos de teclado padrão](../ide/default-keyboard-shortcuts-in-visual-studio.md)