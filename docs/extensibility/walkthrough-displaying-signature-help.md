---
title: 'Passo a passo: Exibindo a Ajuda de assinatura | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 28
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
ms.openlocfilehash: e936c1e0b857349468b47884f58268edfd160025
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-displaying-signature-help"></a>Passo a passo: Exibindo a Ajuda de assinatura
Ajuda da assinatura (também conhecido como *informações de parâmetro*) exibe a assinatura de um método em uma dica de ferramenta quando um usuário digita o caractere de início da lista de parâmetro (normalmente um parêntese de abertura). Como um parâmetro e o separador de parâmetro (geralmente uma vírgula) são digitados, a dica de ferramenta é atualizada para mostrar o próximo parâmetro em negrito. Você pode definir a assinatura ajuda no contexto de um serviço de linguagem, você pode definir seu próprio tipo de conteúdo e extensão de nome do arquivo e exibir a Ajuda de assinatura apenas desse tipo ou você pode exibir a Ajuda de assinatura para um tipo de conteúdo existente (por exemplo, "text"). Este passo a passo mostra como exibir a Ajuda de assinatura para o tipo de conteúdo "text".  
  
 Ajuda da assinatura costuma ser disparada, digitando um caractere específico, por exemplo, "(" (parêntese de abertura) e será descartada digitando outro caractere, por exemplo, ")" (parêntese de fechamento). Recursos do IntelliSense que são disparados, digitando um caractere podem ser implementados usando um manipulador de comandos para os pressionamentos de teclas (o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface) e um provedor do manipulador que implementa o <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>interface.</xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Para criar a fonte de ajuda de assinatura, que é a lista de assinaturas que participam de ajuda de assinatura, implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>interface e um provedor de origem que implementa o <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>interface.</xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> </xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> Os provedores são componentes do Managed Extensibility Framework (MEF) e é responsáveis pelas classes de origem e o controlador de exportação e importação de serviços e agentes, por exemplo, o <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, que permite que você navegue no buffer de texto, e o <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, que dispara a sessão de ajuda de assinatura.</xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> </xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>  
  
 Este passo a passo mostra como implementar a Ajuda de assinatura para um conjunto de identificadores embutidos. Em implementações completas, a linguagem é responsável por fornecer esse conteúdo.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Criando um projeto MEF  
  
#### <a name="to-create-a-mef-project"></a>Para criar um projeto MEF  
  
1.  Crie um projeto c# VSIX. (No **novo projeto** caixa de diálogo, selecione **Visual c# / extensibilidade**, em seguida, **projeto VSIX**.) Nomeie a solução `SignatureHelpTest`.  
  
