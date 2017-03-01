---
title: Suporte a controle de origem | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
caps.latest.revision: 18
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
ms.openlocfilehash: 0702319ac76eafac3cd05167ff2a3186d83d283c
ms.lasthandoff: 02/22/2017

---
# <a name="supporting-source-control"></a>Suporte a controle de origem
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]oferece suporte a check-out do arquivo, check-ins e outras operações de controle de origem para o projeto ou o editor. Como um cliente de controle de origem, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é projetado para interagir com um pacote de controle de origem, como [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], que fornece arquivamento, controle de versão e recursos de controle para um conjunto de arquivos definido dinamicamente.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Modelo de pacotes de controle de origem](../../extensibility/internals/model-for-source-control-packages.md)  
 Descreve as interfaces que um tipo de projeto deve implementar para oferecer suporte ao controle de origem.  
  
 [Decisões de design](../../extensibility/internals/source-control-design-decisions.md)  
 Fornece perguntas para cujas respostas alterar como implementar um tipo de projeto.  
  
 [Detalhes de configuração](../../extensibility/internals/source-control-configuration-details.md)  
 Descreve como o suporte a controle de origem altera a implementação de um tipo de projeto.  
  
 [Diretrizes adicionais para projetos e editores](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 Aborda as práticas recomendadas para tipos de projeto e editores.  
  
 [Detalhes de tempo de execução](../../extensibility/internals/source-control-runtime-details.md)  
 Descreve como registrar um projeto quando um usuário adiciona a um sistema de controle de origem.  
  
## <a name="reference"></a>Referência  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2></xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Indica o ambiente ou o pacote de controle de origem que um arquivo está prestes a ser alterado na memória ou salva.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Permite que projetos e hierarquias se registrem com controle de origem e obter informações sobre o status de controle do código-fonte.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 Implementado em um sistema de projeto para fornecer controle de origem para arquivos de projeto e itens de projeto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Usado por projetos para consultar o ambiente de permissão para adicionar, remover ou renomear um arquivo ou diretório em uma solução.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Notifica os clientes de alterações que foram feitas em arquivos de projeto ou diretórios.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Tipos de projeto](../../extensibility/internals/project-types.md)  
 Fornece uma visão geral de projetos como blocos de construção básicos do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE). São fornecidos links para tópicos adicionais que explicam como projetos de controle de criação e compilação do código.
