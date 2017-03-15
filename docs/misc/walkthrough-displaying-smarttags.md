---
title: "Passo a passo: Exibindo marcas inteligentes | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK], new - marcas inteligentes"
ms.assetid: 10bb4f69-b259-41f0-b91a-69b04385d9a5
caps.latest.revision: 31
caps.handback.revision: 31
manager: "douge"
---
# Passo a passo: Exibindo marcas inteligentes
Marcas inteligentes foram preteridas em favor de lâmpadas. Consulte [Passo a passo: Exibindo sugestões de lâmpada](../Topic/Walkthrough:%20Displaying%20Light%20Bulb%20Suggestions.md).  
  
 Marcas inteligentes são marcas no texto que se expandem para exibir um conjunto de ações. Por exemplo, em um projeto Visual Basic ou Visual c\#, uma linha vermelha aparecerá em uma palavra quando você renomeia um identificador como um nome de variável. Quando você move o ponteiro sobre o sublinhado, um botão é exibido próximo do ponteiro. Se você clicar no botão, uma ação sugerida é exibida, por exemplo, **foi lido renomear para IsReady**. Se você clicar em ação, todas as referências aos **foi lido** no projeto são renomeados **IsReady**.  
  
 Embora as marcas inteligentes são parte da implementação do IntelliSense no editor, você pode implementar as marcas inteligentes, subclassificar <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>, e implementar o <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> interface e o <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> interface.  
  
> [!NOTE]
>  Outros tipos de marcas podem ser implementados de maneira semelhante.  
  
 A instrução a seguir mostra como criar uma marca inteligente que aparece na palavra atual e tem duas ações sugeridas: **Converter em maiúsculas** e **Converter em letras minúsculas**.  
  
## Pré-requisitos  
 Para seguir este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Criando um projeto do Managed Extensibility Framework \(MEF\)  
  
#### Para criar um projeto MEF  
  
1.  Crie um projeto de classificação do Editor. Nomeie a solução `SmartTagTest`.  
  
2.  Abra o arquivo source.extension.vsixmanifest no Editor de manifesto VSIX.  
  
3.  Verifique se o **ativos** seção contém um `Microsoft.VisualStudio.MefComponent` tipo, o **fonte** é definido como `A project in current solution`, e **projeto** é definido como SmartTagTest.dll.  
  
4.  Salve e feche source.extension.vsixmanifest.  
  
5.  Adicione a seguinte referência ao projeto e defina **CopyLocal** para `false`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
6.  Exclua os arquivos de classe existentes.  
  
## Implementando um marcador de marcas inteligentes  
  
#### Para implementar um marcador de marcas inteligentes  
  
1.  Adicione um arquivo de classe e nomeie\-o `TestSmartTag`.  
  
