---
title: "Passo a passo: Exibindo a conclusão de instrução | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 36
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
ms.openlocfilehash: 66353615fcad0f2f29c26e519512ff19bd27f209
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-displaying-statement-completion"></a>Passo a passo: Exibindo a conclusão de instrução
Você pode implementar a conclusão de instrução com base em linguagem definindo os identificadores para o qual você deseja fornecer a conclusão e, em seguida, acionar uma sessão de conclusão. Você pode definir a conclusão da instrução no contexto de um serviço de linguagem, definir sua própria extensão de nome de arquivo e o tipo de conteúdo e exibir conclusão apenas desse tipo de, ou você pode acionar a conclusão de um tipo de conteúdo existente — por exemplo, "texto sem formatação". Este passo a passo mostra como disparar a conclusão de instrução para o tipo de conteúdo "texto sem formatação", que é o tipo de conteúdo de arquivos de texto. O tipo de conteúdo "text" é o ancestral de todos os outros tipos de conteúdo, incluindo o código e arquivos XML.  
  
 Conclusão de instrução costuma ser disparado digitando determinados caracteres — por exemplo, digitando o início de um identificador, como "using". Normalmente é descartado, pressionando a tecla barra de espaço, Tab ou Enter para confirmar uma seleção. Você pode implementar os recursos do IntelliSense que são disparados, digitando um caractere usando um manipulador de comandos para os pressionamentos de teclas (o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface) e um provedor do manipulador que implementa o <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>interface.</xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Para criar a fonte de conclusão, que é a lista de identificadores que participam de conclusão, implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>interface e um provedor de origem de conclusão (o <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>interface).</xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> </xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> Os provedores são componentes do Managed Extensibility Framework (MEF). Eles são responsáveis pelas classes de origem e o controlador de exportação e importação de serviços e os agentes — por exemplo, o <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, que permite a navegação no buffer de texto e o <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, que dispara a sessão de conclusão.</xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> </xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>  
  
 Este passo a passo mostra como implementar a conclusão de instrução para um conjunto de identificadores embutidos. Em implementações completas, o serviço de linguagem e a documentação da linguagem serão responsáveis por fornecer esse conteúdo.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Criando um projeto MEF  
  
#### <a name="to-create-a-mef-project"></a>Para criar um projeto MEF  
  
1.  Crie um projeto c# VSIX. (No **novo projeto** caixa de diálogo, selecione **Visual c# / extensibilidade**, em seguida, **projeto VSIX**.) Nomeie a solução `CompletionTest`.  
  
