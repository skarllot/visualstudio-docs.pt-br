---
title: Contexto do projeto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: 10
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
ms.openlocfilehash: d74d804f65338edb589e63dde111e2ec1a4b5c6f
ms.lasthandoff: 02/22/2017

---
# <a name="project-context"></a>Contexto de projeto
Quando o usuário adiciona ou funciona com projetos e itens de projeto, o IDE usa a noção de contexto de projeto para determinar como as várias operações devem ser executadas.  
  
 Normalmente, os arquivos são os objetos de projeto padrão que o usuário cria explicitamente selecionando o **novo projeto** comando ou disponibiliza selecionando o **Abrir projeto** comando o **arquivo** menu. Nesses casos, os arquivos são criados e abertos no contexto de um projeto e o tipo de projeto define o contexto de edição do documento.  
  
 Alguns projetos fornecem um contexto muito sofisticado. Por exemplo, o projeto gerencia um namespace no escopo do projeto, através de programação ou uma conexão de banco de dados de projeto para vinculação de dados. O usuário pode abrir com frequência arquivos ou conexões de banco de dados usando um objeto de projeto específico, como um item de projeto exibido no Solution Explorer.  
  
 Em outras ocasiões, o contexto do projeto de um item não for especificado explicitamente. Por exemplo, o contexto de um item não está disponível quando o usuário abre um arquivo, selecionando o **abrir arquivo existente** comando o **arquivo** menu, quando o depurador opera em um arquivo ou quando o usuário clica o **localizar nos arquivos** do **localizar e substituir** caixa de diálogo. Para lidar com essas situações, o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>para gerenciar o processo de localizar o melhor projeto para abrir um documento.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>  
  
## <a name="see-also"></a>Consulte também  
 [Prioridade do projeto](../../extensibility/internals/project-priority.md)   
 [Adicionando o projeto e modelos de Item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)
