---
title: Adicionando o projeto e modelos de Item de projeto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 17
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
ms.openlocfilehash: 70bf0281d395643d4865a3d783b16f10fbf2d2c4
ms.lasthandoff: 02/22/2017

---
# <a name="adding-project-and-project-item-templates"></a>Adicionando o projeto e modelos de Item de projeto
Quando você cria seus próprios tipos de projeto, você deve fornecer suporte para a adição de novos projetos e itens de projeto usando o padrão [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrado caixas de diálogo (IDE) do ambiente de desenvolvimento. Os tópicos a seguir discutem as técnicas diferentes para adicionar projetos e itens de projeto.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Contexto de projeto](../../extensibility/internals/project-context.md)  
 Explica que o projeto fornece a maioria das informações de contexto de que ocorre no ambiente.  
  
 [Prioridade do projeto](../../extensibility/internals/project-priority.md)  
 Explica que um item de projeto geralmente é um membro de um projeto para ajudar a evitar ambiguidade sobre qual projeto é usado para abrir o item.  
  
 [Projeto de arquivos diversos](../../extensibility/internals/miscellaneous-files-project.md)  
 Fornece informações sobre os dois tipos de editores que podem ser usados para abrir arquivos em um projeto e a função de projeto desempenha na determinação de qual editor a ser usado quando um item de projeto é aberto.  
  
 [Registrando o projeto e modelos de Item](../../extensibility/internals/registering-project-and-item-templates.md)  
 Explica o que ocorre quando um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projeto é criado.  
  
 [Adicionando itens a adicionar novo Item caixas de diálogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Explica o processo de adição de itens para o **Adicionar Novo Item** caixa de diálogo.  
  
 [Adicionando pastas a caixa de diálogo Novo projeto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Fornece um exemplo de como registrar um novo diretório que contém os modelos personalizados disponibilizados por um VSPackage.  
  
 [Adicionando pastas para a caixa de diálogo Novo Item adicionar](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Fornece um exemplo de como registrar um novo conjunto de diretórios para o **Adicionar Novo Item** caixa de diálogo.  
  
 [Comandos definidos pelo IDE para estender sistemas de projeto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Lista os diferentes tipos de itens de comando usadas para ampliar os sistemas de projeto.  
  
 [CATIDs para objetos que normalmente são usados para estender a projetos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Lista CATIDs para objetos que são usados para estender [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] sistemas de projeto.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Como: abrir editores específicos do projeto](../../extensibility/how-to-open-project-specific-editors.md)  
 Fornece instruções passo a passo para abrir um item intrinsecamente associado a um editor específico para um projeto.  
  
 [Como: abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)  
 Fornece instruções passo a passo para abrir um editor padrão.  
  
 [Subtipos de projeto](../../extensibility/internals/project-subtypes.md)  
 Fornece links para tópicos conceituais do subtipo de projeto. Estendem o projeto subtipos existentes [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projetos.  
  
 [Tipos de projeto](../../extensibility/internals/project-types.md)  
 Fornece links para tópicos adicionais que oferecem informações sobre como criar novos tipos de projeto.
