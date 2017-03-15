---
title: Criar Designers e editores personalizados | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
caps.latest.revision: 31
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
ms.openlocfilehash: 3475a1ef760ae5eda0e14e8d1957c7f918635af8
ms.lasthandoff: 02/22/2017

---
# <a name="creating-custom-editors-and-designers"></a>Criar Designers e editores personalizados
O ambiente de desenvolvimento integrado (IDE) do Visual Studio pode hospedar diferentes tipos de editor:  
  
-   Editor de núcleo do Visual Studio  
  
-   Editores personalizados  
  
-   Editores externos  
  
-   Designers  
  
 As informações a seguir o ajudará a escolher o tipo de editor que é necessário.  
  
## <a name="types-of-editor"></a>Tipos de Editor  
 Para obter informações sobre o editor do Visual Studio core, consulte [estendendo o Editor e serviços de linguagem](../extensibility/extending-the-editor-and-language-services.md).  
  
##### <a name="custom-editors"></a>Editores personalizados  
 Um editor personalizado é aquele que foi projetado para funcionar em casos especializados. Por exemplo, você pode criar um editor cuja função é ler e gravar dados em um repositório específico, como um servidor do Microsoft Exchange. Escolha um editor personalizado se você quiser um editor que funciona com o tipo de projeto ou se você quiser que um editor que tem apenas alguns comandos específicos. No entanto, observe que os usuários não poderão usar um editor personalizado para editar padrão [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projetos.  
  
 Um editor personalizado pode usar uma fábrica de editor e adicionar informações sobre o editor do registro. No entanto, o tipo de projeto associado com o editor personalizado pode instanciar o editor personalizado de outras maneiras.  
  
 Um editor personalizado pode usar a ativação no local ou inserindo simplificado para implementar uma exibição.  
  
##### <a name="external-editors"></a>Editores externos  
 Editores externos são editores que não estão integradas ao Visual Studio, como Microsoft Word, o bloco de notas ou o Microsoft FrontPage. Você pode chamar tal um editor se, por exemplo, você está passando o texto a ele do VSPackage. Editores externos se registrem e podem ser usados fora do Visual Studio. Quando você chamar um editor externo, e pode ser incorporado em uma janela do host, ele aparece em uma janela no IDE. Caso contrário, o IDE cria uma janela separada para ele.  
  
 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>método define a prioridade do documento usando o <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>enumeração.</xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> </xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Se o `DP_External` valor for especificado, o arquivo pode ser aberto por um editor externo.  
  
## <a name="editor-design-decisions"></a>Decisões de Design do Editor  
 As questões de design a seguir ajudarão você a escolher o tipo de editor melhor adequado para seu aplicativo:  
  
-   Seu aplicativo salvará os dados nos arquivos ou não? Se ele salvará os dados em arquivos, estarão em um formato padrão ou personalizado?  
  
     Se você usar um formato de arquivo padrão, outros tipos de projeto, além de seu projeto será capazes de abrir e ler/gravar dados neles. Se você usar um formato de arquivo personalizado, no entanto, o tipo de projeto será capaz de abrir e ler/gravar dados neles.  
  
     Se seu projeto usa arquivos, você deve personalizar o editor padrão. Se seu projeto não usa arquivos, mas em vez disso, usa itens em um banco de dados ou outro repositório, você deve criar um editor personalizado.  
  
-   O editor precisa hospedar controles ActiveX?  
  
     Se o editor de hospedar controles ActiveX, em seguida, implementar um editor de ativação no local, conforme descrito em [da ativação In loco](../misc/in-place-activation.md). Se não hospeda controles ActiveX, em seguida, use um editor de inserção simplificado, ou personalizar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor padrão.  
  
-   O editor oferecerá suporte a vários modos de exibição? Se desejar que os modos de exibição do editor seja visível ao mesmo tempo como o editor padrão, você deve suportar vários modos de exibição.  
  
     Se o editor precisa oferecer suporte a vários modos de exibição, os dados de documentos e objetos de exibição de documento para o editor devem ser objetos separados. Para obter mais informações, consulte [suporte a várias exibições de documento](../extensibility/supporting-multiple-document-views.md).  
  
     Se o editor dá suporte a vários modos de exibição, você planeja usar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] principais de implementação do buffer do editor de texto (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto) para o objeto de dados de documentos?</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Isto é, você deseja oferecer suporte a seu editor exibição-lado a lado com o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principal? A capacidade de fazer isso é a base do designer de formulários...  
  
-   Se você precisar hospedar um editor externo, pode editor ser incorporado dentro de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?  
  
     Se ele pode ser incorporado, você deve criar uma janela de host para o editor externo e, em seguida, chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>método e defina o <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>valor de enumeração para `DP_External`.</xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> </xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Se o editor não pode ser inserido, o IDE criará automaticamente uma janela separada para ele.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Passo a passo: Criando um Editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md)  
 Explica como criar um editor personalizado.  
  
 [Passo a passo: Adicionando recursos a um Editor personalizado](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 Explica como adicionar recursos a um editor personalizado.  
  
 [Inicialização de Designer e a configuração de metadados](../extensibility/designer-initialization-and-metadata-configuration.md)  
 Explica como inicializar um designer.  
  
 [Fornecendo suporte à função desfazer para Designers](../extensibility/supplying-undo-support-to-designers.md)  
 Explica como fornecer suporte à função desfazer para designers.  
  
 [Cores de sintaxe no editores personalizados](../extensibility/syntax-coloring-in-custom-editors.md)  
 Explica a diferença entre cores no editor de núcleo e nos editores personalizados de sintaxe.  
  
 [Dados de documentos e visualização de documentos em editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 Explica como implementar dados de documentos e exibições de documento em editores personalizados.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Interfaces herdadas no Editor](../extensibility/legacy-interfaces-in-the-editor.md)  
 Explica como acessar o editor principal por meio da API herdada.  
  
 [Desenvolvendo um serviço de linguagem herdado](../extensibility/internals/developing-a-legacy-language-service.md)  
 Explica como implementar um serviço de linguagem.  
  
 [Estendendo a outras partes do Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica como criar elementos de interface do usuário que correspondem ao restante da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory></xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