2.  Adicione um modelo de item Editor classificador ao projeto. Para obter mais informações, consulte [criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Exclua os arquivos de classe existentes.  
  
4.  Adicione as seguintes referências ao projeto e certifique-se de que **CopyLocal** é definido como `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-the-completion-source"></a>Implementando a origem de conclusão  
 A fonte de conclusão é responsável por coletar o conjunto de identificadores e adicionando o conteúdo para a janela de conclusão quando um usuário digita um gatilho de conclusão, como as primeiras letras de um identificador. Neste exemplo, os identificadores e suas descrições são embutidos no código de <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A>método.</xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> A maioria dos usos do mundo real, você usaria o analisador da linguagem para obtenção de tokens para preencher a lista de conclusão.  
  
#### <a name="to-implement-the-completion-source"></a>Para implementar a origem de conclusão  
  
1.  Adicione um arquivo de classe e nomeie-o `TestCompletionSource`.  
  
2.  Adicione essas importações:  
  
     [!code-cs[&#1; VSSDKCompletionTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs) ] 
     [!code-vb [VSSDKCompletionTest n º&1;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  Modifique a declaração de classe de `TestCompletionSource` para que ele implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:</xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
     [!code-cs[N º&2; VSSDKCompletionTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs) ] 
     [!code-vb [VSSDKCompletionTest n º&2;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  Adicionar campos privados para o provedor de origem, o buffer de texto e uma lista de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion>objetos (que correspondem aos identificadores que participarão da sessão de conclusão):</xref:Microsoft.VisualStudio.Language.Intellisense.Completion>  
  
     [!code-cs[N º&3; VSSDKCompletionTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs) ] 
     [!code-vb [VSSDKCompletionTest n º&3;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  Adicione um construtor que define o buffer e o provedor de origem. O `TestCompletionSourceProvider` classe é definida em etapas posteriores:  
  
     [!code-cs[N º&4; VSSDKCompletionTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs) ] 
     [!code-vb [VSSDKCompletionTest n º&4;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A>método adicionando um conjunto de conclusão que contém as conclusões que você deseja fornecer o contexto.</xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> Cada conjunto de conclusão contém um conjunto de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion>conclusões e corresponde a uma guia da janela de conclusão.</xref:Microsoft.VisualStudio.Language.Intellisense.Completion> (Em projetos do Visual Basic, as guias da janela de conclusão são nomeadas **comuns** e **todas as**.) O método FindTokenSpanAtPosition é definido na próxima etapa.  
  
     [!code-cs[N º&5; VSSDKCompletionTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs) ] 
     [!code-vb [VSSDKCompletionTest n º&5;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  O método a seguir é usado para localizar a palavra atual da posição do cursor:  
  
     [!code-cs[N º&6; VSSDKCompletionTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs) ] 
     [!code-vb [VSSDKCompletionTest n º&6;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  Implementar o `Dispose()` método:  
  
     [!code-cs[#7 VSSDKCompletionTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs) ] 
     [!code-vb [VSSDKCompletionTest&#7;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## <a name="implementing-the-completion-source-provider"></a>Implementando o provedor de origem de conclusão  
 O provedor de origem de conclusão é a parte do componente MEF que instancia a origem de conclusão.  
  
#### <a name="to-implement-the-completion-source-provider"></a>Para implementar o provedor de origem de conclusão  
  
1.  Adicione uma classe chamada `TestCompletionSourceProvider` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>.</xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> Exportar esta classe com um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>de "texto sem formatação" e um <xref:Microsoft.VisualStudio.Utilities.NameAttribute>de "conclusão de teste".</xref:Microsoft.VisualStudio.Utilities.NameAttribute> </xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
     [!code-cs[N º&8; VSSDKCompletionTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs) ] 
     [!code-vb [VSSDKCompletionTest n º&8;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  Importar um <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, que é usado para localizar a palavra atual na fonte de conclusão.</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>  
  
     [!code-cs[N º&9; VSSDKCompletionTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs) ] 
     [!code-vb [VSSDKCompletionTest n º&9;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A>método para instanciar a origem de conclusão.</xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A>  
  
     [!code-cs[N º&10; VSSDKCompletionTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs) ] 
     [!code-vb [VSSDKCompletionTest n º&10;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>Implementando o provedor de manipulador de comando de conclusão  
 O provedor de manipulador de comando de conclusão é derivado de um <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, que verifica se há um evento de criação de exibição de texto e converte o modo de exibição de um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>— que permite a adição do comando para a cadeia de comando do shell do Visual Studio — a <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> Como essa classe é uma exportação MEF, você também pode usá-la para importar os serviços necessários para o manipulador de comandos.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Para implementar o provedor de manipulador de comando de conclusão  
  
1.  Adicione um arquivo chamado `TestCompletionCommandHandler`.  
  
2.  Adicione essas instruções using:  
  
     [!code-cs[N º&11; VSSDKCompletionTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs) ] 
     [!code-vb [VSSDKCompletionTest n º&11;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  Adicione uma classe chamada `TestCompletionHandlerProvider` que implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>.</xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> Exportar esta classe com um <xref:Microsoft.VisualStudio.Utilities.NameAttribute>"token de conclusão do manipulador de", um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>de "texto sem formatação" e um <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.</xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> </xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> </xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.NameAttribute>  
  
     [!code-cs[#12 VSSDKCompletionTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs) ] 
     [!code-vb [VSSDKCompletionTest&#12;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  Importar o <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, que permite a conversão de um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>para um <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, um <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>e um <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>que permite o acesso a serviços padrão do Visual Studio.</xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> </xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> </xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>  
  
     [!code-cs[VSSDKCompletionTest&13;](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs) ] 
     [!code-vb [VSSDKCompletionTest&13;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  Implementar o <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A>método para instanciar o manipulador de comandos.</xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A>  
  
     [!code-cs[#14 VSSDKCompletionTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs) ] 
     [!code-vb [VSSDKCompletionTest&#14;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## <a name="implementing-the-completion-command-handler"></a>Implementar o manipulador de comandos de conclusão  
 Como conclusão de instrução é disparado por pressionamentos de teclas, você deve implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface para receber e processar os pressionamentos de teclas que disparam, confirmam e ignorar a sessão de conclusão.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
#### <a name="to-implement-the-completion-command-handler"></a>Para implementar o manipulador de comandos de conclusão  
  
1.  Adicione uma classe chamada `TestCompletionCommandHandler` que implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
     [!code-cs[#15 VSSDKCompletionTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs) ] 
     [!code-vb [VSSDKCompletionTest&15;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2.  Adicionar campos privados para o próximo manipulador de comando (para que você passa o comando), a exibição de texto, o provedor do manipulador de comando (que permite o acesso a vários serviços) e uma sessão de conclusão:  
  
     [!code-cs[N º&16; VSSDKCompletionTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs) ] 
     [!code-vb [VSSDKCompletionTest&16;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3.  Adicione um construtor que define a exibição de texto e os campos de provedor e adiciona o comando para a cadeia de comando:  
  
     [!code-cs[17 VSSDKCompletionTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs) ] 
     [!code-vb [VSSDKCompletionTest&17;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4.  Implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>método passando o comando ao longo:</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
     [!code-cs[VSSDKCompletionTest&18;](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs) ] 
     [!code-vb [VSSDKCompletionTest n º&18;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5.  Implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>método.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Quando esse método recebe um pressionamento de tecla, ele deve fazer uma dessas coisas:  
  
    -   Permitir que o caractere a ser gravadas no buffer e então disparar ou conclusão de filtro. (Caracteres imprimíveis fazem isso.)  
  
    -   Confirmar a conclusão, mas não permitem que o caractere a ser gravadas no buffer. (Espaço em branco, Tab e Enter isso quando uma sessão de conclusão é exibida.)  
  
    -   Permitir que o comando a ser passado para o próximo manipulador. (Todos os outros comandos.)  
  
     Como esse método pode exibir a interface do usuário, chamar <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A>para certificar-se de que ele não é chamado em um contexto de automação:</xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A>  
  
     [!code-cs[19 VSSDKCompletionTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest&19;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6.  Esse código é um método particular que dispara a sessão de conclusão:  
  
     [!code-cs[20 VSSDKCompletionTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs) ] 
     [!code-vb [VSSDKCompletionTest&20;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7.  O exemplo a seguir é um método particular que cancela a inscrição do <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed>evento:</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed>  
  
     [!code-cs[#21 VSSDKCompletionTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs) ] 
     [!code-vb [VSSDKCompletionTest&#21;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## <a name="building-and-testing-the-code"></a>Compilar e testar o código  
 Para testar esse código, crie a solução CompletionTest e executá-lo na instância experimental.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Para compilar e testar a solução CompletionTest  
  
1.  Compile a solução.  
  
2.  Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
3.  Crie um arquivo de texto e digite um texto que inclui a palavra "Adicionar".  
  
4.  Conforme você digita primeiro "a" e, em seguida, "d", uma lista que contém "inclusão" e "adaptação" deve ser exibida. Observe que a adição é selecionada. Quando você digita outro "d", a lista deve conter somente "inclusão", que agora é selecionado. Você pode confirmar "inclusão" pressionando a tecla barra de espaço, Tab ou Enter ou descartar a lista digitando Esc ou qualquer outra chave.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Vinculação de um tipo de conteúdo para uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
