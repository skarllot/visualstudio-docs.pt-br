---
title: "Persistência de projeto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: 11
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
ms.openlocfilehash: 556dc7bd75de2192fdd08af6cc440da5caea11d9
ms.lasthandoff: 02/22/2017

---
# <a name="project-persistence"></a>Persistência de projeto
Persistência é uma consideração importante no design do seu projeto. A maioria dos projetos usar itens de projeto que representam arquivos; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] também oferece suporte a projetos cujos dados são não baseados em arquivo. Os arquivos de propriedade do projeto e o arquivo de projeto devem ser persistidos. O IDE instrui o projeto para salvar a mesmo ou um item de projeto.  
  
 Modelos para projetos são passados para a fábrica do projeto. Os modelos devem oferecer suporte a inicialização de todos os itens de projeto de acordo com os requisitos do tipo de projeto específico. Esses modelos posteriormente podem ser salvos como arquivos de projeto e gerenciados pelo IDE por meio da solução. Para obter mais informações, consulte [criar projeto instâncias por usando projeto fábricas](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) e [soluções](../../extensibility/internals/solutions.md).  
  
 Itens de projeto podem ser baseada em arquivo ou baseados em arquivo:  
  
-   Itens com base em arquivo podem ser local ou remoto. Em projetos Web em c#, por exemplo, conexões com arquivos em um sistema remoto persistem localmente, enquanto os próprios arquivos permanecem no sistema remoto.  
  
-   Itens não baseados em arquivo podem salvar itens em um banco de dados ou um repositório.  
  
## <a name="commit-models"></a>Confirmar modelos  
 Depois de decidir onde se encontram os itens de projeto, você deve escolher o modelo apropriado de confirmação. Por exemplo, em um modelo baseado em arquivo com arquivos locais, cada projeto pode ser salvo autonomia. Em um modelo de repositório, você pode salvar vários itens em uma transação. Para obter mais informações, consulte [decisões de Design de tipo de projeto](../../extensibility/internals/project-type-design-decisions.md).  
  
 Para determinar as extensões de nome de arquivo, os projetos de implementam o <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>interface, que fornece informações permitindo que o cliente de um objeto que implemente o **Salvar como** caixa de diálogo — ou seja, preencha o **Salvar como tipo** suspensa listar e gerenciar a extensão de nome de arquivo inicial.</xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>  
  
 O IDE chama o `IPersistFileFormat` interface no projeto para indicar que o projeto deve manter seu projeto itens conforme apropriado. Portanto, o objeto possui todos os aspectos de seu arquivo e formato. Isso inclui o nome do formato do objeto.  
  
 No caso em que itens não são arquivos, `IPersistFileFormat` ainda é como não-file-based itens são mantidos. Projeto de arquivos, como arquivos. vbp para [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] arquivos de projetos ou. vcproj para [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projetos, também deve ser mantido.  
  
 Para salvar as ações, o IDE examina a tabela de documento (RDT) em execução e a hierarquia passa os comandos para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem>e o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>interfaces.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> O <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A>método é implementado para determinar se o item foi modificado.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> Se o item tiver, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A>método é implementado para salvar o item modificado.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A>  
  
 Os métodos de `IVsPersistHierarchyItem2` interface são usados para determinar se um item pode ser recarregado e, se o item pode ser para recarregá-lo. Além disso, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A>método pode ser implementado para fazer com que itens alterados sejam descartados sem ser salvado.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A>  
  
## <a name="see-also"></a>Consulte também  
 [Lista de verificação: Criar novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Criação de instâncias de projetos usando fábricas de projeto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