2.  Adicione um modelo de item Editor classificador ao projeto. Para obter mais informações, consulte [criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Exclua os arquivos de classe existentes.  
  
4.  Adicione as seguintes referências ao projeto e certifique-se de **CopyLocal** é definido como `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>Implementando a assinatura ajuda parâmetros e assinaturas  
 A fonte de ajuda de assinatura se baseia em assinaturas de implementam <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, cada um deles contém parâmetros que implementam <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.</xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> </xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> Em uma implementação completa, essas informações seriam obtidas com a documentação da linguagem, mas neste exemplo, as assinaturas são embutidos.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Para implementar os parâmetros e assinaturas de ajuda de assinatura  
  
1.  Adicione um arquivo de classe e nomeie-o `SignatureHelpSource`.  
  
2.  Adicione as seguintes importações.  
  
     [!code-vb[&#1; VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest n º&1;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]  
  
3.  Adicione uma classe chamada `TestParameter` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.</xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>  
  
     [!code-vb[N º&2; VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest n º&2;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]  
  
4.  Adicione um construtor que define todas as propriedades.  
  
     [!code-vb[N º&3; VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest n º&3;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]  
  
5.  Adicione as propriedades de <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.</xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>  
  
     [!code-vb[N º&4; VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest n º&4;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]  
  
6.  Adicione uma classe chamada `TestSignature` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>  
  
     [!code-vb[N º&5; VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest n º&5;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]  
  
7.  Adicione alguns campos particulares.  
  
     [!code-vb[N º&6; VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest n º&6;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]  
  
8.  Adicione um construtor que define os campos e assina o <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>evento.</xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>  
  
     [!code-vb[#7 VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest&#7;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]  
  
9. Declarar uma `CurrentParameterChanged` eventos. Esse evento é gerado quando o usuário preenche um dos parâmetros na assinatura.  
  
     [!code-vb[N º&8; VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
   [!code-cs[VSSDKSignatureHelpTest n º&8;  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]  
  
10. Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A>propriedade para que ele gera o `CurrentParameterChanged` eventos quando o valor da propriedade é alterado.</xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A>  
  
     [!code-vb[N º&9; VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest n º&9;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]  
  
11. Adicione um método que gera o `CurrentParameterChanged` evento.  
  
     [!code-vb[N º&10; VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest n º&10;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]  
  
12. Adicione um método que computa o parâmetro atual, comparando o número de vírgulas no <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>para o número de vírgulas na assinatura.</xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>  
  
     [!code-vb[N º&11; VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest n º&11;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]  
  
13. Adicionar um manipulador de eventos para o <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>eventos que chama o `ComputeCurrentParameter()` método.</xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>  
  
     [!code-vb[#12 VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest&#12;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]  
  
14. Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>propriedade.</xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> Esta propriedade contém um <xref:Microsoft.VisualStudio.Text.ITrackingSpan>que corresponde ao intervalo de texto no buffer ao qual se aplica a assinatura.</xref:Microsoft.VisualStudio.Text.ITrackingSpan>  
  
     [!code-vb[VSSDKSignatureHelpTest&13;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest&13;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]  
  
15. Implemente os outros parâmetros.  
  
     [!code-vb[#14 VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest&#14;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]  
  
## <a name="implementing-the-signature-help-source"></a>Implementando a origem de ajuda de assinatura  
 A fonte de ajuda de assinatura é o conjunto de assinaturas para que você forneça informações.  
  
#### <a name="to-implement-the-signature-help-source"></a>Para implementar a fonte de ajuda de assinatura  
  
1.  Adicione uma classe chamada `TestSignatureHelpSource` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
     [!code-vb[#15 VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest&15;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]  
  
2.  Adicione uma referência ao buffer de texto.  
  
     [!code-vb[N º&16; VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest&16;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]  
  
3.  Adicione um construtor que define o buffer de texto e o provedor de origem ajuda de assinatura.  
  
     [!code-vb[17 VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest&17;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]  
  
4.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>método.</xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> Neste exemplo, as assinaturas são embutidos, mas uma implementação completa, você obteria essas informações na documentação do idioma.  
  
     [!code-vb[VSSDKSignatureHelpTest&18;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest n º&18;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]  
  
5.  O método auxiliar `CreateSignature()` é fornecido apenas para ilustração.  
  
     [!code-vb[19 VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest&19;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]  
  
6.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>método.</xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> Neste exemplo, há apenas duas assinaturas, cada um deles tem dois parâmetros. Portanto, esse método não é necessário. Em uma implementação mais completa, em que mais de uma fonte de ajuda de assinatura está disponível, esse método é usado para decidir se a fonte de ajuda de assinatura de prioridade mais alta pode fornecer uma assinatura correspondente. Se não for, o método retornará null e a origem do próximo maior prioridade é solicitada a fornecer uma correspondência.  
  
     [!code-vb[20 VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest&20;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]  
  
7.  Implemente o método Dispose ():  
  
     [!code-vb[#21 VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest&#21;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>Implementando o provedor de fonte de ajuda de assinatura  
 O provedor de origem ajuda de assinatura é responsável por exportar a parte do componente Managed Extensibility Framework (MEF) e criando a fonte de ajuda de assinatura.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>Para implementar o provedor de origem ajuda de assinatura  
  
1.  Adicione uma classe chamada `TestSignatureHelpSourceProvider` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>e exportá-lo com um <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>de "texto" e um <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>de antes = "padrão".</xref:Microsoft.VisualStudio.Utilities.OrderAttribute> </xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.NameAttribute> </xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
     [!code-vb[#22 VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest&#22;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]  
  
2.  Implementar <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A>instanciando a `TestSignatureHelpSource`.</xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A>  
  
     [!code-vb[#23 VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest&#23;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]  
  
## <a name="implementing-the-command-handler"></a>Implementar o manipulador de comandos  
 Ajuda da assinatura é normalmente disparada por um (caractere e ignorado por uma) caracteres. Você pode manipular esses pressionamentos de tecla, Implementando um <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>para que ele dispara uma sessão de ajuda de assinatura quando ele recebe um (caractere precedido de um nome de método e descarta a sessão quando ele recebe um) caracteres.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
#### <a name="to-implement-the-command-handler"></a>Para implementar o manipulador de comandos  
  
1.  Adicione uma classe chamada `TestSignatureHelpCommand` que implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
     [!code-vb[VSSDKSignatureHelpTest&#24;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest&#24;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]  
  
2.  Adicionar campos privados para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>adaptador (que permite que você adicione o manipulador de comandos para os manipuladores de cadeia de comando), a exibição de texto, o agente de ajuda de assinatura e a sessão, um <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>e o próximo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> </xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>  
  
     [!code-vb[#25 VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest&#25;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]  
  
3.  Adicione um construtor para inicializar esses campos e adicionar o filtro de comando com os filtros de cadeia de comando.  
  
     [!code-vb[#26 VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest&#26;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]  
  
4.  Implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>método para acionar a sessão de ajuda de assinatura quando o filtro de comando recebe um (caractere depois que um dos nomes de método e para ignorar a sessão quando ele recebe um) caracteres enquanto a sessão ainda estiver ativa.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Em cada caso, o comando é encaminhado.  
  
     [!code-vb[#27 VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest&#27;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]  
  
5.  Implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>método para que ele sempre encaminhe o comando.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
     [!code-vb[#28 VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest&#28;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>Implementando o provedor de comando de ajuda de assinatura  
 Você pode fornecer o comando de ajuda de assinatura Implementando o <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>para instanciar o manipulador de comando quando o modo de texto é criado.</xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>Para implementar o provedor de comando Ajuda de assinatura  
  
1.  Adicione uma classe chamada `TestSignatureHelpController` que implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>e exportá-lo com o <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>e <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.</xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> </xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.NameAttribute> </xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>  
  
     [!code-vb[29 VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest&29;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]  
  
2.  Importar o <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>(usado para obter o <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, determinado o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>objeto), o <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>(usado para localizar a palavra atual) e o <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>(para disparar a sessão de ajuda de assinatura).</xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> </xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>  
  
     [!code-vb[VSSDKSignatureHelpTest&30;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest&30;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]  
  
3.  Implementar o <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A>método instanciando a `TestSignatureCommandHandler`.</xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A>  
  
     [!code-vb[#31 VSSDKSignatureHelpTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb) ] 
     [!code-cs [VSSDKSignatureHelpTest&#31;](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]  
  
## <a name="building-and-testing-the-code"></a>Compilar e testar o código  
 Para testar esse código, crie a solução SignatureHelpTest e executá-lo na instância experimental.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Para compilar e testar a solução SignatureHelpTest  
  
1.  Compile a solução.  
  
2.  Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
3.  Crie um arquivo de texto e digite um texto que inclui a palavra "Adicionar" mais um parêntese de abertura.  
  
4.  Depois de digitar o parêntese de abertura, você deve ver uma dica de ferramenta que exibe uma lista das duas assinaturas para o `add()` método.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Vinculação de um tipo de conteúdo para uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
