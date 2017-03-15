---
title: "Suporte a vários modos de exibição de documento | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: 25
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
ms.openlocfilehash: acb177a86d49958efb5855213de6121383929434
ms.lasthandoff: 02/22/2017

---
# <a name="supporting-multiple-document-views"></a>Suporte a vários modos de exibição de documento
Você pode fornecer mais de uma exibição de um documento, criando dados de documentos separada e objetos de exibição de documento para o editor. Alguns casos em que uma exibição de documento adicionais seria útil são:  
  
-   Novo suporte de janela: você deseja que o editor fornecer dois ou mais modos de exibição do mesmo tipo, para que um usuário que já tem uma janela aberto no editor pode abrir uma nova janela selecionando o **nova janela** comando o **janela** menu.  
  
-   Exibir o formulário e código suporte: você deseja que o editor fornecer modos de exibição de tipos diferentes. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], por exemplo, fornece um modo de exibição de formulário e um modo de exibição de código.  
  
 Para obter mais informações sobre isso, consulte o procedimento CreateEditorInstance no arquivo EditorFactory.cs no projeto editor personalizado criado pelo modelo de pacote do Visual Studio. Para obter mais informações sobre esse projeto, consulte [passo a passo: Criando um Editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
## <a name="synchronizing-views"></a>Sincronizando modos de exibição  
 Quando você implementa vários modos de exibição, o objeto de dados de documentos é responsável por manter sincronizadas com os dados de todas as exibições. Você pode usar o evento tratamento interfaces em <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>para sincronizar vários modos de exibição com os dados.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>  
  
 Se você não usar o <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>objeto para sincronizar vários modos de exibição, em seguida, você deve implementar seu próprio sistema de eventos para lidar com as alterações feitas no objeto de dados do documento.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Você pode usar diferentes níveis de granularidade para manter vários modos de exibição atualizado. Com uma configuração de granularidade máximo, conforme você digita em um modo de exibição de outros modos de exibição são atualizados imediatamente. Com granularidade mínima, outros modos de exibição não serão atualizados até que eles são ativados.  
  
## <a name="determining-whether-document-data-is-already-open"></a>Determinar se os dados dos documentos ainda estiver aberto  
 A tabela de documento (RDT) em execução no ambiente de desenvolvimento integrado (IDE) ajuda a controlar se os dados para um documento já estão abertos, conforme mostrado no diagrama a seguir.  
  
 ![Gráfico de DocDataView](../extensibility/media/docdataview.gif "Docdataview")  
Várias exibições  
  
 Por padrão, cada modo de exibição (objeto de exibição de documento) é contido em seu próprio quadro de janela (<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>).</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Como já mencionado, no entanto, os dados de documentos podem ser exibidos em vários modos de exibição. Para habilitar isso, o Visual Studio verifica o RDT para determinar se o documento em questão já está aberto em um editor. Quando o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>para criar o editor, um valor não nulo retornado no `punkDocDataExisting` parâmetro indica que o documento já está aberto em outro editor.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Para obter mais informações sobre como as funções RDT, consulte [executando tabela Document](../extensibility/internals/running-document-table.md).  
  
 No seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>implementação, examine o objeto de dados de documento retornado `punkDocDataExisting` para determinar se os dados do documento são apropriados para seu editor.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> (Por exemplo, somente os dados HTML devem ser exibidos por um editor de HTML.) Se for o caso, a fábrica do editor deve fornecer um segundo modo de exibição para os dados. Se o `punkDocDataExisting` parâmetro não é `NULL`, é possível também que o objeto de dados de documento é aberto em outro editor, ou, mais provavelmente, que os dados do documento já estão abertos em uma exibição diferente com o mesmo editor. Se os dados do documento estão abertos em um editor diferente que não oferece suporte a sua fábrica de editor, o Visual Studio não abrir sua fábrica de editor. Para obter mais informações, consulte [como: anexar modos de exibição para dados de documentos](../extensibility/how-to-attach-views-to-document-data.md).
