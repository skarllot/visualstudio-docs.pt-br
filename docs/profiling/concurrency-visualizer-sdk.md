---
title: "SDK da Visualização Simultânea | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 1a51a8dbf28be35febf4a0954a997e542ffd0f09
ms.openlocfilehash: 4734ac951c93fb7921e637494e91c1ca1cf16594

---
# <a name="concurrency-visualizer-sdk"></a>SDK do Visualizador de Simultaneidade
Descreve como instrumentalizar o código-fonte usando o SDK de Visualização Simultânea para exibir informações adicionais na Visualização Simultânea. É possível associar os dados adicionais a fases e eventos em seu código. Estas visualizações adicionais são conhecidas como *marcadores*.  Para ver um passo a passo introdutório, consulte [Apresentando o SDK da Visualização Simultânea](http://go.microsoft.com/fwlink/?LinkId=235405).  
  
## <a name="properties"></a>Propriedades  
 Sinalizadores, intervalos e mensagens têm, cada um, duas propriedades: categoria e importância. Na caixa de diálogo [Configurações Avançadas](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md), é possível usar essas propriedades para filtrar o conjunto de marcadores exibidos. Além disso, essas propriedades afetam a representação visual de marcadores. Por exemplo, o tamanho dos sinalizadores é usado para representar a importância. Além disso, a cor é usada para indicar a categoria.  
  
## <a name="basic-usage"></a>Uso básico  
 A Visualização Simultânea expõe um provedor padrão que pode ser usado para gerar marcadores. O provedor já está registrado junto com a Visualização Simultânea e não é necessário fazer mais nada para fazer os marcadores serem exibidos na interface do usuário.  
  
### <a name="c-and-visual-basic"></a>C# e Visual Basic  
 Em C#, o Visual Basic e outro código gerenciado usam o provedor padrão chamando <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers>. Ele expõe quatro funções para gerar marcadores: <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteFlag%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.EnterSpan%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteMessage%2A> e <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteAlert%2A>. Há várias sobrecargas para essas funções, dependendo se você deseja usar os padrões para as propriedades.  A sobrecarga mais simples aceita apenas um parâmetro de cadeia de caracteres que especifica a descrição do evento. A descrição é exibida nos relatórios da Visualização Simultânea.  
  
##### <a name="to-add-sdk-support-to-a-c-or-visual-basic-project"></a>Para adicionar suporte do SDK a um projeto em C# ou do Visual Basic  
  
1.  Na barra de menus, escolha **Analisar**, **Visualização Simultânea**, **Adicionar SDK ao projeto**.  
  
2.  Selecione o projeto no qual você deseja acessar o SDK e, em seguida, escolha o botão **Adicionar SDK ao Projeto Selecionado**.  
  
3.  Adicione uma importação ou instrução using ao seu código.  
  
    ```CSharp  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
    ```VB  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
    ```  
  
### <a name="c"></a>C++  
 Em C++, crie um objeto [classe marker_series](../profiling/marker-series-class.md) e use-o para chamar funções.  A classe `marker_series` expõe três funções para gerar marcadores, a [marker_series::write_flag Method](../profiling/marker-series-write-flag-method.md), a [marker_series::write_message Method](../profiling/marker-series-write-message-method.md) e a [marker_series::write_alert Method](../profiling/marker-series-write-alert-method.md).  
  
##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>Para adicionar suporte do SDK a um projeto em C# ou em C  
  
1.  Na barra de menus, escolha **Analisar**, **Visualização Simultânea**, **Adicionar SDK ao projeto**.  
  
2.  Selecione o projeto no qual você deseja acessar o SDK e, em seguida, escolha o botão **Adicionar SDK ao Projeto Selecionado**.  
  
3.  Para C++, inclua `cvmarkersobj.h`. Para C, inclua `cvmarkers.h`.  
  
4.  Adicione uma instrução using ao seu código.  
  
    ```  
    using namespace Concurrency::diagnostic;  
    ```  
  
5.  Crie um objeto `marker_series` e passe-o para o construtor `span`.  
  
    ```C++  
  
    marker_series mySeries;  
    span s(mySeries, _T("Span description"));  
  
    ```  
  
## <a name="custom-usage"></a>Uso personalizado  
 Para cenários avançados, o SDK da Visualização Simultânea expõe mais controle.  Dois conceitos principais estão associados a cenários mais avançados: séries de marcadores e provedores de marcador. Os provedores de marcador são diferentes provedores ETW (cada um tem um GUID diferente). As séries de marcadores são canais seriais de eventos gerados por um provedor. É possível usá-los para organizar os eventos gerados por um provedor de marcador.  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>Para usar um novo provedor de marcador em um projeto em C# ou do Visual Basic  
  
1.  Crie um objeto <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter>.  O construtor aceita um GUID.  
  
2.  Para registrar o provedor, abra a caixa de diálogo [Configurações Avançadas](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) da Visualização Simultânea.  Selecione a guia **Marcadores** e, em seguida, escolha o botão **Adicionar novo provedor**. Na caixa de diálogo [Configurações Avançadas](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md), digite o GUID usado para criar o provedor e uma descrição do provedor.  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>Para usar um novo provedor de marcador em um projeto em C ou em C++  
  
1.  Use a função `CvInitProvider` para inicializar um PCV_PROVIDER.  O construtor aceita um GUID* e PCV_PROVIDER\*.  
  
2.  Para registrar o provedor, abra a caixa de diálogo [Configurações Avançadas](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md).  Selecione a guia **Marcadores** e, em seguida, escolha o botão **Adicionar novo provedor**. Nessa caixa de diálogo, insira o GUID usado para criar o provedor e uma descrição do provedor.  
  
#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>Para usar uma série de marcadores em um projeto em C# ou do Visual Basic  
  
1.  Para usar um novo <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries>, crie-o primeiro usando um objeto <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> e, em seguida, gere os eventos de marcador diretamente da nova série.  
  
    ```CSharp  
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries(″Series 1″);  
    series1.WriteFlag(″My flag″);  
    ```  
  
    ```VB  
    Dim series1 As New myMarkerWriter.CreateMarkerSeries(″Series 1″)  
    series1.WriteFlag(″My flag″)  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>Para usar uma série de marcadores em um projeto em C++  
  
1.  Crie um objeto `marker_series`.  É possível gerar eventos nessa nova série.  
  
    ```scr  
    marker_series series;  
    series.write_flag(_T("Hello world!"));  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>Para usar uma série de marcadores em um projeto em C  
  
1.  Use a função `CvCreateMarkerSeries` para criar um PCV_MARKERSERIES.  
  
    ```C++  
    PCV_MARKERSERIES series;  
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);  
    CvWriteFlag(series, _T("Writing a flag"));  
    ```  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Referência de biblioteca C++](../profiling/cpp-library-reference.md)|Descreve a API da Visualização Simultânea para C++.|  
|[Referência de biblioteca C](../profiling/c-library-reference.md)|Descreve a API da Visualização Simultânea para C.|  
|<xref:Microsoft.ConcurrencyVisualizer.Instrumentation>|Descreve a API da Visualização Simultânea para o código gerenciado.|  
|[Visualização Simultânea](../profiling/concurrency-visualizer.md)|Informações de referência para as exibições e relatórios de arquivos de dados de criação de perfil gerados usando o método de simultaneidade e que incluem dados de execução de threads.|


<!--HONumber=Feb17_HO4-->


