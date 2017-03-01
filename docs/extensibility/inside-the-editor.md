---
title: Dentro do Editor | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
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
ms.openlocfilehash: 910b2bf452e085149b8adf23b8a167b9b39eeb3d
ms.lasthandoff: 02/22/2017

---
# <a name="inside-the-editor"></a>Dentro do Editor
O editor é composto de um número de diferentes subsistemas, que são projetadas para impedir que o editor de texto separado de modelo a exibição de texto e a interface do usuário.  
  
 Estas seções descrevem diferentes aspectos do editor:  
  
-   [Visão geral dos subsistemas](../extensibility/inside-the-editor.md#overview)  
  
-   [O modelo de texto](../extensibility/inside-the-editor.md#textmodel)  
  
-   [A exibição de texto](../extensibility/inside-the-editor.md#textview)  
  
 Estas seções descrevem os recursos do editor:  
  
-   [Marcas e classificadores](../extensibility/inside-the-editor.md#tagsandclassifiers)  
  
-   [Adornos](../extensibility/inside-the-editor.md#adornments)  
  
-   [Projeção](../extensibility/inside-the-editor.md#projection)  
  
-   [Estrutura de tópicos](../extensibility/inside-the-editor.md#outlining)  
  
-   [Associações de mouse](../extensibility/inside-the-editor.md#mousebindings)  
  
-   [Operações do Editor](../extensibility/inside-the-editor.md#editoroperations)  
  
-   [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
##  <a name="a-nameoverviewa-overview-of-the-subsystems"></a><a name="overview"></a>Visão geral dos subsistemas  
  
### <a name="text-model-subsystem"></a>Subsistema do modelo de texto  
 O subsistema de modelo de texto é responsável para representar texto e habilitar sua manipulação. O subsistema de modelo de texto contém o <xref:Microsoft.VisualStudio.Text.ITextBuffer>interface, que descreve a sequência de caracteres que deve ser exibida pelo editor.</xref:Microsoft.VisualStudio.Text.ITextBuffer> Esse texto pode ser modificado, controlado e manipulado de várias maneiras. O modelo de texto também fornece tipos para os seguintes aspectos:  
  
-   Um serviço que associa a arquivos de texto e gerencia lendo e gravando-os no sistema de arquivos.  
  
-   Um serviço diferencial que localiza as diferenças mínimas entre duas sequências de objetos.  
  
-   Um sistema usado para descrever o texto em um buffer em termos de subconjuntos do texto em outros buffers.  
  
 O subsistema de modelo de texto está livre de conceitos de interface de usuário. Por exemplo, não é responsável pelo layout de texto ou formatação de texto, e ele não tem conhecimento da ornamentos visual que pode ser associado com o texto.  
  
 Os tipos públicos do subsistema de modelo de texto estão contidos em Microsoft.VisualStudio.Text.Data.dll e Microsoft.VisualStudio.CoreUtilitiy.dll, depender apenas de biblioteca de classes base do .NET Framework e o Managed Extensibility Framework (MEF).  
  
### <a name="text-view-subsystem"></a>Subsistema de modo de exibição de texto  
 O subsistema do modo de exibição de texto é responsável por formatação e exibição de texto. Os tipos neste subsistema são divididos em duas camadas, dependendo se os tipos se baseiam no Windows Presentation Foundation (WPF). Os tipos mais importantes são <xref:Microsoft.VisualStudio.Text.Editor.ITextView>e <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>, que controlam o conjunto de linhas de texto a ser exibido, e também o cursor, a seleção e os recursos de adorno o texto usando elementos de UI do WPF.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> </xref:Microsoft.VisualStudio.Text.Editor.ITextView> Esse subsistema fornece também a área de exibição de margens ao redor do texto. Essas margens podem ser estendidas e podem conter diferentes tipos de efeitos visuais e conteúdos. Exemplos de margens são linha número exibe e barras de rolagem.  
  
 Os tipos públicos do subsistema de modo de exibição de texto estão contidos em Microsoft.VisualStudio.Text.UI.dll e Microsoft.VisualStudio.Text.UI.Wpf.dll. O primeiro conjunto contém os elementos independentes de plataforma e o segundo contém os elementos do WPF-específica.  
  
### <a name="classification-subsystem"></a>Subsistema de classificação  
 O subsistema de classificação é responsável por determinar propriedades de fonte para texto. Um classificador quebra o texto em classes diferentes, por exemplo, "palavra-chave" ou "comentário". O mapa do formato de classificação relaciona essas classes para propriedades de fonte real, por exemplo, "azul Consolas 10 pt". Essas informações são usadas pelo modo de exibição de texto quando formata e processa o texto. Marcação, que é descrito em mais detalhes posteriormente neste tópico, permite que os dados a serem associados com intervalos de texto.  
  
 Os tipos públicos do subsistema de classificação estão contidos em Microsoft.VisualStudio.Text.Logic.dll e interagem com os aspectos visuais de classificação, que estão contidos em Microsoft.VisualStudio.Text.UI.Wpf.dll.  
  
### <a name="operations-subsystem"></a>Subsistema de operações  
 O subsistema de operações define o comportamento do editor. Ele fornece a implementação de comandos do editor Visual Studio e o sistema de desfazer.  
  
## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Examinar mais de perto o modelo de texto e a exibição de texto  
  
###  <a name="a-nametextmodela-the-text-model"></a><a name="textmodel"></a>O modelo de texto  
 O subsistema de modelo de texto consiste em diferentes grupos de tipos de texto. Isso inclui o buffer de texto, os instantâneos de texto e intervalos de texto.  
  
#### <a name="text-buffers-and-text-snapshots"></a>Buffers de texto e texto instantâneos  
 O <xref:Microsoft.VisualStudio.Text.ITextBuffer>interface representa uma sequência de caracteres Unicode que são codificados usando UTF-16, que é a codificação usada pelo `String` tipo no .NET Framework.</xref:Microsoft.VisualStudio.Text.ITextBuffer> Um buffer de texto pode ser persistente como um documento do sistema de arquivo, mas isso não é necessário.  
  
 O que <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>é usado para criar um buffer de texto vazio, ou um buffer de texto que é inicializado a partir de uma cadeia de caracteres ou <xref:System.IO.TextReader>.</xref:System.IO.TextReader> </xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> O buffer de texto pode ser transferido para o sistema de arquivos como <xref:Microsoft.VisualStudio.Text.ITextDocument>.</xref:Microsoft.VisualStudio.Text.ITextDocument>  
  
 O buffer de texto pode ser editado por qualquer thread até que um thread se apropria de buffer de texto chamando <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>.</xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A> Depois disso, somente esse thread pode executar edições.  
  
 Um buffer de texto pode passar por várias versões durante seu ciclo de vida. Uma nova versão é gerada sempre que o buffer é editado e um imutável <xref:Microsoft.VisualStudio.Text.ITextSnapshot>representa o conteúdo dessa versão do buffer.</xref:Microsoft.VisualStudio.Text.ITextSnapshot> Como os instantâneos de texto são imutáveis, você pode acessar um instantâneo de texto em qualquer thread, sem restrições, mesmo se o buffer de texto representa continua a mudar.  
  
#### <a name="text-snapshots-and-text-snapshot-lines"></a>Instantâneos de texto e linhas de instantâneo de texto  
 Você pode exibir o conteúdo de um instantâneo de texto como uma sequência de caracteres ou como uma sequência de linhas. Caracteres e as linhas são que ambos indexados começando com zero. Um instantâneo de texto vazio contém caracteres e uma linha vazia. Uma linha é delimitada por qualquer sequência de caracteres de quebra de linha Unicode válida ou o início ou fim do buffer. Caracteres de quebra de linha explicitamente são representados no instantâneo de texto e as quebras de linha em um instantâneo de texto não tiverem o mesmo.  
  
> [!NOTE]
>  Para obter mais informações sobre os caracteres de quebra de linha no editor do Visual Studio, consulte [codificações e quebras de linha](../ide/encodings-and-line-breaks.md).  
  
 Uma linha de texto é representada por um <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine>objeto, que pode ser obtido a partir de um instantâneo de texto para um número de linha específico ou para uma posição de caracteres em particular.</xref:Microsoft.VisualStudio.Text.ITextSnapshotLine>  
  
#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints, SnapshotSpans e NormalizedSnapshotSpanCollections  
 Um <xref:Microsoft.VisualStudio.Text.SnapshotPoint>representa uma posição de caractere em um instantâneo.</xref:Microsoft.VisualStudio.Text.SnapshotPoint> A posição é garantida entre zero e o comprimento do instantâneo. Um <xref:Microsoft.VisualStudio.Text.SnapshotSpan>representa um intervalo de texto em um instantâneo.</xref:Microsoft.VisualStudio.Text.SnapshotSpan> Sua posição final é garantida entre zero e o comprimento do instantâneo. O <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>consiste em um conjunto de <xref:Microsoft.VisualStudio.Text.SnapshotSpan>objetos do mesmo instantâneo.</xref:Microsoft.VisualStudio.Text.SnapshotSpan> </xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>  
  
#### <a name="spans-and-normalizedspancollections"></a>Intervalos e NormalizedSpanCollections  
 Um <xref:Microsoft.VisualStudio.Text.Span>representa um intervalo que pode ser aplicado a um intervalo de texto em um instantâneo de texto.</xref:Microsoft.VisualStudio.Text.Span> Posições de instantâneo são baseadas em zero, para que podem começar intervalos em qualquer posição incluindo zero. O `End` propriedade de uma extensão é igual à soma de suas `Start` propriedade e seu `Length` propriedade. A `Span` não inclui o caractere que é indexado pelo `End` propriedade. Por exemplo, um intervalo que tem início = 5 e comprimento = 3 tem final = 8, e inclui os caracteres em posições 5, 6 e 7. A notação para esse período é 5..8).  
  
 Dois intervalos de interseção que tenham qualquer posições em comum, incluindo a posição final. Portanto, a interseção de [3, 5) e [2, 7) é [3, 5) e a interseção de [3, 5) e [5, 7) é [5, 5). (Observe que [5, 5) é um intervalo vazio.)  
  
 Dois intervalos sobreponham, se eles têm em comum, posições, exceto a posição final. Um intervalo vazio nunca se sobrepõe a qualquer outra extensão e a sobreposição de duas extensões nunca está vazia.  
  
 A <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection>é uma lista de extensões na ordem as propriedades de início das extensões.</xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> Na lista de extensões sobrepostos ou adjacentes são mesclados. Por exemplo, considerando o conjunto de intervalos de [5..9), [0..1), [3..6), e [9..10), a lista normalizada de extensões é [0..1), [3..10).  
  
#### <a name="itextedit-textversion-and-text-change-notifications"></a>ITextEdit, TextVersion e notificações de alteração de texto  
 O conteúdo de um buffer de texto pode ser alterado usando um <xref:Microsoft.VisualStudio.Text.ITextEdit>objeto.</xref:Microsoft.VisualStudio.Text.ITextEdit> Criando um objeto (usando um do `CreateEdit()` métodos de <xref:Microsoft.VisualStudio.Text.ITextBuffer>) inicia uma transação de texto que consiste em edições de texto.</xref:Microsoft.VisualStudio.Text.ITextBuffer> Cada edição é uma substituição de um intervalo de texto no buffer por uma cadeia de caracteres. As coordenadas e o conteúdo de cada edição são expressas em relação ao instantâneo do buffer quando a transação foi iniciada. O <xref:Microsoft.VisualStudio.Text.ITextEdit>objeto ajusta as coordenadas de edições que são afetadas por outras edições na mesma transação.</xref:Microsoft.VisualStudio.Text.ITextEdit>  
  
 Por exemplo, considere um buffer de texto que contém essa cadeia de caracteres:  
  
```  
abcdefghij  
```  
  
 Aplicar uma transação que contém duas edições, uma edição que substitui a extensão em [2..4) usando o caractere `X` e uma segunda edição que substitui a extensão em [6..9) usando o caractere `Y`. O resultado é esse buffer:  
  
```  
abXefYj  
```  
  
 As coordenadas para a segunda edição foram computadas em relação ao conteúdo do buffer no início da transação, antes da primeira edição foi aplicada.  
  
 As alterações para o buffer em vigor quando o <xref:Microsoft.VisualStudio.Text.ITextEdit>objeto confirmado chamando seu `Apply()` método.</xref:Microsoft.VisualStudio.Text.ITextEdit> Se houver pelo menos uma edição vazio, um novo <xref:Microsoft.VisualStudio.Text.ITextVersion>é criado, um novo <xref:Microsoft.VisualStudio.Text.ITextSnapshot>é criada e um `Changed` é gerado.</xref:Microsoft.VisualStudio.Text.ITextSnapshot> </xref:Microsoft.VisualStudio.Text.ITextVersion> Cada versão de texto tem um instantâneo de texto. Um instantâneo de texto representa o estado do buffer de texto completo após uma transação de edição, mas uma versão de texto descreve somente as alterações de um instantâneo para a próxima. Em geral, os instantâneos de texto são deve ser usado uma vez e depois são descartados, enquanto as versões de texto devem permanecer ativa por algum tempo.  
  
 Uma versão de texto contém <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>.</xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection> Essa coleção descreve as alterações que, quando aplicada ao instantâneo, produzirá o instantâneo subsequente. Cada <xref:Microsoft.VisualStudio.Text.ITextChange>na coleção contém a posição do caractere de alteração, a cadeia de caracteres de substituição e a cadeia de caracteres de substituição.</xref:Microsoft.VisualStudio.Text.ITextChange> A cadeia de caracteres de substituição está vazia para uma inserção básica e a cadeia de caracteres de substituição está vazia para uma exclusão básica. A coleção normalizada é sempre `null` para a versão mais recente do buffer de texto.  
  
 Apenas uma <xref:Microsoft.VisualStudio.Text.ITextEdit>objeto pode ser instanciado para um buffer de texto a qualquer momento e todas as edições de texto devem ser executadas no thread que possui o buffer de texto (se a propriedade tenha sido solicitada).</xref:Microsoft.VisualStudio.Text.ITextEdit> Uma edição de texto pode ser abandonada chamando seu `Cancel` método ou seu `Dispose` método.  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer>também fornece `Insert()`, `Delete()`, e `Replace()` métodos semelhantes aos encontrados no <xref:Microsoft.VisualStudio.Text.ITextEdit>interface.</xref:Microsoft.VisualStudio.Text.ITextEdit></xref:Microsoft.VisualStudio.Text.ITextBuffer> Chamando essas tem o mesmo efeito que a criação de um <xref:Microsoft.VisualStudio.Text.ITextEdit>objeto, fazer a chamada semelhante e, em seguida, aplicando a editar.</xref:Microsoft.VisualStudio.Text.ITextEdit>  
  
#### <a name="tracking-points-and-tracking-spans"></a>Pontos de controle e períodos de controle  
 Um <xref:Microsoft.VisualStudio.Text.ITrackingPoint>representa uma posição de caractere em um buffer de texto.</xref:Microsoft.VisualStudio.Text.ITrackingPoint> Se o buffer for editado de forma que faz com que a posição do caractere para mudar, o ponto de controle é deslocado com ele. Por exemplo, se um ponto de controle se refere à posição 10 em um buffer e cinco caracteres é inserido no início do buffer, o ponto de controle, em seguida, refere-se à posição 15. Se ocorrer uma inserção no precisamente a posição denotada pelo ponto de controle, seu comportamento é determinado pelo seu <xref:Microsoft.VisualStudio.Text.PointTrackingMode>, que poderá ser `Positive` ou `Negative`.</xref:Microsoft.VisualStudio.Text.PointTrackingMode> Se o modo de controle for positivo, que o ponto de controle refere-se para o mesmo caractere, que agora está no final da inserção; Se o modo de controle for negativo, o ponto de controle se refere ao primeiro caractere inserido na posição original. Se o caractere na posição que é representado por um ponto de controle for excluído, o ponto de controle é deslocado para o primeiro caractere que segue o intervalo excluído. Por exemplo, se um ponto de controle se refere ao caractere na posição 5, e os caracteres em posições 3 a 6 são excluídos, o ponto de controle refere-se com o caractere na posição 3.  
  
 Um <xref:Microsoft.VisualStudio.Text.ITrackingSpan>representa um intervalo de caracteres em vez de apenas uma posição.</xref:Microsoft.VisualStudio.Text.ITrackingSpan> Seu comportamento é determinado pelo seu <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>.</xref:Microsoft.VisualStudio.Text.SpanTrackingMode> Se o modo de controle de extensão é <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, aumenta o período de controle para incorporar o texto inserido em suas bordas; se o modo de controle de extensão é <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, o período de controle não incorporar o texto inserido em suas bordas.</xref:Microsoft.VisualStudio.Text.SpanTrackingMode> </xref:Microsoft.VisualStudio.Text.SpanTrackingMode> No entanto, se o modo de controle de extensão é <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, uma inserção envia a posição atual em direção ao início e se o modo de controle de span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, uma inserção envia a posição atual no final.</xref:Microsoft.VisualStudio.Text.SpanTrackingMode> </xref:Microsoft.VisualStudio.Text.SpanTrackingMode>  
  
 Você pode obter a posição de um ponto de controle ou o intervalo de um período de controle para qualquer instantâneo do buffer de texto à qual pertencem. Pontos de controle e rastreamento intervalos podem ser consultados com segurança de qualquer thread.  
  
#### <a name="content-types"></a>Tipos de conteúdo  
 Tipos de conteúdo são um mecanismo para definir diferentes tipos de conteúdo. Um tipo de conteúdo pode ser um tipo de arquivo, como "text", "código" ou "binário" ou um tipo de tecnologia, como "xml", "vb" ou "c#". Por exemplo, a palavra "using" é uma palavra-chave em c# e Visual Basic, mas não em outras linguagens de programação. Portanto, a definição da palavra-chave this poderia ser limitada aos tipos de conteúdo "c#" e "vb".  
  
 Tipos de conteúdo são usados como um filtro de adornos e outros elementos do editor. Muitos recursos do editor e pontos de extensão são definidos por tipo de conteúdo. Por exemplo, cor do texto é diferente para arquivos de texto sem formatação, arquivos XML e arquivos de código de origem do Visual Basic. Buffers de texto geralmente são atribuídos a um tipo de conteúdo quando eles são criados e o tipo de conteúdo de um buffer de texto pode ser alterado.  
  
 Tipos de conteúdo podem herdar múltiplo de outros tipos de conteúdo. O <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>permite que você especifique vários tipos de base como pai de um determinado tipo de conteúdo.</xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>  
  
 Os desenvolvedores podem definir seus próprios tipos de conteúdo e registrá-los usando o <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>.</xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> Vários recursos do editor podem ser definidos em relação a um tipo específico de conteúdo usando <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>.</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Por exemplo, margens de editor, ornamentos e manipuladores de mouse podem ser definidos para que eles se aplicam somente a editores que exibem tipos específicos de conteúdo.  
  
###  <a name="a-nametextviewa-the-text-view"></a><a name="textview"></a>A exibição de texto  
 A parte de modo de exibição do modelo exibição controller (MVC) padrão define o modo de exibição de texto, a formatação de exibição, elementos gráficos, como a barra de rolagem e o cursor. Todos os elementos de apresentação do editor do Visual Studio baseiam-se no WPF.  
  
#### <a name="text-views"></a>Modos de exibição de texto  
 O <xref:Microsoft.VisualStudio.Text.Editor.ITextView>interface é uma representação independente da plataforma de uma exibição de texto.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> Ele é usado principalmente para exibir documentos de texto em uma janela, mas ele pode também ser usado para outras finalidades, por exemplo, em uma dica de ferramenta.  
  
 A exibição de texto faz referência a tipos diferentes de buffers de texto. O <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A>propriedade refere-se a uma <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel>objeto que aponta para esses três buffers de texto diferentes: o buffer de dados, que é o buffer de dados de nível superior, o buffer de edição, em que a edição ocorre e o buffer visual, o que é o buffer é exibido no modo de exibição de texto.</xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> </xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A>  
  
 O texto é formatado com base em dos classificadores que estão anexados ao buffer de texto subjacente e marcado por meio de provedores de adorno associadas à exibição de texto em si.  
  
#### <a name="the-text-view-coordinate-system"></a>O sistema de coordenadas de modo de exibição de texto  
 O sistema de coordenadas de modo de exibição de texto Especifica posições na exibição de texto. No sistema de coordenadas, o valor de x 0.0 corresponde à borda esquerda do texto que está sendo exibido e o valor de y 0.0 corresponde a borda superior do texto que está sendo exibido. A coordenada x aumenta da esquerda para a direita e a coordenada y aumenta de cima para baixo.  
  
 Um visor (a parte do texto visível na janela de texto) não pode ser rolado da mesma maneira horizontalmente conforme ele é rolado verticalmente. Um visor é rolado horizontalmente alterando sua coordenada esquerda para que ela se move em relação a superfície de desenho. No entanto, uma porta de visualização pode ser rolada verticalmente apenas alterando o texto processado, o que faz com que um <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>evento a ser gerado.</xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>  
  
 Distâncias no sistema de coordenadas correspondem aos pixels lógicos. Se for exibida a superfície de renderização de texto sem uma transformação de escala, uma unidade de sistema de coordenadas de renderização de texto corresponde a um pixel na tela.  
  
#### <a name="margins"></a>Margens  
 O <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin>interface representa uma margem e habilita o controle da visibilidade da margem e seu tamanho.</xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> Há quatro margens predefinidas, que são nomeadas "Top", "Esquerda", "Right" e "Baixo" e anexadas à parte superior, inferior, esquerda ou borda direita de um modo de exibição. Essas margens são contêineres no qual outras margens podem ser colocadas. A interface define os métodos que retornam o tamanho da margem e a visibilidade de uma margem. As margens são elementos visuais que fornecem informações adicionais sobre o modo de exibição de texto às quais eles estão conectados. Por exemplo, a margem de número de linha exibe números de linha para a exibição de texto. Margem do glifo exibe elementos de interface do usuário.  
  
 O <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>interface trata a criação e o posicionamento das margens.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> Margens podem ser solicitadas em relação a outras margens. Margens de prioridade mais alta são localizadas próximo à exibição de texto. Por exemplo, se há margens esquerdas, margem A e B de margem e margem B tem uma prioridade menor que uma margem, margem B aparece à esquerda da margem A.  
  
#### <a name="the-text-view-host"></a>O Host de exibição de texto  
 O <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>interface contém a exibição de texto e qualquer decorações adjacentes que acompanham o modo de exibição, por exemplo, as barras de rolagem.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> O host de exibição de texto também contém margens que são anexadas a uma borda do modo de exibição.  
  
#### <a name="formatted-text"></a>Texto formatado  
 O texto que é exibido em uma exibição de texto é composto de <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>objetos.</xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> Cada linha da exibição de texto corresponde a uma linha de texto no modo de exibição de texto. Longas linhas no buffer de texto subjacente podem ser parcialmente encobertas (se a quebra de texto não está habilitada) ou divididas em várias linhas de exibição de texto. O <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>interface contém métodos e propriedades para mapeamento entre as coordenadas e caracteres e os adornos que podem ser associados à linha.</xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>objetos são criados usando um <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>interface.</xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource></xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> Se você estiver preocupado apenas com o texto que é exibido atualmente no modo de exibição, você pode ignorar a origem da formatação. Se você estiver interessado em formato de texto que não é exibido no modo de exibição (por exemplo, para dar suporte a um corte de rich text e colar), você pode usar <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>para formatar o texto em um buffer de texto.</xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>  
  
 A exibição de texto formata um <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine>por vez.</xref:Microsoft.VisualStudio.Text.ITextSnapshotLine>  
  
## <a name="editor-features"></a>Recursos do Editor  
 Os recursos do editor são projetados para que a definição do recurso é separada da sua implementação. O editor inclui os seguintes recursos:  
  
-   Marcas e classificadores  
  
-   Adornos  
  
-   Projeção  
  
-   Estrutura de tópicos  
  
-   Associações de mouse e de chave  
  
-   Operações e primitivos  
  
-   IntelliSense  
  
###  <a name="a-nametagsandclassifiersa-tags-and-classifiers"></a><a name="tagsandclassifiers"></a>Marcas e classificadores  
 As marcas são marcadores que estão associados com um intervalo de texto. Podem ser apresentados de maneiras diferentes, por exemplo, usando a cor do texto, sublinhados, gráficos ou pop-ups. Classificadores são um tipo de marca.  
  
 Outros tipos de marcas são <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>para realçar texto, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>para a estrutura de tópicos, e <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>para erros de compilação.</xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> </xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> </xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>  
  
#### <a name="classification-types"></a>Tipos de classificação  
 Um <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>interface representa uma classe de equivalência, que é uma categoria abstrata de texto.</xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> Tipos de classificação podem herdar vários outros tipos de classificação. Por exemplo, a classificações de linguagem de programação pode incluir "palavra-chave", "comentário" e "identificador", que herda de "código". Tipos de classificação de idioma natural podem incluir "substantivo", "verbo" e "adjetivo", que herde "idioma natural".  
  
#### <a name="classifications"></a>Classificações  
 Uma classificação é uma instância de um tipo específico de classificação, normalmente em um intervalo de texto. A <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan>é usada para representar uma classificação.</xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> Uma extensão de classificação pode ser pensada como um rótulo que abrange um determinado intervalo de texto e informa ao sistema que esse intervalo de texto é de um tipo específico de classificação.  
  
#### <a name="classifiers"></a>Classificadores  
 Um <xref:Microsoft.VisualStudio.Text.Classification.IClassifier>é um mecanismo que quebra o texto em um conjunto de classificações.</xref:Microsoft.VisualStudio.Text.Classification.IClassifier> Classificadores devem ser definidos para tipos específicos de conteúdo e instanciadas para buffers de texto específico. Os clientes devem implementar <xref:Microsoft.VisualStudio.Text.Classification.IClassifier>participem de classificação de texto.</xref:Microsoft.VisualStudio.Text.Classification.IClassifier>  
  
#### <a name="classifier-aggregators"></a>Agregadores de classificação  
 Um agregador de classificador é um mecanismo que combina todos os classificadores de buffer de um texto em apenas um conjunto de classificações. Por exemplo, um classificador de c# e uma classificação do idioma inglês pode criar classificações sobre um comentário em um arquivo c#. Considere este comentário:  
  
```  
// This method produces a classifier  
```  
  
 Um classificador c# pode rotular o período inteiro como um comentário e a classificação do idioma inglês pode classificar "produz" como "verbo" e "método" um "substantivo". O agregador produz um conjunto de classificações de não-sobreposição e o tipo do conjunto é baseado em todas as contribuições.  
  
 Um agregador de classificador também é um classificador porque ele quebra o texto em um conjunto de classificações. O agregador de classificador também garante que não há nenhuma sobreposição classificações e que as classificações são classificadas. Classificadores individuais são gratuitos retornar qualquer conjunto de classificações, em qualquer ordem e sobrepostos de qualquer forma.  
  
#### <a name="classification-formatting-and-text-coloring"></a>Cor de texto e formatação de classificação  
 Formatação de texto é um exemplo de um recurso que se baseia em classificação de texto. Ele é usado pela camada de exibição de texto para determinar a exibição do texto em um aplicativo. Depende da área de formatação de texto no WPF, mas a definição lógica de classificação não é.  
  
 Um formato de classificação é um conjunto de propriedades para um tipo de classificação específicas de formatação. Esses formatos herdam o formato do pai do tipo de classificação.  
  
 Um <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>é um mapa de um tipo de classificação para um conjunto de propriedades de formatação de texto.</xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> A implementação do mapa do formato no editor manipula todas as exportações dos formatos de classificação.  
  
###  <a name="a-nameadornmentsa-adornments"></a><a name="adornments"></a>Adornos  
 Adornos são efeitos gráficos que não estão diretamente relacionados a fonte e a cor dos caracteres na exibição de texto. Por exemplo, o sublinhado vermelho rabisco que é usado para marcar o código não compilar em muitas linguagens de programação é um adorno incorporado e dicas de ferramenta são ornamentos pop-up. Adornos são derivados do <xref:System.Windows.UIElement>e implementar <xref:Microsoft.VisualStudio.Text.Tagging.ITag>.</xref:Microsoft.VisualStudio.Text.Tagging.ITag> </xref:System.Windows.UIElement> Dois tipos especializados de marca de adorno são o <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, para adornos que ocupam o mesmo espaço que o texto em uma exibição, e o <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>, para o sublinhado Rabisco.</xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> </xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>  
  
 Adornos incorporados são gráficos que fazem parte do modo de exibição de texto formatado. Eles são organizados em diferentes camadas da ordem Z. Há três camadas internos, como segue: texto, o cursor e a seleção. No entanto, os desenvolvedores podem definir mais camadas e colocá-los na ordem em relação uns dos outros. Os três tipos de adornos incorporados são ornamentos relativos a texto (o qual mover quando move o texto e são excluídos quando o texto é excluído), ornamentos relativos a exibição (que tem a ver com partes não são de texto de exibição) e adornos controlada pelo proprietário (o desenvolvedor deve gerenciar sua colocação).  
  
 Pop-up adornos são gráficos que aparecem em uma pequena janela acima da exibição de texto, por exemplo, as dicas de ferramentas.  
  
###  <a name="a-nameprojectiona-projection"></a><a name="projection"></a>Projeção  
 Projeção é uma técnica para a criação de um tipo diferente de buffer de texto que realmente não armazenar texto, mas em vez disso, combina o texto dos outros buffers de texto. Por exemplo, um buffer de projeção pode ser usado para concatenar o texto dos dois outros buffers e apresentará o resultado como se estivesse em apenas um buffer ou ocultar partes do texto em um buffer. Um buffer de projeção pode agir como um buffer de origem para outro buffer de projeção. Um conjunto de buffers que são relacionados por projeção pode ser construído para reorganizar o texto de várias maneiras diferentes. (Esse conjunto também é conhecido como um *gráfico buffer*.) O recurso de estrutura de tópicos de texto do Visual Studio é implementado por meio de um buffer de projeção para ocultar o texto recolhido e editor do Visual Studio para páginas ASP.NET usa a projeção para dar suporte a idiomas incorporados como Visual Basic e c#.  
  
 Um <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>é criado usando <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>.</xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService> </xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> Um buffer de projeção é representado por uma sequência ordenada de <xref:Microsoft.VisualStudio.Text.ITrackingSpan>objetos que são conhecidos como *intervalos de origem*.</xref:Microsoft.VisualStudio.Text.ITrackingSpan> O conteúdo dessas extensões é apresentado como uma sequência de caracteres. Os buffers de texto na qual os intervalos de origem são desenhados são nomeados *buffers de origem*. Os clientes de um buffer de projeção é preciso estar ciente de que ele difere de um buffer de texto comum.  
  
 O buffer de projeção escuta para eventos de alteração de texto em buffers de origem. Quando o texto em uma fonte abrangem as alterações, o buffer de projeção mapeia as coordenadas de texto alterado para seus próprio coordenadas e gera eventos de alteração de texto apropriado. Por exemplo, considere os buffers de origem A e B com esses conteúdos:  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 Se o buffer de projeção P é formado por dois intervalos de texto, um que tenha todos do buffer de e outros que tem todos os buffers B, P tem o seguinte conteúdo:  
  
```  
P: ABCDEvwxyz  
```  
  
 Se a subcadeia de caracteres `xy` é excluído do buffer B, e o buffer P gera um evento que indica que os caracteres em posições 7 e 8 foram excluídos.  
  
 O buffer de projeção também pode ser editado diretamente. Ele propaga edições para os buffers de origem apropriada. Por exemplo, se uma cadeia de caracteres é inserida no buffer P na posição 6 (a posição original do caractere "v"), a inserção é propagada ao buffer B na posição 1.  
  
 Há restrições sobre os intervalos de origem que contribuem para um buffer de projeção. Não podem se sobrepor os intervalos de origem; um local em um buffer de projeção não é possível mapear mais de um local em qualquer buffer de origem e um local em um buffer de origem não é possível mapear mais de um local em um buffer de projeção. Nenhum circularities são permitidas na relação de buffer de origem.  
  
 Eventos são gerados quando o conjunto de origem buffers para alterações de buffer uma projeção e quando o conjunto de origem contém alterações.  
  
 Um buffer elisão é um tipo especial de buffer de projeção. Ele é usado principalmente para a estrutura de tópicos e operações que expandir e recolher blocos de texto. Um buffer elisão baseia-se em apenas um buffer de origem e as extensões no buffer de elisão devem ser solicitadas a mesma como eles serão ordenados no buffer de origem.  
  
##### <a name="the-buffer-graph"></a>O gráfico de Buffer  
 O <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>interface permite o mapeamento em um gráfico de buffers de projeção.</xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> Todos os buffers de texto e buffers de projeção são coletados em um gráfico acíclico direcionado, bem como a árvore de sintaxe abstrata que é produzido por um compilador de linguagem. O gráfico é definido pelo buffer de superior, que pode ser qualquer buffer de texto. O gráfico de buffer pode mapear de um ponto no buffer superior a um ponto em um buffer de origem ou de uma extensão do buffer superior a um conjunto de extensões em um buffer de origem. Da mesma forma, ele pode mapear um ponto ou variam de um buffer de origem para um ponto no buffer superior. Gráficos de buffer são criados usando o <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>.</xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>  
  
##### <a name="events-and-projection-buffers"></a>Eventos e Buffers de projeção  
 Quando um buffer de projeção é modificado, as modificações são enviadas do buffer de projeção para os buffers que dependem dele. Depois que todos os buffers são modificados, são gerados eventos de alteração de buffer, começando com o buffer de nível mais profundo.  
  
###  <a name="a-nameoutlininga-outlining"></a><a name="outlining"></a>Estrutura de tópicos  
 Estrutura de tópicos é a capacidade de expandir ou recolher blocos de texto em uma exibição de texto diferentes. Estrutura de tópicos é definida como um tipo de <xref:Microsoft.VisualStudio.Text.Tagging.ITag>, da mesma maneira que adornos são definidos.</xref:Microsoft.VisualStudio.Text.Tagging.ITag> A <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>é uma marca que define uma região de texto que pode ser expandida ou recolhida.</xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> Para usar a estrutura de tópicos, você deve importar a <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>obter um <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>.</xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> </xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> O Gerenciador de estrutura de tópicos enumera, recolhe e expande os blocos distintos, que são representados como <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible>objetos e gera eventos adequadamente.</xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible>  
  
###  <a name="a-namemousebindingsa-mouse-bindings"></a><a name="mousebindings"></a>Associações de mouse  
 Associações de mouse vinculam os movimentos do mouse a comandos diferentes. Mouse associações são definidas usando um <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>, e as associações de teclas são definidas usando um <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>.</xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider> </xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> O <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>automaticamente cria uma instância de todas as associações e conecta-se para eventos de mouse no modo de exibição.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>  
  
 O <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor>interface contém manipuladores de eventos de pré-processamento e pós-processamento para eventos de mouse diferente.</xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> Para lidar com um dos eventos, você pode substituir alguns dos métodos no <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>.</xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>  
  
###  <a name="a-nameeditoroperationsa-editor-operations"></a><a name="editoroperations"></a>Operações do Editor  
 Operações do Editor podem ser usadas para automatizar a interação com o editor de scripts ou outras finalidades. Você pode importar o <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>para acessar operações em um determinado <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> Em seguida, você pode usar esses objetos para modificar a seleção, role a exibição ou mover o cursor para diferentes partes da exibição.  
  
###  <a name="a-nameintellisensea-intellisense"></a><a name="intellisense"></a>IntelliSense  
 Oferece suporte a IntelliSense, conclusão de instrução, ajuda de assinatura (também conhecido como informações de parâmetro), informações rápidas e lâmpadas.  
  
 Conclusão de instrução fornece listas pop-up de conclusões possíveis para nomes de método, elementos XML e outros elementos de código ou marcação. Em geral, um gesto do usuário invoca uma sessão de conclusão. A sessão exibe a lista de possíveis conclusões e o usuário pode selecionar um ou descartar a lista. O que <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>é responsável por criar e disparar o <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.</xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession> </xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> O <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>computa o <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet>de itens de conclusão para a sessão.</xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> </xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
## <a name="see-also"></a>Consulte também  
 [Serviço de linguagem e pontos de extensão de Editor](../extensibility/language-service-and-editor-extension-points.md)   
 [Editor de importações](../extensibility/editor-imports.md)
