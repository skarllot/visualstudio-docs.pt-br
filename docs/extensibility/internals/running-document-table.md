---
title: "Tabela de documento em execução | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
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
ms.openlocfilehash: ad4283a3627820c53efde15c0ff34d941d7c3fd7
ms.lasthandoff: 02/22/2017

---
# <a name="running-document-table"></a>Tabela de documento em execução
O IDE mantém a lista de todos os documentos abertos em uma estrutura interna chamada tabela de documento (RDT) em execução. Essa lista inclui todos os documentos abertos na memória, independentemente de se esses documentos estão sendo editados atualmente. Um documento é qualquer item que é mantido, incluindo arquivos em um projeto ou o arquivo de projeto principal (por exemplo, um arquivo. vcxproj).  
  
## <a name="elements-of-the-running-document-table"></a>Elementos da tabela documento em execução  
 A tabela de documento em execução contém as entradas a seguir.  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Moniker do documento|Uma cadeia de caracteres que identifica exclusivamente o objeto de dados do documento. Isso seria o caminho de arquivo absoluto para um sistema de projeto que gerencia arquivos (por exemplo, C:\MyProject\MyFile). Essa cadeia de caracteres também é usada para projetos salvos em armazenamentos diferentes sistemas de arquivos, como procedimentos armazenados em um banco de dados. Nesse caso, o sistema de projeto pode inventar uma cadeia de caracteres exclusiva que pode reconhecer e possivelmente analisar para determinar como armazenar o documento.|  
|Proprietário da hierarquia|O objeto de hierarquia que possui o documento, conforme representado por um <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|ID do item|Identificador do item para um item específico dentro da hierarquia. Esse valor é exclusivo entre todos os documentos na hierarquia que possui este documento, mas esse valor não é garantido para ser exclusivo em hierarquias diferentes.|  
|Objeto de dados de documento|No mínimo, isso é um`IUnknown`<br /><br /> . O IDE não requer qualquer interface específica, além de `IUnknown` interface de objeto de dados de documento de um editor personalizado. No entanto, para um editor padrão, a implementação do editor do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>interface é necessária para lidar com chamadas de persistência do arquivo do projeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> Para obter mais informações, consulte [salvando um documento padrão](../../extensibility/internals/saving-a-standard-document.md).|  
|Sinalizadores|Sinalizadores que controlam se o documento é salvo, se um bloqueio de leitura ou edição é aplicado e assim por diante, podem ser especificados quando são adicionadas entradas para o RDT. Para obter mais informações, consulte o <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>enumeração.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>|  
|Editar contagem de bloqueio|Contagem de bloqueios de edição. Um bloqueio de edição indica que algum editor tem o documento aberto para edição. Quando a contagem de bloqueios de editar muda para zero, o usuário é solicitado a salvar o documento, se ele tiver sido modificado. Por exemplo, sempre que você abrir um documento em um editor usando o **nova janela** de comando, um bloqueio de edição é adicionado para o documento no RDT. Em ordem para um bloqueio de edição a ser definido, o documento deve ter uma hierarquia ou item ID.|  
|Contagem de bloqueio de leitura|Contagem de bloqueios de leitura. Um bloqueio de leitura indica que o documento está sendo lido por algum outro mecanismo, como um assistente. Um bloqueio de leitura contém um documento ativo no RDT ao mesmo tempo, indicando que o documento não pode ser editado. Você pode definir um bloqueio de leitura, mesmo se o documento não possui uma hierarquia ou item ID. Esse recurso permite que você abrir um documento na memória e insira o RDT sem o documento que pertença a qualquer hierarquia. Esse recurso é raramente usado.|  
|Proprietário do bloqueio|Uma instância de um <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> O proprietário do bloqueio é implementado por recursos como assistentes que abrir e editar documentos fora de um editor. Um proprietário de bloqueio permite que o recurso Adicionar um bloqueio de editar o documento para impedir que o documento está sendo fechado enquanto ele ainda está sendo editado. Normalmente, editar bloqueios só são adicionados por janelas de documento (ou seja, editores).|  
  
 Cada entrada de RDT tem uma hierarquia exclusiva ou a ID do item associado a ele, que geralmente corresponde a um nó do projeto. Todos os documentos disponíveis para edição normalmente pertencem a uma hierarquia. As entradas feitas no RDT controlam qual projeto, ou — com mais precisão — a hierarquia, que atualmente possui o objeto de dados do documento que está sendo editado. Usando as informações de RDT, o IDE pode impedir que um documento que está sendo aberto por mais de um projeto por vez.  
  
 A hierarquia também controla a persistência de dados e usa as informações de RDT para atualizar o **salvar** e **Salvar como** caixas de diálogo. Quando os usuários modificar um documento e, em seguida, escolha o **Exit** comando o **arquivo** menu, o IDE solicita-las com o **salvar alterações** caixa de diálogo para mostrar todos os projetos e itens de projeto são modificados no momento. Isso permite aos usuários escolher qual salvar os documentos. A lista de documentos para salvar (ou seja, aqueles documentos que têm alterações) é gerada a partir de RDT. Todos os itens que você esperava ver no **salvar alterações** caixa de diálogo ao sair do aplicativo deve ter registros no RDT. O RDT coordena quais documentos são salvos e se o usuário é avisado sobre salvar operação usando os valores especificados na entrada de sinalizadores para cada documento. Para obter mais informações sobre os sinalizadores RDT, consulte o <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>enumeração.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>  
  
