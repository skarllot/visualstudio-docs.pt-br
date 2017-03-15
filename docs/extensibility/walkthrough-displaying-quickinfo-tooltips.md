---
title: "Passo a passo: Exibindo dicas de ferramenta Informaçãorápida | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 27
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
ms.openlocfilehash: b533e77a2310194b2bccc225f9902e5a8d502da5
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>Passo a passo: Exibindo Informaçãorápida dicas de ferramenta
Informaçãorápida é um recurso IntelliSense que exibe as assinaturas de método e descrições de quando um usuário move o ponteiro sobre um nome de método. Você pode implementar recursos de linguagem como Informaçãorápida definindo os identificadores para o qual você deseja fornecer descrições de Informaçãorápida e, em seguida, criando uma dica de ferramenta para exibir o conteúdo. Você pode definir Informaçãorápida no contexto de um serviço de linguagem, você pode definir seu próprio tipo de conteúdo e extensão de nome do arquivo e exibir a Informaçãorápida apenas desse tipo ou Informaçãorápida podem ser exibidos para um tipo de conteúdo existente (como "text"). Este passo a passo mostra como exibir Informaçãorápida para o tipo de conteúdo "text".  
  
 O exemplo Informaçãorápida neste passo a passo exibe as dicas de ferramentas quando um usuário move o ponteiro sobre um nome de método. Esse design requer que você implementar esse quatro interfaces:  
  
-   interface de origem  
  
-   interface do provedor de origem  
  
-   interface do controlador  
  
-   interface do provedor de controlador  
  
 Os provedores de origem e o controlador são componentes do Managed Extensibility Framework (MEF) e serão responsáveis pela exportação as classes de origem e o controlador e importação de serviços e os agentes, como o <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, que cria o buffer de texto de dica de ferramenta e o <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, que dispara a sessão Informaçãorápida.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> </xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>  
  
 Neste exemplo, a fonte Informaçãorápida usa uma lista de nomes de método e descrições embutidos, mas em implementações completas, o serviço de linguagem e a documentação da linguagem serão responsáveis por fornecer esse conteúdo.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Criando um projeto MEF  
  
#### <a name="to-create-a-mef-project"></a>Para criar um projeto MEF  
  
1.  Crie um projeto c# VSIX. (No **novo projeto** caixa de diálogo, selecione **Visual c# / extensibilidade**, em seguida, **projeto VSIX**.) Nomeie a solução `QuickInfoTest`.  
  
