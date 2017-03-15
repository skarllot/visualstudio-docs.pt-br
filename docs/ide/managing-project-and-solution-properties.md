---
title: "Gerenciando propriedades de solução e projeto | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d727efc0-1096-4ede-84b6-31a65da22ac0
caps.latest.revision: 6
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
ms.openlocfilehash: e843adb473be51e185fd3b5dc514b44f16106157
ms.lasthandoff: 02/22/2017

---
# <a name="managing-project-and-solution-properties"></a>Gerenciando propriedades de solução e projeto
Projetos têm propriedades que controlam muitos aspectos da compilação, da depuração, do teste e da implantação. Algumas propriedades são comuns entre todos os tipos de projeto, e algumas são exclusivas de linguagens ou plataformas específicas. Acesse propriedades do projeto clicando com o botão direito do mouse no nó do projeto no Gerenciador de Soluções e escolhendo Propriedades ou digitando as propriedades na caixa de pesquisa **QuickLaunch** na barra de menus.  
  
 ![Menu de contexto do projeto](../ide/media/vs2015_proj_prop_menu.gif "vs2015_proj_prop_menu")  
  
 Projetos do .NET também têm um nó de propriedades na árvore do projeto em si.  
  
 ![Nó de propriedades na árvore do Gerenciador de Soluções](../ide/media/vs2015_props_se.png "VS2015_Props_SE")  
  
> [!TIP]
>  As soluções têm algumas propriedades, bem como os itens de projeto; essas propriedades são acessadas na [Janela Propriedades](../ide/reference/properties-window.md), não no **Designer de Projeto**.  
  
## <a name="project-properties"></a>Propriedades do projeto  
 Propriedades do Projeto são organizadas em grupos, cada grupo tem sua própria página de propriedades, e as páginas podem ser diferentes para diferentes linguagens e tipos de projeto.  
  
### <a name="c-and-visual-basic-projects"></a>Projetos em C# e Visual Basic  
 Em projetos C# e Visual Basic, as propriedades são expostas no **Designer de Projeto**. A ilustração a seguir mostra a página de propriedades Build para um projeto WPF em C#:  
  
 ![Designer de Projeto do Visual Studio](../ide/media/vs2015_proppage_build.png "VS2015_PropPage_Build")  
  
 Para obter informações sobre cada uma das páginas de propriedades no Designer de Projeto, consulte [Referência de Propriedades de Projeto](../ide/reference/project-properties-reference.md).  
  
### <a name="c-and-javascript-projects"></a>Projetos em C++ e JavaScript  
 Projetos em C++ e JavaScript têm uma interface do usuário diferente para gerenciar propriedades do projeto. Esta ilustração mostra uma página de propriedades de projeto em C++ (páginas em JavaScript são semelhantes):  
  
 ![Propriedades do projeto em Visual C&#43;&#43;](../ide/media/vs2015_projprops_cpp.png "VS2015_ProjProps_cpp")  
  
 Para obter informações sobre propriedades de projeto C++, consulte [Trabalhando com propriedades do projeto](/visual-cpp/ide/working-with-project-properties). Para obter mais informações sobre as propriedades de JavaScript, consulte [Páginas de propriedades, JavaScript](../ide/reference/property-pages-javascript.md).  
  
## <a name="solution-properties"></a>Propriedades da solução  
 Para acessar propriedades na solução, clique com o botão direito do mouse no nó da solução no **Gerenciador de Soluções** e escolha **Propriedades**. Na caixa de diálogo, você pode definir configurações de projeto para compilações de Depuração ou Versão, escolher quais projetos devem ser o projeto de inicialização quando F5 é pressionado e definir opções de análise de código.  
  
## <a name="see-also"></a>Consulte também  
 [Soluções e projetos no Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
