---
title: "Analisar a qualidade do c&#243;digo do Visual Basic e C# em aplicativos da Store usando a an&#225;lise de c&#243;digo est&#225;tico do Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.csvb.express"
ms.assetid: cab553fc-19a9-4cbf-858e-8200258ffe50
caps.latest.revision: 14
caps.handback.revision: 14
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
---
# Analisar a qualidade do c&#243;digo do Visual Basic e C# em aplicativos da Store usando a an&#225;lise de c&#243;digo est&#225;tico do Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Applies to Windows and Windows Phone](../debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 A ferramenta de análise de código no Visual Studio Express examina seu código para um conjunto de defeitos comuns e violações de práticas recomendadas de programação.  Avisos da análise de código diferem de avisos e erros do compilador porque a ferramenta de análise de código procura por padrões de código específicos que são válidos, mas ainda podem criar problemas para você ou outras pessoas que usam seu código.  Análise de código também pode localizar defeitos em seu código que são difíceis de serem descobertas por meio de testes.  Executando a ferramenta de análise de código em intervalos regulares durante o processo de desenvolvimento pode melhorar a qualidade do seu aplicativo concluído.  
  
> [!NOTE]
>  No Visual Studio Ultimate, Visual Studio Premium e Professional do Visual Studio, você pode usar a funcionalidade completa da análise de código.  Consulte[Analisando a qualidade do aplicativo usando ferramentas de análise de código](http://msdn.microsoft.com/library/dd264897.aspx)na biblioteca MSDN.  
  
## Neste tópico  
 Você pode aprender sobre:  
  
 [Executar análise de código](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Run)  
  
 [Analisando e resolvendo avisos da análise de código](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Analyze)  
  
 [Suprimindo avisos da análise de código](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Suppress)  
  
 [Pesquisando e filtrando resultados da análise de código](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Search)  
  
 [Avisos da análise de código do Visual Basic e C#.](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Warnings)  
  
##  <a name="BKMK_Run"></a> Executar análise de código  
 Para executar análise de código em sua solução do Visual Studio:  
  
-   Sobre o**criar**menu, escolha**Executar análise de código na solução**.  
  
 Para executar análise de código automaticamente cada vez que você constrói um projeto:  
  
1.  Clique no nome do projeto no Solution Explorer e escolha**propriedades**.  
  
2.  Na página de propriedades do projeto, escolha**a análise de código**e, em seguida, escolha**habilitar análise de código na compilação \(define a constante CODEANALYSIS\)**.  
  
 A solução é compilada e análise de código é executado.  Resultados aparecem na janela de análise de código.  
  
 ![Janela de análise de código](../test/media/ca_managed_collapsed.png "CA\_Managed\_Collapsed")  
  
##  <a name="BKMK_Analyze"></a> Analisando e resolvendo avisos da análise de código  
 Para analisar um aviso específico, clique no título do aviso na janela análise de código.  O aviso se expande para exibir informações detalhadas sobre o problema.  
  
 ![Aviso de análise de código expandido](../test/media/ca_managed_callouts.png "CA\_Managed\_Callouts")  
  
 Quando você expande um aviso, a linha de código que causou o aviso é realçada no editor de código do Visual Studio.  
  
 ![Realce de texto com a análise de código](../test/media/ca_managed_sourceline.png "CA\_Managed\_SourceLine")  
  
 Depois de entender o problema, você pode resolvê\-lo em seu código.  Em seguida, execute novamente a análise de código para certificar\-se de que o aviso não aparece mais na janela análise de código e que a correção não gerou novos avisos.  
  
> [!TIP]
>  Você pode executar novamente a análise de código na janela de análise de código.  Clique o**Analisar**botão e escolha o escopo da análise.  Você pode executar novamente a análise na solução inteira ou em um projeto selecionado.  
  
##  <a name="BKMK_Suppress"></a> Suprimindo avisos da análise de código  
 Há momentos em que você pode decidir não corrigir um aviso de análise de código.  Você pode decidir que resolver o aviso exige recodificação demais a probabilidade de que o problema ocorrerá em qualquer implementação real do seu código.  Ou você pode achar que a análise é usada no aviso é inadequada nesse contexto específico.  Você pode suprimir avisos individuais para que eles não aparecem mais na janela análise de código.  
  
 Para suprimir um aviso:  
  
1.  Se as informações detalhadas não for exibidas, clique no título do aviso para expandi\-la.  
  
2.  Escolha o**ações**link na parte inferior do aviso.  
  
3.  Aponte para**suprimir mensagem**e, em seguida, escolha**na origem**ou**no arquivo de supressão**.  
  
    -   **Na origem**insere um`SuppressMessage`atributo no arquivo de origem acima do método que gerou o aviso.  Isso torna a supressão mais detectáveis.  
  
    -   **No arquivo de supressão**adiciona um`SuppressMessage`de atributo para o**GlobalSuppressions.cs**arquivo do projeto.  Isso pode facilitar o gerenciamento das supressões.  Observe que o`SuppressMessage`atributo adicionado**GlobalSuppression.cs**também afeta o método que gerou o aviso.  Ele não suprime o aviso globalmente.  
  
     Sua decisão suprimir o aviso no arquivo de origem ou no arquivo de supressão depende suas necessidades e estilo de codificação.  
  
##  <a name="BKMK_Search"></a> Pesquisando e filtrando resultados da análise de código  
 Você pode pesquisar listas longas de mensagens de aviso e você pode filtrar avisos em soluções multiprojeto.  
  
 ![Pesquisar e filtrar a janela de análise de código](../test/media/ca_searchfilter.png "CA\_SearchFilter")  
  
 Em[!INCLUDE[vs_dev11_expwin_long](../misc/includes/vs_dev11_expwin_long_md.md)]todos os avisos têm o nível de gravidade de aviso de análise de código.  
  
##  <a name="BKMK_Warnings"></a> Avisos da análise de código do Visual Basic e C\#.  
 Análise de código gera os seguintes avisos:  
  
 [CA1001: tipos que possuem campos descartáveis devem ser descartáveis](http://msdn.microsoft.com/library/ms182172.aspx)  
  
 [CA1821: Remova finalizadores vazios](http://msdn.microsoft.com/library/bb264476.aspx)  
  
 [CA2213: campos descartáveis devem ser descartados](http://msdn.microsoft.com/library/ms182328.aspx)  
  
 [CA2229: implementar construtores de serialização](http://msdn.microsoft.com/library/ms182343.aspx)  
  
 [CA2231: sobrecarregar operador equals ao substituir ValueType. Equals](http://msdn.microsoft.com/library/ms182359.aspx)