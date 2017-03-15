---
title: "Como criar e remover dependências do projeto | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ProjectDependenciesDlg
helpviewer_keywords:
- vs.build.projectdependencies
- project dependencies
- builds [Visual Studio], setting up
- project build configurations, dependencies
- dependencies, project
- projects [Visual Studio], dependencies
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
caps.latest.revision: 12
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
ms.openlocfilehash: 397db9439dbeead2d719f2cb8778f499d1dcb52c
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-create-and-remove-project-dependencies"></a>Como criar e remover dependências de projeto
Ao compilar uma solução que contém vários projetos, pode ser necessário compilar determinados projetos primeiro, para gerar o código usado por outros projetos. Quando um projeto consome o código executável gerado por outro projeto, o projeto que gera o código é chamado de uma dependência de projeto do projeto que consome o código. Esses relacionamentos de dependência podem ser definidos na caixa de diálogo **Dependências do Projeto**.  
  
### <a name="to-assign-dependencies-to-projects"></a>Para atribuir dependências a projetos  
  
1.  No Gerenciador de Soluções, selecione um projeto.  
  
2.  No menu **Projeto**, escolha **Dependências do Projeto**.  
  
     A caixa de diálogo **Dependências do Projeto** é aberta.  
  
    > [!NOTE]
    >  A opção **Dependências do Projeto** está disponível apenas em uma solução com mais de um projeto.  
  
3.  Na guia **Dependências**, selecione um projeto no menu suspenso **Projeto**.  
  
4.  No campo **Depende de**, marque a caixa de seleção de qualquer outro projeto que deve ser compilado antes desse projeto.  
  
 A solução deve consistir em mais de um projeto antes que seja possível criar dependências de projeto.  
  
### <a name="to-remove-dependencies-from-projects"></a>Para remover dependências de projetos  
  
1.  No Gerenciador de Soluções, selecione um projeto.  
  
2.  No menu **Projeto**, escolha **Dependências do Projeto**.  
  
     A caixa de diálogo **Dependências do Projeto** é aberta.  
  
    > [!NOTE]
    >  A opção **Dependências do Projeto** está disponível apenas em uma solução com mais de um projeto.  
  
3.  Na guia **Dependências**, selecione um projeto no menu suspenso **Projeto**.  
  
4.  No campo **Depende de**, desmarque as caixas de seleção ao lado de outros projetos que não são mais dependências desse projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Compilando e limpando projetos e soluções no Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Compilando e criando](../ide/compiling-and-building-in-visual-studio.md)   
 [Noções sobre configurações de build](../ide/understanding-build-configurations.md)   
 [NIB: como modificar as propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