2.  Adicione as seguintes importações:  
  
     [!code-cs[VSSDKSmartTagTest#1](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_1.cs)]
     [!code-vb[VSSDKSmartTagTest#1](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_1.vb)]  
  
3.  Adicione uma classe chamada `TestSmartTag` que herda de <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-cs[VSSDKSmartTagTest#2](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_2.cs)]
     [!code-vb[VSSDKSmartTagTest#2](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_2.vb)]  
  
4.  Adicione um construtor para essa classe que chama o construtor base com um <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> de <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, isso fará com que uma linha azul apareça sob o primeiro caractere de uma palavra. \(Se você usar <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, uma linha vermelha aparecerá sob o último caractere da palavra.\)  
  
     [!code-cs[VSSDKSmartTagTest#3](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_3.cs)]
     [!code-vb[VSSDKSmartTagTest#3](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_3.vb)]  
  
5.  Adicione uma classe chamada `TestSmartTagger` que herda de <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> do tipo `TestSmartTag`, e implementa <xref:System.IDisposable>.  
  
     [!code-cs[VSSDKSmartTagTest#4](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_4.cs)]
     [!code-vb[VSSDKSmartTagTest#4](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_4.vb)]  
  
6.  Adicione os seguintes campos privados para a classe de marcador.  
  
     [!code-cs[VSSDKSmartTagTest#5](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_5.cs)]
     [!code-vb[VSSDKSmartTagTest#5](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_5.vb)]  
  
7.  Adicione um construtor que define os campos particulares e assina o <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> evento.  
  
     [!code-cs[VSSDKSmartTagTest#6](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_6.cs)]
     [!code-vb[VSSDKSmartTagTest#6](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_6.vb)]  
  
8.  Implementar <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> para que a marca é criada para a palavra atual. \(Esse método também chama um método particular `GetSmartTagActions` que é explicado posteriormente.\)  
  
     [!code-cs[VSSDKSmartTagTest#7](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_7.cs)]
     [!code-vb[VSSDKSmartTagTest#7](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_7.vb)]  
  
9. Adicione um `GetSmartTagActions` método para configurar as ações de marca inteligente. As ações propriamente ditas são implementadas em etapas posteriores.  
  
     [!code-cs[VSSDKSmartTagTest#8](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_8.cs)]
     [!code-vb[VSSDKSmartTagTest#8](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_8.vb)]  
  
10. Declarar o `SmartTagsChanged` evento.  
  
     [!code-cs[VSSDKSmartTagTest#9](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_9.cs)]
     [!code-vb[VSSDKSmartTagTest#9](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_9.vb)]  
  
11. Implementar o `OnLayoutChanged` manipulador de eventos para gerar o `TagsChanged` evento, que faz com que <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> seja chamado.  
  
     [!code-cs[VSSDKSmartTagTest#10](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_10.cs)]
     [!code-vb[VSSDKSmartTagTest#10](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_10.vb)]  
  
12. Implementar o <xref:System.IDisposable.Dispose%2A> método para que ele cancela a inscrição do <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> evento.  
  
     [!code-cs[VSSDKSmartTagTest#11](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_11.cs)]
     [!code-vb[VSSDKSmartTagTest#11](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_11.vb)]  
  
## Implementando o provedor de marcador de marca inteligente  
  
#### Para implementar o provedor de marcador de marca inteligente  
  
1.  Adicione uma classe chamada `TestSmartTagTaggerProvider` que herda de <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. Exportá\-lo com um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "text", um <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de antes \= "padrão" e um <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-cs[VSSDKSmartTagTest#12](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_12.cs)]
     [!code-vb[VSSDKSmartTagTest#12](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_12.vb)]  
  
2.  Importar o <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> como uma propriedade.  
  
     [!code-cs[VSSDKSmartTagTest#13](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_13.cs)]
     [!code-vb[VSSDKSmartTagTest#13](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_13.vb)]  
  
3.  Implementar o <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> método.  
  
     [!code-cs[VSSDKSmartTagTest#14](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_14.cs)]
     [!code-vb[VSSDKSmartTagTest#14](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_14.vb)]  
  
## Implementar ações com marcas inteligentes  
  
#### Para implementar ações com marcas inteligentes  
  
1.  Crie duas classes, a primeira chamada `UpperCaseSmartTagAction` e a segunda chamada `LowerCaseSmartTagAction`. Ambas as classes implementam <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction>.  
  
     [!code-cs[VSSDKSmartTagTest#15](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_15.cs)]
     [!code-vb[VSSDKSmartTagTest#15](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_15.vb)]  
  
     [!code-cs[VSSDKSmartTagTest#16](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_16.cs)]
     [!code-vb[VSSDKSmartTagTest#16](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_16.vb)]  
  
 Ambas as classes são semelhantes, exceto que um chama <xref:System.String.ToUpper%2A> e as outras chamadas <xref:System.String.ToLower%2A>. As etapas a seguir abrangem apenas a classe de ação em maiúsculas, mas você deve implementar ambas as classes. Use as etapas para implementar a ação maiúsculas como um padrão para implementar a ação em minúsculas.  
  
1.  Declare um conjunto de campos particulares.  
  
     [!code-cs[VSSDKSmartTagTest#17](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_17.cs)]
     [!code-vb[VSSDKSmartTagTest#17](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_17.vb)]  
  
2.  Adicione um construtor que define os campos.  
  
     [!code-cs[VSSDKSmartTagTest#18](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_18.cs)]
     [!code-vb[VSSDKSmartTagTest#18](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_18.vb)]  
  
3.  Implemente as propriedades da seguinte maneira.  
  
     [!code-cs[VSSDKSmartTagTest#19](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_19.cs)]
     [!code-vb[VSSDKSmartTagTest#19](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_19.vb)]  
  
4.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction.Invoke%2A> método substituindo o texto na extensão com seu equivalente em maiúsculas.  
  
     [!code-cs[VSSDKSmartTagTest#20](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_20.cs)]
     [!code-vb[VSSDKSmartTagTest#20](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_20.vb)]  
  
## Compilar e testar o código  
 Para testar esse código, crie a solução SmartTagTest e executá\-lo na instância experimental.  
  
#### Para compilar e testar a solução SmartTagTest  
  
1.  Compile a solução.  
  
2.  Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
3.  Crie um arquivo de texto e digite algum texto.  
  
     Uma linha azul deve ser exibida sob a primeira letra da primeira palavra do texto.  
  
4.  Mova o ponteiro sobre a linha azul.  
  
     Um botão deve ser exibido perto do ponteiro.  
  
5.  Quando você clica no botão, duas sugeridas ações devem ser exibidas: **Converter em maiúsculas** e **Converter em letras minúsculas**. Se você clicar na primeira ação, todo o texto na palavra atual deve ser convertido em letras maiúsculas. Se você clicar na segunda ação, todo o texto deve ser convertido em letras minúsculas.  
  
## Consulte também  
 [Passo a passo: Vinculação de um tipo de conteúdo para uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)