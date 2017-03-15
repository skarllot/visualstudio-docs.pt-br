---
title: Hierarquias no Visual Studio | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
caps.latest.revision: 14
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
ms.openlocfilehash: ca8fa51a14f38dcd651f26e8ed10ca48d670f37b
ms.lasthandoff: 02/22/2017

---
# <a name="hierarchies-in-visual-studio"></a>Hierarquias no Visual Studio
O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o ambiente de desenvolvimento integrado (IDE) exibe um projeto como um *hierarquia*. No IDE, uma hierarquia é uma árvore de nós, onde cada nó tem um conjunto de propriedades associadas. A *projeto hierarquia* é um contêiner que mantém os itens do projeto, relações dos itens e propriedades associadas a itens e comandos.  
  
 Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], gerenciar hierarquias de projeto usando a interface de hierarquia, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> O <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>interface redireciona comandos invocar de itens de projeto para a janela hierarquia apropriada em vez do manipulador de comandos padrão.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>  
  
## <a name="project-hierarchies"></a>Hierarquias de projeto  
 Cada hierarquia de projeto contém itens que você pode exibir e editar. Esses itens variam dependendo do tipo de projeto. Por exemplo, um projeto de banco de dados pode conter procedimentos armazenados, exibições de banco de dados e tabelas de banco de dados. Por outro lado, um projeto de linguagem de programação, provavelmente será incluem arquivos de origem e arquivos de recurso para caixas de diálogo e bitmaps. Hierarquias podem ser aninhadas, que dá a você algumas mais flexibilidade ao criar uma hierarquia de projeto.  
  
 Quando você cria um novo tipo de projeto, o tipo de projeto controla o conjunto completo de itens que podem ser editados nela. No entanto, os projetos podem conter itens para os quais não têm suporte de edição. Por exemplo, os projetos do Visual C++ podem conter arquivos HTML, mesmo que o Visual C++ não oferece qualquer editor personalizado para o tipo de arquivo HTML.  
  
 Hierarquias de gerenciam a persistência de itens que eles contêm. A implementação da hierarquia deve controlar as propriedades especiais que afetam a persistência dos itens dentro da hierarquia. Por exemplo, se os itens representam objetos em um repositório em vez de arquivos, a implementação de hierarquia deve controlar a persistência desses objetos. O próprio IDE direciona a hierarquia para salvar os itens em conformidade com a entrada do usuário, mas o IDE não controla as ações necessárias para salvar esses itens. Em vez disso, o projeto está no controle.  
  
 Quando um usuário abre um item em um editor, a hierarquia que controla esse item é selecionada e se torna a hierarquia ativa. A hierarquia selecionada determina o conjunto de comandos disponíveis para atuar no item. Controle o foco do usuário dessa maneira permite que a hierarquia refletir o contexto do usuário atual.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de projeto](../../extensibility/internals/project-types.md)   
 [Seleção e moeda no IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Exemplos de VSSDK](../../misc/vssdk-samples.md)
