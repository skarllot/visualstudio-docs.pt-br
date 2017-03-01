---
title: "Implementando geradores de arquivo único | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
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
ms.openlocfilehash: fd92e6c24d583cf2a4c4ad2d35f7a726e54b21af
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-single-file-generators"></a>Implementando geradores de arquivo único
Uma ferramenta personalizada — às vezes conhecido como um gerador de arquivo único — pode ser usado para estender o [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] sistemas de projeto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Uma ferramenta personalizada é um componente COM que implementa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Usando esta interface, uma ferramenta personalizada transforma um único arquivo de entrada em um único arquivo de saída. O resultado da transformação pode ser o código-fonte, ou qualquer outra saída que é útil. Dois exemplos de arquivos de código gerados por ferramenta personalizada são código gerado em resposta a alterações nos arquivos gerados usando Web Services descrição Language (WSDL) e um designer visual.  
  
 Quando uma ferramenta personalizada é carregada, ou o arquivo de entrada é salva, o sistema de projeto chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>método e passa uma referência para um <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress>interface de retorno de chamada, no qual a ferramenta pode relatar o andamento para o usuário.</xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>  
  
 O arquivo de saída gerado pela ferramenta personalizada é adicionado ao projeto com uma dependência no arquivo de entrada. O sistema de projeto determina automaticamente o nome do arquivo de saída, com base na cadeia de caracteres retornada pela implementação da ferramenta de personalização do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
  
 Uma ferramenta personalizada deve implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Opcionalmente, oferecer suporte a ferramentas personalizadas a <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>interface para recuperar informações de fontes diferentes do arquivo de entrada.</xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> Em qualquer caso, antes de usar uma ferramenta personalizada, você deve registrá-lo com o sistema ou no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registro local. Para obter mais informações sobre como registrar ferramentas personalizadas, consulte [registrar geradores de arquivo único](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>Consulte também  
 [Determinando o Namespace padrão de um projeto](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Expondo tipos de Designers visuais](../../extensibility/internals/exposing-types-to-visual-designers.md)