2.  Adicione um modelo de item Editor classificador ao projeto. Para obter mais informações, consulte [criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Exclua os arquivos de classe existentes.  
  
## <a name="implementing-the-quickinfo-source"></a>Implementando a fonte Informaçãorápida  
 A fonte Informaçãorápida é responsável por coletar o conjunto de identificadores e suas descrições e adicionando o conteúdo para o buffer de texto de dica de ferramenta quando um dos identificadores é encontrado. Neste exemplo, os identificadores e suas descrições são adicionadas apenas no construtor do código-fonte.  
  
#### <a name="to-implement-the-quickinfo-source"></a>Para implementar a fonte Informaçãorápida  
  
1.  Adicione um arquivo de classe e nomeie-o `TestQuickInfoSource`.  
  
2.  Adicione uma referência ao Microsoft.VisualStudio.Language.IntelliSense.  
  
3.  Adicione as seguintes importações.  
  
     [!code-vb[&#1; VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n º&1;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]  
  
4.  Declare uma classe que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>e nomeie-o `TestQuickInfoSource`.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
     [!code-vb[N º&2; VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n º&2;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]  
  
5.  Adicione campos para o provedor de origem Informaçãorápida, o buffer de texto e um conjunto de nomes de método e assinaturas de método. Neste exemplo, os nomes de método e as assinaturas são inicializadas no `TestQuickInfoSource` construtor.  
  
     [!code-vb[N º&3; VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n º&3;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]  
  
6.  Adicione um construtor que define o provedor de origem Informaçãorápida e o buffer de texto e, em seguida, preenche o conjunto de nomes de método e assinaturas de método e descrições.  
  
     [!code-vb[N º&4; VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n º&4;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]  
  
7.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>método.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> Neste exemplo, o método localiza a palavra atual ou a palavra anterior se o cursor estiver no final de uma linha ou um buffer de texto. Se o word é um dos nomes de método, a descrição do nome desse método é adicionada ao conteúdo Informaçãorápida.  
  
     [!code-vb[N º&5; VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n º&5;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]  
  
8.  Você também deve implementar um método Dispose (), desde <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>implementa <xref:System.IDisposable>:</xref:System.IDisposable> </xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
     [!code-vb[N º&6; VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n º&6;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>Implementando um provedor de fonte de Informaçãorápida  
 O provedor da fonte de Informaçãorápida serve principalmente para exportar a mesma como uma parte do componente MEF e instanciar a fonte Informaçãorápida. Porque é uma parte do componente MEF, ele pode importar outras partes do componente MEF.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Para implementar um provedor de origem Informaçãorápida  
  
1.  Declarar um provedor de origem Informaçãorápida chamado `TestQuickInfoSourceProvider` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>e exportá-lo com um <xref:Microsoft.VisualStudio.Utilities.NameAttribute>de "Dica de ferramenta com a fonte Informaçãorápida", um <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>de antes = "padrão" e um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>de "text".</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.OrderAttribute> </xref:Microsoft.VisualStudio.Utilities.NameAttribute> </xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
     [!code-vb[#7 VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#7;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]  
  
2.  Importar dois serviços de editor, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>e <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, como propriedades de `TestQuickInfoSourceProvider`.</xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> </xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>  
  
     [!code-vb[N º&8; VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n º&8;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]  
  
3.  Implementar <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>para retornar um novo `TestQuickInfoSource`.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>  
  
     [!code-vb[N º&9; VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n º&9;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]  
  
## <a name="implementing-a-quickinfo-controller"></a>Implementando um controlador Informaçãorápida  
 Controladores de Informaçãorápida determinam quando Informaçãorápida deve ser exibida. Neste exemplo, Informaçãorápida é exibida quando o ponteiro está sobre uma palavra que corresponde a um dos nomes de método. O controlador Informaçãorápida implementa um manipulador de eventos de foco do mouse que dispara uma sessão Informaçãorápida.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>Para implementar um controlador Informaçãorápida  
  
1.  Declare uma classe que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>e nomeie-o `TestQuickInfoController`.</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>  
  
     [!code-vb[N º&10; VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n º&10;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]  
  
2.  Adicione campos privados para o modo de exibição de texto, os buffers de texto representados na exibição de texto, a sessão Informaçãorápida e o provedor de controlador Informaçãorápida.  
  
     [!code-vb[N º&11; VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n º&11;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]  
  
3.  Adicione um construtor que define os campos e adiciona o manipulador de eventos do mouse em foco.  
  
     [!code-vb[#12 VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#12;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]  
  
4.  Adicione o manipulador de eventos de foco do mouse que dispara a sessão Informaçãorápida.  
  
     [!code-vb[VSSDKQuickInfoTest&13;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&13;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]  
  
5.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>método para que ele remove o manipulador de eventos de foco do mouse quando o controlador é separado da exibição do texto.</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>  
  
     [!code-vb[#14 VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#14;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]  
  
6.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>método e o <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A>método como métodos vazios para este exemplo.</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> </xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>  
  
     [!code-vb[#15 VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&15;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Implementando o provedor Informaçãorápida controlador  
 O provedor do controlador Informaçãorápida serve principalmente para exportar a mesma como uma parte do componente MEF e instanciar o controlador Informaçãorápida. Porque é uma parte do componente MEF, ele pode importar outras partes do componente MEF.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>Para implementar o provedor de controlador Informaçãorápida  
  
1.  Declare uma classe denominada `TestQuickInfoControllerProvider` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>e exportá-lo com um <xref:Microsoft.VisualStudio.Utilities.NameAttribute>de "Dica de ferramenta Informaçãorápida controlador" e um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>de "texto":</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.NameAttribute> </xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>  
  
     [!code-vb[N º&16; VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&16;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]  
  
2.  Importar o <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>como uma propriedade.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>  
  
     [!code-vb[17 VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&17;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]  
  
3.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A>método instanciando o controlador Informaçãorápida.</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A>  
  
     [!code-vb[VSSDKQuickInfoTest&18;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n º&18;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]  
  
## <a name="building-and-testing-the-code"></a>Compilar e testar o código  
 Para testar esse código, crie a solução QuickInfoTest e executá-lo na instância experimental.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>Para compilar e testar a solução QuickInfoTest  
  
1.  Compile a solução.  
  
2.  Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
3.  Crie um arquivo de texto e digite um texto que contém as palavras "Adicionar" e "subtrair".  
  
4.  Mova o ponteiro sobre uma das ocorrências de "Adicionar". A assinatura e a descrição de `add` método deve ser exibido.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Vinculação de um tipo de conteúdo para uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
