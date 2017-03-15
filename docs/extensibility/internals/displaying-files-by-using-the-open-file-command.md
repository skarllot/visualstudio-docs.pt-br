---
title: Exibindo arquivos usando o comando Abrir arquivo | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: 13
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
ms.openlocfilehash: 1811b4d207d7ade7bcff89870e6b3dd1e3f92593
ms.lasthandoff: 02/22/2017

---
# <a name="displaying-files-by-using-the-open-file-command"></a>Exibindo arquivos usando o comando Abrir arquivo
As etapas a seguir descrevem como o IDE manipula o **abrir arquivo** comando, que está disponível na **arquivo** menu em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. As etapas também descrevem como projetos devem responder a chamadas originadas desse comando.  
  
 Quando um usuário clica o **abrir arquivo** comando o **arquivo** menu e selecionar um arquivo do **abrir arquivo** caixa de diálogo, o seguinte processo ocorre.  
  
1.  Usando a tabela de documento em execução, o IDE determina se o arquivo já está aberto em um projeto.  
  
    -   Se o arquivo estiver aberto, o IDE resurfaces a janela.  
  
    -   Se o arquivo não estiver aberto, o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>para consultar cada projeto para determinar qual projeto pode abrir o arquivo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>  
  
        > [!NOTE]
        >  Na implementação do projeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>, forneça um valor de prioridade que indica o nível no qual seu projeto abre o arquivo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Valores de prioridade são fornecidos no <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>enumeração.</xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>  
  
2.  Cada projeto responde com um nível de prioridade que indica a importância coloca em sendo o projeto para abrir o arquivo.  
  
3.  O IDE usa os seguintes critérios para determinar qual projeto abre o arquivo:  
  
    -   O projeto que responde com a prioridade mais alta (DP_Intrinsic) abre o arquivo. Se mais de um projeto responde com essa prioridade, o primeiro projeto responder abre o arquivo.  
  
    -   Se nenhum responde de projeto com a prioridade mais alta (DP_Intrinsic), mas todos os responder de projetos com a mesma prioridade inferior, o projeto ativo abre o arquivo. Se nenhum projeto estiver ativo, o primeiro projeto responder abre o arquivo.  
  
    -   Se nenhum projeto declarações de propriedade do arquivo (DP_Unsupported), o projeto de arquivos diversos abre o arquivo.  
  
         Se uma instância do projeto arquivos diversos for criada, o projeto sempre responde com o valor DP_CanAddAsExternal. Esse valor indica que o projeto pode abrir o arquivo. Este projeto é usado para armazenar arquivos abertos que não estão em qualquer outro projeto. A lista de itens no projeto não é persistente; Este projeto está visível no **Solution Explorer** apenas quando ele é usado para abrir um arquivo.  
  
         Se o projeto de arquivos diversos indicar que ele pode abrir o arquivo, uma instância do projeto não foi criada. Nesse caso, o IDE cria uma instância do projeto arquivos diversos e informa ao projeto para abrir o arquivo.  
  
4.  Assim que o IDE determina qual projeto abre o arquivo, ele chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>método no projeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>  
  
5.  O projeto, em seguida, tem a opção de abrir o arquivo usando um editor específico do projeto ou um editor padrão. Para obter mais informações, consulte [como: abrir editores específicos do projeto](../../extensibility/how-to-open-project-specific-editors.md) e [como: abrir editores padrão](../../extensibility/how-to-open-standard-editors.md), respectivamente.  
  
## <a name="see-also"></a>Consulte também  
 [Exibindo arquivos usando o abrir com o comando](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [Abrindo e salvando itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Como: abrir editores específicos do projeto](../../extensibility/how-to-open-project-specific-editors.md)   
 [Como: abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)
