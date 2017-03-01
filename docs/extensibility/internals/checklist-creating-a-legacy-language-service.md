---
title: "Lista de verificação: Criar um serviço de linguagem herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: 9
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
ms.openlocfilehash: eae51c15223f899151849c43d5a846da33342183
ms.lasthandoff: 02/22/2017

---
# <a name="checklist-creating-a-legacy-language-service"></a>Lista de verificação: Criar um serviço de linguagem herdado
A lista de verificação a seguir resume as etapas básicas que você deve seguir para criar um serviço de linguagem para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor básicos. Integre seu serviço de linguagem em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], você deve criar um avaliador de expressão de depuração. Para obter mais informações, consulte [escrevendo um avaliador de expressão de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) no [extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="steps-for-creating-a-language-service"></a>Etapas para criar um serviço de linguagem  
  
1.  Implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>  
  
    -   O VSPackage, implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>interface para fornecer o serviço de linguagem.</xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>  
  
    -   Disponibilizar seu serviço de linguagem para o ambiente de desenvolvimento integrado (IDE) do seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>implementação.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>  
  
2.  Implementar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>interface na classe de serviço idioma principal.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
     O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>interface é o ponto de partida da interação entre o editor de núcleo e o serviço de linguagem.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
### <a name="optional-features"></a>Recursos opcionais  
 Os recursos a seguir são opcionais e podem ser implementados em qualquer ordem. Esses recursos aumentam a funcionalidade do seu serviço de linguagem.  
  
-   Coloração de sintaxe  
  
     Implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> A implementação dessa interface deve as informações do analisador para retornar as informações de cor apropriado.  
  
     O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>método retorna o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Uma instância de colorizador separado é criada para cada buffer de texto, portanto você deve implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>interface separadamente.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Para obter mais informações, consulte [coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
-   Janela de código  
  
     Implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>interface para habilitar o serviço de linguagem receber notificação quando uma nova janela de código é criada.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>  
  
     O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>método retorna o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> O serviço de linguagem pode então adicionar a interface do usuário especial na janela de código do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> O serviço de linguagem também pode fazer qualquer processamento especial, como adicionar um filtro de exibição de texto no <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>  
  
-   Filtro de exibição de texto  
  
     Para fornecer IntelliSense conclusão de instrução em um serviço de linguagem, você deve interceptar alguns dos comandos que trataria a exibição de texto. Para interceptar esses comandos, conclua as seguintes etapas:  
  
    -   Implementar <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>participar os comandos de editor de cadeia e identificador de comando.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
    -   Chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>método e passar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>implementação.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>  
  
    -   Chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A>método ao desanexar do modo de exibição para que esses comandos não são passados para você.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A>  
  
     Comandos que devem ser tratados dependem os serviços que são fornecidos. Para obter mais informações, consulte [comandos importantes para filtros de serviço de linguagem](../../extensibility/internals/important-commands-for-language-service-filters.md).  
  
    > [!NOTE]
    >  O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>interface deve ser implementada no mesmo objeto, como o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>  
  
-   Conclusão da instrução  
  
     Implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>  
  
     Suporte para o comando de conclusão de instrução (ou seja, <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>) e chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>método o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>interface, passando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> </xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Para obter mais informações, consulte [conclusão de instrução em um serviço de linguagem herdado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).  
  
-   Dicas de método  
  
     Implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>interface para fornecer dados para a janela de dica de método.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>  
  
     Instale o filtro de exibição de texto para manipular comandos apropriadamente, para que você saiba quando mostrar uma janela de dica de dados do método. Para obter mais informações, consulte [informações de parâmetro em um serviço de linguagem herdado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).  
  
-   Marcadores de erro  
  
     Implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
  
     Criar o erro objetos de marcador que implementam o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>interface e chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>método, passando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>interface do objeto marcador error.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
  
     Normalmente, cada marcador de erro gerencia um item na janela lista de tarefas.  
  
-   Itens de lista de tarefas  
  
     Implementar uma classe de item de tarefa fornecendo o <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem>  
  
     Implementar uma classe de provedor de tarefa fornecendo o <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider>interface e o <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider>  
  
     Implementar uma classe de enumerador de tarefa fornecendo o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems>  
  
     Registrar o provedor de tarefa com a lista de tarefas <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A>  
  
     Obter a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>interface chamando o provedor do serviço de linguagem com o serviço GUID <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>.</xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> </xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>  
  
     Criar objetos de item de tarefa e chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A>método o <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>interface quando há novos ou tarefas atualizadas.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> </xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A>  
  
-   Itens de tarefas de comentário  
  
     Use o <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>interface e o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens>interface para obter o comentário tokens de tarefa.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> </xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>  
  
     Obter um <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>interface do <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>service.</xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> </xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>  
  
     Obter o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens>da interface do <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens>  
  
     Implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents>interface alterações na lista de token.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents>  
  
-   Estrutura de tópicos  
  
     Há várias opções para oferecer suporte a estrutura de tópicos. Por exemplo, você pode oferecer suporte a **recolher para definições de** de comando, forneçam controlada pelo editor de regiões ou regiões controlado pelo cliente. Para obter mais informações, consulte [como: fornecer expandido de estrutura de tópicos suporte em um serviço de linguagem herdado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).  
  
-   Registro de serviço de linguagem  
  
     Para obter mais informações sobre como registrar um serviço de linguagem, consulte [registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service2.md) e [Gerenciando VSPackages](../../extensibility/managing-vspackages.md).  
  
-   Ajuda contextual  
  
     Fornece contexto para o editor de uma das seguintes maneiras:  
  
    -   Fornecer contexto para os marcadores de texto Implementando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
  
 Fornecer todo o contexto de usuário ao implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolvendo um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Escrevendo um avaliador de expressão de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
