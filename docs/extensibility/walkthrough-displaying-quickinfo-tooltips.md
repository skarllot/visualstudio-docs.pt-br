---
title: 'Passo a passo: Exibindo dicas de ferramenta Inforapida | Microsoft Docs'
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
ms.translationtype: MT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 7acb244077949ffb0a59018b24706fd3ccfefc14
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>Passo a passo: Exibindo Inforapida dicas de ferramenta
QuickInfo é um recurso do IntelliSense que exibe as assinaturas de método e descrições de quando um usuário move o ponteiro sobre um nome de método. Você pode implementar recursos de idioma como Inforapida definindo os identificadores para o qual você deseja fornecer Inforapida descrições e, em seguida, criando uma dica de ferramenta para exibir o conteúdo. Você pode definir Inforapida no contexto de um serviço de idioma, você pode definir seu próprio tipo de conteúdo e a extensão de nome do arquivo e exibir Inforapida apenas desse tipo ou Inforapida podem ser exibidos para um tipo de conteúdo existente (como "texto"). Este passo a passo mostra como exibir Inforapida para o tipo de conteúdo "texto".  
  
 O exemplo Inforapida neste passo a passo exibe as dicas de ferramentas quando um usuário move o ponteiro sobre um nome de método. Esse design requer que você implementar essas quatro interfaces:  
  
-   interface de origem  
  
-   interface do provedor de origem  
  
-   interface do controlador  
  
-   interface do provedor de controlador  
  
 Os provedores de origem e o controlador são partes de componente do Managed Extensibility Framework (MEF) e serão responsáveis para exportar as classes de origem e o controlador e importando os serviços e os agentes, como o <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, que cria o texto de dica de ferramenta buffer e o <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, que aciona a sessão Inforapida.  
  
 Neste exemplo, a fonte de Inforapida usa uma lista codificada de nomes de método e descrições, mas em implementações completas, o serviço de linguagem e a documentação de idioma serão responsáveis por fornecer esse conteúdo.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Criando um projeto MEF  
  
#### <a name="to-create-a-mef-project"></a>Para criar um projeto MEF  
  
1.  Crie um projeto c# VSIX. (No **novo projeto** caixa de diálogo, selecione **Visual C# / extensibilidade**, em seguida, **projeto VSIX**.) Nome da solução `QuickInfoTest`.  
  
