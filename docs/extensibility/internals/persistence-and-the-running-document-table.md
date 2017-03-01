---
title: "Tabela de documentos de persistência e execução | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
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
ms.openlocfilehash: c5d3a440112c324f626377226a6c9db174c7ca4b
ms.lasthandoff: 02/22/2017

---
# <a name="persistence-and-the-running-document-table"></a>A tabela de documento em execução e persistência
No [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, os projetos são totalmente responsáveis por gerenciar a persistência de seus itens de projeto, eles realizar usando o serviço, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>.</xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> Documentos são a unidade básica de persistência no ambiente do Visual Studio. Projetos de coordenam a abertura, salvando e renomeação de documentos com execução tabela document (RDT), um recurso que rastreia o estado de todos os documentos abertos.  
  
## <a name="managing-persistence"></a>Gerenciamento de persistência  
 Projetos de controle de serviço de persistência do ambiente Implementando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> Enquanto o ambiente nunca diretamente solicita um documento para persistir em si, ele solicita o projeto proprietário (ou hierarquia) para salvar o documento. Isso torna possível para o projeto salvar seus dados de item de projeto em arquivos locais, arquivos remotos, um banco de dados, um repositório ou outra mídia.  
  
 O ambiente global mantém o RDT. O ambiente mantém entradas para todas as janelas abertas e documentos em RDT, o que torna possível para que eles possam recebem notificações especiais, como quando uma solução é fechada. Além disso, a RDT possibilita o ambiente controlar seus nós correspondentes na **Solution Explorer**. O RDT mantém um registro por objeto aberto, persistente, incluindo arquivos de projeto e item de projeto de documentos.  
  
## <a name="see-also"></a>Consulte também  
 [Tabela de documento em execução](../../extensibility/internals/running-document-table.md)   
 [Seleção e moeda no IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
