---
title: "Fábricas de editor | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
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
ms.openlocfilehash: 8cb47fe9bb6177b2d904739e86ad52e340582e9c
ms.lasthandoff: 02/22/2017

---
# <a name="editor-factories"></a>Fábricas de editor
Uma fábrica de editor cria objetos do editor e os coloca em um quadro de janela, conhecido como uma exibição física. Ele cria os dados de documentos e objetos de exibição de documento que são necessários para criar editores e designers. Uma fábrica de editor é necessário para criar o editor do Visual Studio core e qualquer editor padrão. Um editor personalizado também pode ser criado com uma fábrica de editor.  
  
 Criar uma fábrica de editor Implementando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> O exemplo a seguir ilustra como implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>para criar uma fábrica de editor:</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>  
  
 [!code-vb[&#1; VSSDKEditorFactories](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb) ] 
 [!code-cs [VSSDKEditorFactories n º&1;](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 Um editor é carregado na primeira vez que você abre um tipo de arquivo tratado pelo editor. Você pode optar por abrir um editor específico ou o editor padrão. Se você selecionar o editor padrão, o ambiente de desenvolvimento integrado (IDE) determina o editor correto para abrir e abre. Para obter mais informações, consulte [determinar qual Editor abre um arquivo em um projeto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="registering-editor-factories"></a>Fábricas de Editor do registro  
 Antes de usar um editor que você criou, primeiro você deve registrar informações sobre ele, incluindo as extensões de arquivo pode manipular.  
  
 Se o VSPackage é escrito em código gerenciado, você pode usar o método de estrutura de pacote gerenciado (MPF) <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>para registrar a fábrica do editor após o VSPackage é carregado.</xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> Se o VSPackage é escrito em código não gerenciado, você deve registrar sua fábrica de editor usando o <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors>service.</xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors>  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>Registrar uma fábrica de Editor usando código gerenciado  
 Você deve registrar sua fábrica de editor em seu VSPackage o `Initialize` método. Primeiro chamar `base.Initialize`e, em seguida, a chamada <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>para cada fábrica de editor</xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>  
  
 No código gerenciado, não é necessário para cancelar o registro de uma fábrica de editor, pois o VSPackage cuidará disso para você. Além disso, se sua fábrica de editor implementar <xref:System.IDisposable>, ele é automaticamente descartado quando é cancelado.</xref:System.IDisposable>  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>Registrando uma fábrica de editor usando código não gerenciado  
 No <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>implementação para o pacote de editor, use o `QueryService` método para chamar `SVsRegisterEditors`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Isso retorna um ponteiro para <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors> Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>método passando a implementação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> </xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> Você deve mplement <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>em uma classe separada</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>  
  
## <a name="the-editor-factory-registration-process"></a>O processo de registro de fábrica do Editor  
 O seguinte processo ocorre quando o Visual Studio carregará seu editor usando sua fábrica de editor:  
  
1.  O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> de chamadas do sistema de projeto  
  
2.  Esse método retorna a fábrica do editor. Carregar o pacote do editor, no entanto, até que um sistema de projeto precisa realmente o editor visual atrasos de Studio.  
  
3.  Quando um sistema de projeto requer o editor, o Visual Studio chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, um método especializado que retorna o modo de exibição de documento e o documento de objetos de dados.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
4.  Se chama pelo Visual Studio para a fábrica de editor usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>retornar um objeto de dados de documentos e um objeto de exibição de documento, o Visual Studio, em seguida, cria a janela de documento, coloca o objeto de exibição de documento nele e cria uma entrada na tabela de documento (RDT) em execução para o objeto de dados do documento.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory></xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Tabela de documento em execução](../extensibility/internals/running-document-table.md)