2.  Adicione um modelo de item de classificação de Editor para o projeto. Para obter mais informações, consulte [criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Exclua os arquivos de classe existente.  
  
## <a name="implementing-the-quickinfo-source"></a>Implementando a fonte Inforapida  
 A fonte Inforapida é responsável por coletar o conjunto de identificadores e suas descrições e adicionar o conteúdo para o buffer de texto de dica de ferramenta quando um dos identificadores é encontrado. Neste exemplo, os identificadores e suas descrições são adicionadas apenas no construtor de origem.  
  
#### <a name="to-implement-the-quickinfo-source"></a>Para implementar o código-fonte Inforapida  
  
1.  Adicione um arquivo de classe e denomine- `TestQuickInfoSource`.  
  
2.  Adicione uma referência a Microsoft.VisualStudio.Language.IntelliSense.  
  
3.  Adicione a seguir importa.  
  
     [!code-vb[VSSDKQuickInfoTest #1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)][!code-csharp[VSSDKQuickInfoTest n º 1  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]  
  
4.  Declarar uma classe que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>e nomeie-o `TestQuickInfoSource`.  
  
     [!code-vb[VSSDKQuickInfoTest 2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)][!code-csharp[VSSDKQuickInfoTest n º 2  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]  
  
5.  Adicione campos para o provedor de origem Inforapida, o buffer de texto e um conjunto de nomes de método e assinaturas de método. Neste exemplo, os nomes de método e as assinaturas são inicializadas no `TestQuickInfoSource` construtor.  
  
     [!code-vb[VSSDKQuickInfoTest 3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)][!code-csharp[VSSDKQuickInfoTest n º 3  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]  
  
6.  Adicione um construtor que define o provedor de origem Inforapida e o buffer de texto e preenche o conjunto de nomes de método e assinaturas de método e descrições.  
  
     [!code-vb[VSSDKQuickInfoTest n º 4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)][!code-csharp[VSSDKQuickInfoTest n º 4  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]  
  
7.  Implementar o método de <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> . Neste exemplo, o método localiza a palavra atual ou a palavra anterior, se o cursor estiver no final de uma linha ou um buffer de texto. Se a palavra é um dos nomes de método, a descrição para esse nome de método é adicionada ao conteúdo Inforapida.  
  
     [!code-vb[N º 5 do VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)][!code-csharp[VSSDKQuickInfoTest n º 5  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]  
  
8.  Você também deve implementar um método Dispose (), como <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementa <xref:System.IDisposable>:  
  
     [!code-vb[VSSDKQuickInfoTest 6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)][!code-csharp[VSSDKQuickInfoTest 6  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>Implementando um provedor de origem Inforapida  
 O provedor da fonte de Inforapida serve basicamente para exportar em si como uma parte do componente MEF e criar a fonte Inforapida. Como é uma parte do componente MEF, pode importar outros componentes do MEF.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Para implementar um provedor de origem Inforapida  
  
1.  Declarar um provedor de origem Inforapida chamado `TestQuickInfoSourceProvider` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>e exportá-lo com um <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "Dica de ferramenta Inforapida fonte", um <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de antes = "padrão" e um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto".  
  
     [!code-vb[VSSDKQuickInfoTest #7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)][!code-csharp[VSSDKQuickInfoTest #7  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]  
  
2.  Importar dois serviços de editor, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> e <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, como propriedades de `TestQuickInfoSourceProvider`.  
  
     [!code-vb[VSSDKQuickInfoTest 8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)][!code-csharp[VSSDKQuickInfoTest n º 8  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]  
  
3.  Implementar <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> para retornar uma nova `TestQuickInfoSource`.  
  
     [!code-vb[VSSDKQuickInfoTest 9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)][!code-csharp[VSSDKQuickInfoTest 9  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]  
  
## <a name="implementing-a-quickinfo-controller"></a>Implementando um controlador de Inforapida  
 QuickInfo controladores determinam quando Inforapida deve ser exibida. Neste exemplo, Inforapida é exibida quando o ponteiro está sobre uma palavra que corresponde a um dos nomes de método. O controlador Inforapida implementa um manipulador de eventos do mouse em foco que dispara uma sessão Inforapida.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>Para implementar um controlador de Inforapida  
  
1.  Declarar uma classe que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>e nomeie-o `TestQuickInfoController`.  
  
     [!code-vb[VSSDKQuickInfoTest #10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)][!code-csharp[VSSDKQuickInfoTest #10  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]  
  
2.  Adicione campos privados para o modo de exibição de texto, os buffers de texto representados na exibição de texto, a sessão Inforapida e o provedor de controlador Inforapida.  
  
     [!code-vb[N º 11 do VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)][!code-csharp[VSSDKQuickInfoTest n º 11  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]  
  
3.  Adicione um construtor que define os campos e adiciona o manipulador de eventos do mouse em foco.  
  
     [!code-vb[VSSDKQuickInfoTest #12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)][!code-csharp[VSSDKQuickInfoTest #12  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]  
  
4.  Adicione o manipulador de eventos do mouse em foco que dispara a sessão Inforapida.  
  
     [!code-vb[VSSDKQuickInfoTest 13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)][!code-csharp[VSSDKQuickInfoTest 13  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]  
  
5.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> método para que ele remove o manipulador de eventos do mouse em foco quando o controlador é separado da exibição do texto.  
  
     [!code-vb[VSSDKQuickInfoTest #14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)][!code-csharp[VSSDKQuickInfoTest #14  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]  
  
6.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> método e o <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> método como métodos vazios para este exemplo.  
  
     [!code-vb[VSSDKQuickInfoTest #15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)][!code-csharp[VSSDKQuickInfoTest 15  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Implementando o provedor Inforapida controlador  
 O provedor do controlador Inforapida serve basicamente para exportar em si como uma parte do componente MEF e criar o controlador Inforapida. Como é uma parte do componente MEF, pode importar outros componentes do MEF.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>Para implementar o provedor de controlador Inforapida  
  
1.  Declare uma classe denominada `TestQuickInfoControllerProvider` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>e exportá-lo com um <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "Dica de ferramenta Inforapida controlador" e um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto":  
  
     [!code-vb[N º 16 do VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)][!code-csharp[VSSDKQuickInfoTest n º 16  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]  
  
2.  Importar o <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> como uma propriedade.  
  
     [!code-vb[VSSDKQuickInfoTest 17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)][!code-csharp[VSSDKQuickInfoTest 17  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]  
  
3.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> método instanciando o controlador Inforapida.  
  
     [!code-vb[VSSDKQuickInfoTest 18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)][!code-csharp[VSSDKQuickInfoTest n º 18  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]  
  
## <a name="building-and-testing-the-code"></a>Compilar e testar o código  
 Para testar esse código, compile a solução QuickInfoTest e executá-lo na instância experimental.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>Para compilar e testar a solução QuickInfoTest  
  
1.  Compile a solução.  
  
2.  Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
3.  Crie um arquivo de texto e tipo de texto que inclui as palavras "Adicionar" e "subtrair".  
  
4.  Mova o ponteiro sobre uma das ocorrências de "Adicionar". A assinatura e a descrição de `add` método deve ser exibido.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Vincular um tipo de conteúdo a uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
