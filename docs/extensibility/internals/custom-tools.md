---
title: Ferramentas personalizadas | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 21
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
ms.openlocfilehash: cb077e92ad15dc3bf66511765782003f3f3d0a22
ms.lasthandoff: 02/22/2017

---
# <a name="custom-tools"></a>Ferramentas personalizadas
*Ferramentas personalizadas* permitem que você associe uma ferramenta de um item em um projeto e executar essa ferramenta, sempre que o arquivo é salvo. Determinadas ferramentas personalizadas, às vezes chamados de *geradores de arquivo único*, são usados para implementar os conversores que geram código de dados e vice-versa. Por exemplo, criar geradores de arquivo único [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] código fora os arquivos. resx e Settings. O código-fonte gerado fornece acesso fortemente tipado aos dados nos arquivos. resx e de Settings. O [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ferramentas personalizadas; suportam a tipos de projeto [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] não tipos de projeto. Seus próprios tipos de projeto também podem oferecer suporte a ferramentas personalizadas.  
  
 Ferramentas personalizadas são registrados componentes que implementam o `IVsSingleFileGenerator` interface.  
  
 Ferramentas personalizadas são associadas com um `ProjectItem` objeto de interface e são como editores e designers. Uma ferramenta personalizada usa o arquivo representado por uma `ProjectItem` como entrada e grava um novo arquivo cujo nome de arquivo é fornecido pelo `DefaultExtension` método.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Implementando geradores de arquivo único](../../extensibility/internals/implementing-single-file-generators.md)  
 Descreve como usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>interface para implementar uma ferramenta personalizada.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
  
 [Determinando o namespace padrão de um projeto](../../misc/determining-the-default-namespace-of-a-project.md)  
 Descreve como determinar o namespace correto com base no idioma que está sendo usado.  
  
 [Registrar geradores de arquivo único](../../extensibility/internals/registering-single-file-generators.md)  
 Fornece descrições de todas as entradas do registro para uma ferramenta personalizada.  
  
 [Expondo tipos de Designers visuais](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Explica como sistemas de projeto oferecem suporte para designers visuais para acesso gerado classes e tipos de arquivos temporários PE (portable executable).  
  
 [Mantendo a propriedade de um Item de projeto](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Mostra como manter uma propriedade de item de projeto, como o autor de um arquivo de origem, no arquivo de projeto.  
  
## <a name="reference"></a>Referência  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator></xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Fornece detalhes sobre o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, que transforma um único arquivo de entrada em um único arquivo de saída que pode ser compilado ou adicionado a um projeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
  
 <xref:EnvDTE.ProjectItem></xref:EnvDTE.ProjectItem>  
 Explica o `ProjectItem` interface, que representa um item em um projeto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Fornece detalhes sobre o `DefaultExtension` método, que recupera a extensão de nome de arquivo que é fornecida para o nome do arquivo de saída.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Estendendo projetos](../../extensibility/extending-projects.md)  
 Descreve como usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projetos e soluções para organizar arquivos de código e arquivos de recurso e como implementar o controle de origem.
