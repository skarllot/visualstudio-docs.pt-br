---
title: "Como escrever um visualizador | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, visualizadores"
  - "visualizadores, gravando"
ms.assetid: 625a0d4f-abcc-43f2-9f8c-31c131a4378e
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como escrever um visualizador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode escrever um visualizador personalizado para um objeto de qualquer classe gerenciada com exceção de <xref:System.Object> ou <xref:System.Array>.  
  
> [!NOTE]
>  Nos aplicativos do **Store**, somente os visualizadores do texto padrão HTML, XML e JSON são suportados.  Não há suporte para visualizadores personalizados \(criados pelo usuário\).  
  
 A arquitetura de um visualizador de depurador tem duas partes:  
  
-   O *lado do depurador* é executado no depurador do Visual Studio.  O código do lado depurador cria e exibe a interface do usuário para o visualizador.  
  
-   O *lado a ser depurado* é executado dentro do processo que o Visual Studio está depurando \(o *lado a ser depurado*\).  
  
 O objeto de dados que você deseja visualizar \(um objeto String, por exemplo\) existe no processo a ser depurado.  Assim, o lado a ser depurado precisa enviar esse objeto de dados para o lado do depurador, que pode então exibi\-lo usando uma interface de usuário que você cria.  
  
 O lado do depurador recebe esse objeto de dados a ser visualizado de um *provedor de objeto* que implementa a interface <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>.  O lado a ser depurado envia o objeto de dados pela *origem do objeto*, que é derivada de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.  O provedor do objeto também pode enviar dados de volta para a origem do objeto, que permite escrever um visualizador que edita, além de exibir, dados.  O provedor do objeto pode ser substituído para se comunicar com o avaliador de expressão e, consequentemente, com a origem do objeto  
  
 O lado a ser depurado e o lado do depurador comunicam\-se por meio do <xref:System.IO.Stream>.  Os métodos são fornecidos para serializar um objeto de dados em um <xref:System.IO.Stream> e desserializar o <xref:System.IO.Stream> de volta para um objeto de dados.  
  
 O código do lado a ser depurado é especificado usando o atributo DebuggerVisualizer \(<xref:System.Diagnostics.DebuggerVisualizerAttribute>\).  
  
 Para criar a interface do usuário do visualizador no lado do depurador, você deverá criar uma classe que herda de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> e substitui o método <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> para exibir a interface.  
  
 Você pode usar <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> para exibir formulários, caixas de diálogo e os controles do Windows a partir do visualizador.  
  
 O suporte para tipos genéricos é limitado.  Você poderá escrever um visualizador para um destino que é um tipo genérico somente se o tipo genérico for um tipo aberto.  Essa restrição é a mesma que a restrição ao usar o atributo `DebuggerTypeProxy`.  Para obter detalhes, consulte [Usando o atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).  
  
 Os visualizadores personalizados podem ter considerações de segurança.  Consulte [Considerações de segurança do visualizador](../debugger/visualizer-security-considerations.md).  
  
 Os procedimentos a seguir dão uma exibição de alto nível do que você precisa fazer para criar um visualizador.  Para obter uma explicação mais detalhada, consulte [Instruções passo a passo: escrevendo um visualizador em C\#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
### Para criar o lado do depurador  
  
1.  Use os métodos <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> para obter o objeto visualizado no lado do depurador.  
  
2.  Crie uma classe que herda de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.  
  
3.  Substitua o método <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> para exibir sua interface.  Use os métodos <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> para exibir os formulários, as caixas de diálogo e os controles do Windows como parte da interface.  
  
4.  Aplique <xref:System.Diagnostics.DebuggerVisualizerAttribute>, permitindo que você tenha um visualizador \(<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>\).  
  
### Para criar o lado a ser depurado  
  
1.  Aplique <xref:System.Diagnostics.DebuggerVisualizerAttribute>, permitindo que você tenha um visualizador \(<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>\) e uma origem do objeto \(<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>\).  Se você omitir a origem do objeto, uma fonte do objeto padrão será usada  
  
2.  Se você quiser que o visualizador edite objetos de dados, bem como exibi\-los, precisará substituir os métodos `TransferData` ou `CreateReplacementObject` do <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.  
  
## Consulte também  
 [Visualizadores](../debugger/create-custom-visualizers-of-data.md)   
 [Como instalar um visualizador](../debugger/how-to-install-a-visualizer.md)   
 [Como testar e depurar um visualizador](../Topic/How%20to:%20Test%20and%20Debug%20a%20Visualizer.md)   
 [Considerações de segurança do visualizador](../debugger/visualizer-security-considerations.md)