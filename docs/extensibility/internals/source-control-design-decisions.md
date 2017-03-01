---
title: "Decisões de Design do controle de origem | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: 12
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
ms.openlocfilehash: ef498359cff47f0eb325d2b6440b4a1e35d0435e
ms.lasthandoff: 02/22/2017

---
# <a name="source-control-design-decisions"></a>Decisões de Design do controle de origem
As decisões de design a seguir devem ser consideradas para projetos ao implementar o controle de origem.  
  
## <a name="will-information-be-shared-or-private"></a>Informações será compartilhado ou particular?  
 A decisão de design mais importante que você pode fazer é quais informações são compartilháveis e qual particular. Por exemplo, a lista de arquivos para o projeto compartilhada, mas dentro dessa lista de arquivos, alguns usuários talvez queira ter arquivos particulares. Configurações de compilador são compartilhadas, mas o projeto de inicialização é geralmente particular. As configurações são puramente compartilhado, compartilhado com uma substituição ou puramente privada. Por design, itens particulares, como arquivos de (configuração. suo), opções de usuário de solução não são verificadas em [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]. Certifique-se de armazenar informações particulares em arquivos particulares, como o arquivo. suo ou um arquivo particular específico, você cria, por exemplo, um. csproj.user arquivo em Visual c# ou. vbproj.user arquivo para o Visual Basic.  
  
 Essa decisão não é completa e pode ser feita em uma base de item por item.  
  
## <a name="will-the-project-include-special-files"></a>O projeto inclui arquivos especiais?  
 Outra decisão de design importante é se a estrutura do projeto usa arquivos especiais. Arquivos especiais são arquivos ocultos que sustenta os arquivos que são caixas de diálogo visível no Gerenciador de soluções e no check-in e check-out. Se você usar arquivos especiais, siga estas diretrizes:  
  
1.  Não associar arquivos especiais no nó raiz do projeto — ou seja, com o projeto de arquivos em si. O arquivo de projeto deve ser um único arquivo.  
  
2.  Quando arquivos especiais são adicionados, removidos ou renomeados em um projeto, apropriado <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>os eventos devem ser disparados com o conjunto de sinalizador que indica que os arquivos são arquivos especiais.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> Esses eventos são chamados pelo ambiente em resposta ao projeto de chamada apropriada <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>métodos.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
  
3.  Quando seu projeto ou editor chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>para um arquivo, os arquivos especiais associados a esse arquivo não são automaticamente checked out.</xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Passe os arquivos especiais juntamente com o arquivo pai. O ambiente detectará a relação entre todos os arquivos que são passados e ocultar adequadamente os arquivos especiais na interface do usuário de fazer check-out.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Suporte a controle de origem](../../extensibility/internals/supporting-source-control.md)
