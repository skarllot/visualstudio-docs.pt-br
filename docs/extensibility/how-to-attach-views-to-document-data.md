---
title: "Como: anexar modos de exibição para dados de documentos | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
caps.latest.revision: 22
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
ms.openlocfilehash: 53e024f0ab9ddc0c55d71dff18b0b3dc130aaeac
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-attach-views-to-document-data"></a>Como: anexar modos de exibição para dados de documentos
Se você tiver um novo modo de exibição de documento, você poderá anexá-lo a um objeto de dados de documento existente.  
  
### <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Para determinar se você pode anexar um modo de exibição para um objeto de dados de documento existente  
  
1.  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
2.  Na implementação do `IVsEditorFactory::CreateEditorInstance`, chame `QueryInterface` sobre o objeto de dados de documento existente quando o IDE chama o `CreateEditorInstance` implementação.  
  
     Chamando `QueryInterface` permite que você examine o objeto de dados de documento existente, que é especificado no `punkDocDataExisting` parâmetro.  
  
     As interfaces exatas, você deverá consultar, no entanto, depende do editor que é abrir o documento, conforme descrito na etapa 4.  
  
3.  Se você não encontrar as interfaces apropriadas no objeto de dados existente do documento e retornar um código de erro para o seu editor indicando que o objeto de dados do documento é incompatível com o seu editor.  
  
     Na implementação do IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, uma caixa de mensagem avisará que o documento está aberto em outro editor e pergunta se você deseja feche-o.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>  
  
4.  Se você fechar este documento, o Visual Studio chama sua fábrica de editor para uma segunda vez. Nessa chamada, o `DocDataExisting` parâmetro for igual a nulo. A implementação de fábrica de editor pode abrir o objeto de dados de documento no seu próprio editor.  
  
    > [!NOTE]
    >  Para determinar se você pode trabalhar com um objeto de dados de documento existente, você também pode usar privado conhecimento sobre a implementação da interface por um ponteiro para o valor real de conversão [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] classe da implementação particular. Por exemplo, implementam todos os editores padrão `IVsPersistFileFormat`, que herda de <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>.</xref:Microsoft.VisualStudio.OLE.Interop.IPersist> Portanto, você pode chamar `QueryInterface` para <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, e se a ID de classe no objeto de dados existente do documento corresponde a implementação de ID de classe, em seguida, você pode trabalhar com o objeto de dados do documento.</xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>  
  
## <a name="robust-programming"></a>Programação robusta  
 Quando o Visual Studio chama a implementação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>método, ele passa novamente um ponteiro para o objeto de dados de documento existente no `punkDocDataExisting` parâmetro, se houver.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Examinar o objeto de dados de documento retornado no `punkDocDataExisting` para determinar se o objeto de dados de documento é apropriado para o editor, conforme descrito na observação na etapa 4 do procedimento neste tópico. Se for apropriado, a fábrica do editor deve fornecer um segundo modo de exibição para os dados conforme descrito em [suporte a várias exibições de documento](../extensibility/supporting-multiple-document-views.md). Caso contrário, em seguida, ela deve exibir uma mensagem de erro apropriada.  
  
## <a name="see-also"></a>Consulte também  
 [Suporte a vários modos de exibição de documento](../extensibility/supporting-multiple-document-views.md)   
 [Dados de documentos e visualização de documentos em editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md)
