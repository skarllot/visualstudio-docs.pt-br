---
title: "Como alterar o diretório de saída do build | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 14
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: a5a83605bc532fdb2a8122b0662fd7d3f7ebf945

---
# <a name="how-to-change-the-build-output-directory"></a>Como alterar o diretório de saída do build
Você pode especificar o local de saída por configuração (para depuração, versão ou ambas) gerada pelo projeto.  
  
> [!NOTE]
>  Se você tiver um projeto de **Instalação**, consulte a observação no final deste artigo.  
  
## <a name="changing-the-build-output-directory"></a>Alterando o diretório de saída do build  
  
#### <a name="to-change-the-build-output-directory"></a>Para alterar o diretório de saída do build  
  
1.  Na barra de menus, escolha **Projeto**, **Propriedades** do *Appname*. Você também pode clicar com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e selecionar **Propriedades**.  
  
2.  Se você tiver um projeto do Visual Basic, selecione a guia **Compilar**. Se você tiver um projeto do Visual C#, selecione a guia **Build**. Se você tiver um projeto C++ ou um projeto de JavaScript, selecione a guia **Geral**.  
  
3.  Na lista suspensa de configuração na parte superior, escolha a configuração cujo local do arquivo de saída você deseja alterar (depuração, versão ou todos).  
  
     Localize a entrada do caminho de saída (**Caminho de Saída do Build** no Visual Basic, **Diretório de Saída** no Visual C++, **Caminho de Saída** no JavaScript e C#). Especifique um novo diretório de saída de build em relação ao diretório do projeto.  
  
> [!NOTE]
>  Em um Projeto de Instalação, a caixa **Nome do arquivo de saída** muda apenas o local do arquivo Setup.exe, não o local dos arquivos de projeto. Para obter mais informações, consulte **Build, Configuration Properties, Deployment Project Properties Dialog Box** (Caixa de diálogo Build, Propriedades de Configuração, Propriedades do Projeto de Implantação).  
  
## <a name="see-also"></a>Consulte também  
 [Página de Build, Designer de Projeto (C#)](../ide/reference/build-page-project-designer-csharp.md)   
 [Página de propriedade geral (projeto)](/visual-cpp/ide/general-property-page-project)   
 [Compilando e criando](../ide/compiling-and-building-in-visual-studio.md)


<!--HONumber=Feb17_HO4-->


