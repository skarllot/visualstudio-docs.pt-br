---
title: Criando o Editor principal usando a API herdada | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 29
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
ms.openlocfilehash: e18118d73d46aeee7612eb7dff64f778726778f0
ms.lasthandoff: 02/22/2017

---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Criando o Editor principal usando a API herdada
O editor é responsável por funções, como inserção, exclusão, copiar e colar de edição de texto. Ele combina essas funções com as fornecidas pelos serviços de linguagem, como cores de texto, recuo e conclusão de instrução do IntelliSense.  
  
 Você pode criar uma instância do editor de núcleo de uma das três maneiras:  
  
-   Crie explicitamente uma instância do núcleo do editor em uma janela.  
  
-   Forneça uma fábrica de editor que retorna uma instância do editor de núcleo  
  
-   Abra um arquivo de hierarquia do projeto.  
  
 As seções a seguir discutem como usar a API herdada para instanciar o editor.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Abrir explicitamente uma instância do Editor de núcleo  
 Ao obter explicitamente uma instância do editor principal:  
  
-   Obter um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>para manter o objeto de dados do documento que está sendo editado.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>  
  
-   Criar uma representação de linha orientado a dados do objeto document, criando um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>interface do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>  
  
-   Definir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>como o objeto de dados de documento para uma instância da implementação padrão do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>da interface, usando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A>método.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>  
  
     Host de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>instância em um <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>interface usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>  
  
 Neste ponto, exibindo o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>interface fornece uma janela que contém uma instância do editor de core.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>  
  
 No entanto, isso não é uma instância muito útil, porque não têm teclas de atalho ou acesso a recursos avançados. Para obter acesso a recursos avançados e teclas de atalho:  
  
-   Use o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>método para associar um serviço de linguagem e o objeto de dados de documento que usa o editor.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>  
  
-   Crie suas próprias teclas de atalho, ou use o padrão do sistema, definindo o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>objetos exibem propriedades.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Para fazer isso, chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A>método com o <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>propriedade.</xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A>  
  
     Para obter e usar teclas de atalho não padrão, gerá-los usando o arquivo. VSCT. Para obter mais informações, consulte [tabela de comando do Visual Studio (. Arquivos VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Como usar uma fábrica de Editor para obter o Editor de núcleo  
 Ao implementar um editor de núcleo com uma fábrica de editor usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>método, execute todas as etapas descritas na seção anterior para hospedar explicitamente um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>usando um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>objeto de dados de documento, em um <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>objeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
 Para exibir o texto, obter um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>interface do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>objeto e chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>  
  
 Para fornecer um serviço de linguagem para o editor, chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>método dentro de <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>  
  
 Para obter padrão teclas de atalho, diferentemente da seção anterior, você use o contexto do comando retornado pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>método ao obter o editor de núcleo do <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
 Se o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>método retorna o mesmo comando GUID como o editor de texto, a instância do editor de núcleo obtém automaticamente o padrão teclas de atalho.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
 Para obter informações gerais, consulte [passo a passo: criar um Editor de núcleo e registrar um tipo de arquivo do Editor de](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Consulte também  
 [Dentro do Editor de núcleo](../extensibility/inside-the-core-editor.md)   
 [Abrindo e salvando itens de projeto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Passo a passo: Criar um Editor de núcleo e registrar um tipo de arquivo do Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)