## <a name="edit-locks-and-read-locks"></a>Bloqueios de editar e bloqueios de leitura  
 Bloqueios de editar e bloqueios de leitura residam na RDT. Os incrementos de janela de documento e diminui a edição de bloqueio. Portanto, quando um usuário abre uma nova janela de documento, os incrementos de contagem de bloqueio de editar por um. Quando o número de bloqueios de editar chega a zero, a hierarquia é sinalizada para persistir ou salvar os dados para o documento associado. A hierarquia pode persistir os dados de forma alguma, incluindo a persistir como um arquivo ou um item em um repositório. Você pode usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A>método o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>interface Adicionar bloqueios de editar e bloqueios de leitura e o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>método para remover esses bloqueios.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> </xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A>  
  
 Normalmente, quando a janela de documento de um editor é instanciada, o quadro de janela adiciona automaticamente um bloqueio de edição para o documento no RDT. No entanto, se você criar uma exibição personalizada de um documento que não use uma janela de documento padrão (ou seja, ele não implementa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>interface), você precisará definir seu próprio bloqueio de edição.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Por exemplo, um assistente, um documento é editado sem ser aberto em um editor. Bloqueios de documento a ser aberto por assistentes e entidades semelhantes, essas entidades devem implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> Para registrar seu proprietário de bloqueio de documento, chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>método e passar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>implementação.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> </xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> Isso adiciona o proprietário do bloqueio de documento para o RDT. Outro cenário para a implementação de um proprietário de bloqueio de documento é se você abrir um documento por meio de uma janela de ferramenta especial. Nesse caso, não será possível ter a janela da ferramenta fechar o documento. No entanto, ao se registrar como um proprietário de bloqueio de documento no RDT, o IDE pode chamar sua implementação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A>método para solicitar um fechamento do documento.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A>  
  
## <a name="other-uses-of-the-running-document-table"></a>Outros usos da tabela de documento em execução  
 Outras entidades no IDE usam o RDT para obter informações sobre os documentos. Por exemplo, o Gerenciador de controle de origem usa o RDT informar ao sistema para recarregar um documento no editor, depois que ele obtém a versão mais recente do arquivo. Para fazer isso, o Gerenciador de controle de origem procura os arquivos no RDT para ver se algum deles está aberto. Se estiverem, o Gerenciador de controle de origem primeiro verifica para ver que a hierarquia implementa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> Se o projeto não implementa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>método e, em seguida, a fonte de controle manager procura uma implementação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>método no objeto de dados de documento diretamente.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>  
  
 O IDE também usa o RDT para repavimentar (Trazer para frente) um documento aberto, se um usuário solicitar esse documento. Para obter mais informações, consulte [exibindo arquivos usando o comando Abrir do arquivo](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Para determinar se um arquivo é aberto no RDT, siga um procedimentos.  
  
-   Consultar o moniker do documento (ou seja, o caminho completo do documento) descobrir se o item estiver aberto.  
  
-   Use a ID de hierarquia ou um item para pedir que o sistema de projeto para o caminho completo do documento e, em seguida, pesquise o item no RDT.  
  
## <a name="see-also"></a>Consulte também  
 [Uso de RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)   
 [A tabela de documento em execução e persistência](../../extensibility/internals/persistence-and-the-running-document-table.md)
