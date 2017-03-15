---
title: Subtipos do projeto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: 20
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
ms.openlocfilehash: 985a1ab16dd6ce379afa7cd15624fcf941c82fd6
ms.lasthandoff: 02/22/2017

---
# <a name="project-subtypes"></a>Subtipos de projeto
Subtipos de projeto permitem que você personalizar ou parecida com o comportamento dos sistemas de projeto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Personalizações incluem salvar dados adicionais no arquivo de projeto, adicionando ou filtrar itens na **Adicionar Novo Item** caixa de diálogo, controlar como os assemblies devem ser depurados e implantados e estendendo o projeto **páginas de propriedade** caixa de diálogo. Os VSPackages implementar subtipos de projeto usando a agregação COM.  
  
> [!NOTE]
>  O sistema de projetos do Visual C++ não oferece suporte para os subtipos de projeto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Se usa subtipos de projeto para implementar projetos do SQL Server e dispositivos inteligentes.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Design de subtipos de projeto](../../extensibility/internals/project-subtypes-design.md)  
 Descreve o conceito de subtipos de projeto.  
  
 [Sequência de inicialização do projeto subtipos](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Descreve a sequência de inicialização do projeto programático subtipo por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente.  
  
 [Propriedades e métodos estendidos por subtipos de projeto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Fornece descrições detalhadas dos recursos e métodos estendidos com mais frequência usando subtipos de projeto.  
  
 [Manter os dados no arquivo de projeto do MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Descreve como manter os dados em um arquivo de projeto e como usar <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>para manter os dados no arquivo de projeto entre os níveis de agregação de subtipo de projeto.</xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>  
  
 [Interface de usuário de propriedades do projeto](../../extensibility/internals/project-property-user-interface.md)  
 Descreve como os subtipos de projeto podem modificar o projeto **páginas de propriedade** caixa de diálogo.  
  
 [Estendendo o modelo de objeto do projeto Base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Fornece informações sobre como os subtipos de projeto podem usar extensores de automação para estender o modelo de objeto de automação.  
  
 [Contribuindo para a caixa de diálogo Novo Item adicionar](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Descreve como adicionar itens para o **Adicionar Novo Item** caixa de diálogo.  
  
 [Salvando dados em arquivos de projeto](../../extensibility/saving-data-in-project-files.md)  
 Explica como um subtipo de projeto pode salvar e recuperar dados específicos subtipo-no arquivo de projeto usando o Framework de pacote gerenciados (MPF).  
  
 [Tratamento especializadas de implantação](../../extensibility/internals/handling-specialized-deployment.md)  
 Explica como subtipos de projeto podem fornecer o comportamento de implantação especializadas Implementando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>  
  
 [Adicionando e removendo páginas de propriedade](../../extensibility/adding-and-removing-property-pages.md)  
 Descreve a adição e remoção de páginas de propriedade no Designer de projeto.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Tipos de projeto](../../extensibility/internals/project-types.md)  
 Fornece links para tópicos detalhando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projetos.
