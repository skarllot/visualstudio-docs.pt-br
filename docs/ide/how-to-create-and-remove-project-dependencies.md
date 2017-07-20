---
title: "Como criar e remover dependências do projeto | Microsoft Docs"
ms.custom: 
ms.date: 06/21/2017
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d2f4eba36e9069a35cf279ccf1c78f72a51d77a1
ms.openlocfilehash: 896da11aa3bc92d153608dc09778817a77eaf7d6
ms.contentlocale: pt-br
ms.lasthandoff: 06/23/2017

---
# Como criar e remover dependências de projeto
<a id="how-to-create-and-remove-project-dependencies" class="xliff"></a>
Ao compilar uma solução que contém vários projetos, pode ser necessário compilar determinados projetos primeiro, para gerar o código usado por outros projetos. Quando um projeto consome o código executável gerado por outro projeto, o projeto que gera o código é chamado de uma dependência de projeto do projeto que consome o código. Esses relacionamentos de dependência podem ser definidos na caixa de diálogo **Dependências do Projeto**.  

### Para atribuir dependências a projetos
<a id="to-assign-dependencies-to-projects" class="xliff"></a>  

1.  No Gerenciador de Soluções, selecione um projeto.  

2.  No menu **Projeto**, escolha **Dependências do Projeto**.  

     A caixa de diálogo **Dependências do Projeto** é aberta.  

    > [!NOTE]
    >  A opção **Dependências do Projeto** está disponível apenas em uma solução com mais de um projeto.  

3.  Na guia **Dependências**, selecione um projeto no menu suspenso **Projeto**.  

4.  No campo **Depende de**, marque a caixa de seleção de qualquer outro projeto que deve ser compilado antes desse projeto.  

 A solução deve consistir em mais de um projeto antes que seja possível criar dependências de projeto.  

### Para remover dependências de projetos
<a id="to-remove-dependencies-from-projects" class="xliff"></a>  

1.  No Gerenciador de Soluções, selecione um projeto.  

2.  No menu **Projeto**, escolha **Dependências do Projeto**.  

     A caixa de diálogo **Dependências do Projeto** é aberta.  

    > [!NOTE]
    >  A opção **Dependências do Projeto** está disponível apenas em uma solução com mais de um projeto.  

3.  Na guia **Dependências**, selecione um projeto no menu suspenso **Projeto**.  

4.  No campo **Depende de**, desmarque as caixas de seleção ao lado de outros projetos que não são mais dependências desse projeto.  

## Consulte também
<a id="see-also" class="xliff"></a>  
 [Compilando e limpando projetos e soluções no Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Compilando e criando](../ide/compiling-and-building-in-visual-studio.md)   
 [Noções sobre configurações de build](../ide/understanding-build-configurations.md)   
 [Gerenciando propriedades de solução e de projeto](managing-project-and-solution-properties.md)


