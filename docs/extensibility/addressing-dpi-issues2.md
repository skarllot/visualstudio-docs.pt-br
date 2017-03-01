---
title: "Endereçamento de DPI Problemas2 | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
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
ms.openlocfilehash: 1a2466ba548758ae119ea768d1c208d2b2ad9684
ms.lasthandoff: 02/22/2017

---
# <a name="addressing-dpi-issues"></a>Questões de DPI
Um número crescente de dispositivos é de envio com telas "alta resolução". Essas telas normalmente têm mais de 200 pixels por polegada (ppi). Trabalhar com um aplicativo nesses computadores exigirá o conteúdo a ser dimensionado para atender às necessidades de exibir o conteúdo em uma distância de exibição normal para o dispositivo. A partir de 2014, o principal alvo para monitores de alta densidade é (tablets, laptops clamshell e telefones) de dispositivos de computação móvel.  
  
 Windows 8.1 e posterior contém vários recursos para habilitar esses computadores trabalhar com exibições e ambientes em que a máquina está conectada à alta densidade e densidade padrão exibe ao mesmo tempo.  
  
-   Windows podem permitir que você a ajustar o conteúdo para o dispositivo usando o "Tornar texto e outros itens maiores ou menores" configuração (disponível desde o Windows XP).  
  
-   Windows 8.1 e mais alta será dimensionado automaticamente conteúdo para a maioria dos aplicativos ser consistente quando movidos entre exibições de diferentes densidades de pixels. Quando o vídeo principal é alta densidade (200% dimensionamento) e a exibição secundária é a densidade padrão (100%), Windows será automaticamente reduzido o conteúdo da janela de aplicativo na exibição secundária (1 pixel exibido para cada 4 pixels processados pelo aplicativo).  
  
-   Windows padrão será o direito de dimensionamento para a densidade de pixels e exibindo distância para a exibição (Windows 7 e posteriores, OEM configurável).  
  
-   Windows pode dimensionar automaticamente conteúdo a 250% em novos dispositivos que excedem 280 ppi (a partir do Windows 8.1 S14).  
  
 O Windows tem uma maneira de lidar com o aumento de interface do usuário para tirar proveito das contagens de pixel maior. Um aplicativo aceita esse sistema declarando próprio "system com reconhecimento de DPI". Aplicativos que não fazem isso são aumentados pelo sistema. Isso pode resultar em uma experiência de usuário "difusa" onde o aplicativo inteiro é alongado uniformemente pixel. Por exemplo:  
  
 ![Problemas de DPI difusa](../extensibility/media/dpi-issues-fuzzy.png "DPI emite difusa")  
  
 Visual Studio aceita sendo compatível com dimensionamento de DPI e, portanto, não está "virtualizado."  
  
 Windows (e o Visual Studio) aproveitam várias tecnologias de interface do usuário, que têm diferentes maneiras de lidar com o dimensionamento fatores definidos pelo sistema. Por exemplo:  
  
-   WPF mede os controles de forma independente de dispositivo (unidades, não em pixels). WPF UI dimensiona automaticamente para o DPI atual.  
  
-   Todos os tamanhos de texto, independentemente da estrutura de interface do usuário são expressos em pontos e então são tratados pelo sistema como independentes de DPI. Texto no Win32, WinForms e WPF já dimensionar corretamente quando desenhado para o dispositivo de vídeo.  
  
-   Janelas e caixas de diálogo do Win32/WinForms tem meios para habilitar o layout é redimensionado com texto – por exemplo, a grade, fluxo e painéis de layout de tabela. Eles permitem evitar locais de pixel embutidos que não são dimensionados quando os tamanhos de fonte são aumentados.  
  
-   Ícones fornecidos pelo sistema ou recursos com base nas métricas de sistema (por exemplo, SM_CXICON e SM_CXSMICON) já estão dimensionados para cima.  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Win32 mais antigos (GDI, GDI+) e a interface do usuário baseada em WinForms  
 Embora o WPF já estiver reconhecimento de DPI alto, grande parte do nosso código baseado em Win32/GDI não foi gravado originalmente com reconhecimento de DPI em mente. Windows fornece APIs de dimensionamento de DPI. Correções para problemas de Win32 devem usá-las consistentemente em todo o produto. Visual Studio forneceu um auxiliar de biblioteca de classes para evitar duplicação de funcionalidade e garantir a consistência em todo o produto.  
  
## <a name="high-resolution-images"></a>Imagens de alta resolução  
 Esta seção é usada principalmente para os desenvolvedores estender o Visual Studio 2013. Para Visual Studio 2015, use o serviço de imagem que está incorporado ao Visual Studio. Você também pode encontrar o que você precisa de suporte/destino muitas versões do Visual Studio e, portanto, usando o serviço de imagem em 2015 não é uma opção pois ela não existe nas versões anteriores. Esta seção é também, em seguida, para você.  
  
## <a name="scaling-up-images-that-are-too-small"></a>Dimensionamento de imagens que são muito pequenas  
 Imagens que estão muito pequenas podem ser "dimensionadas para cima" e processadas GDI e WPF usando alguns métodos comuns. Classes de auxiliar DPI gerenciadas estão disponíveis para integradores de Visual Studio internos e externos para endereço dimensionamento ícones, bitmaps, imagestrips e imagelists. Baseado no Win32 nativo C / C + + auxiliares estão disponíveis para dimensionamento HICON, HBITMAP, HIMAGELIST e VsUI::GdiplusImage. Dimensionamento de um bitmap normalmente requer apenas uma alteração de uma linha depois de incluir uma referência à biblioteca do auxiliar. Por exemplo:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```c#  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Dimensionar um imagelist depende imagelist for concluída no tempo de carregamento, ou é acrescentado em tempo de execução. Se for concluída no tempo de carregamento, chame LogicalToDeviceUnits() com imagelist como faria com um bitmap. Quando o código precisa carregar um bitmap individual antes de composição imagelist, certifique-se de dimensionar o tamanho da imagem de imagelist:  
  
```c#  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 No código nativo, as dimensões podem ser dimensionadas ao criar imagelist da seguinte maneira:  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 Funções na biblioteca permitem especificar o algoritmo de redimensionamento. Quando imagens dimensionamento sejam colocados em imagelists, certifique-se de especificar a cor de plano de fundo que é usada para a transparência, ou usar o dimensionamento de NearestNeighbor (que fará com que as distorções 125% e 150%).  
  
 Consulte o <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper>documentação no MSDN.</xref:Microsoft.VisualStudio.PlatformUI.DpiHelper>  
  
 A tabela a seguir mostra exemplos de como as imagens devem ser dimensionadas em DPI correspondente fatores de dimensionamento. As imagens em verde indicam nossa prática recomendada a partir do Visual Studio 2013 (100 a 200% dimensionamento de DPI):  
  
 ![Problemas DPI dimensionamento](../extensibility/media/dpi-issues-scaling.png "problemas DPI dimensionamento")  
  
## <a name="layout-issues"></a>Problemas de layout  
 Problemas comuns de layout podem ser evitados principalmente mantendo pontos na interface do usuário dimensionado e relação uns aos outros em vez de usar locais absolutos (especificamente, em unidades de pixels). Por exemplo:  
  
-   Posições de texto do layout precisam ajustar a conta para imagens expandidos.  
  
-   Colunas em grades precisam ter larguras ajustadas para o texto expandidos.  
  
-   Tamanhos embutidos ou espaço entre elementos também precisará ser dimensionado. Tamanhos com base apenas nas dimensões de texto são normalmente bem, porque as fontes são automaticamente ajustadas.  
  
 Funções de auxiliar estão disponíveis na <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper>classe para permitir dimensionamento no eixo X e Y:</xref:Microsoft.VisualStudio.PlatformUI.DpiHelper>  
  
-   LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (funções permitem o dimensionamento de X / eixo Y)  
  
-   int espaço = DpiHelper.LogicalToDeviceUnitsX (10);  
  
-   int height = VsUI::DpiHelper::LogicalToDeviceUnitsY(5);  
  
 Há sobrecargas de LogicalToDeviceUnits para permitir o dimensionamento de objetos, como Rect, ponto e tamanho.  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Usando a biblioteca DPIHelper/classe para dimensionar as imagens e o layout  
 A biblioteca do auxiliar de DPI do Visual Studio está disponível em formulários nativos e gerenciados e pode ser usada fora do shell do Visual Studio por outros aplicativos.  
  
 Para usar a biblioteca, vá para o [exemplos de extensibilidade do Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) e clonar o exemplo de alto-DPI_Images_Icons  
  
 Em arquivos de origem incluem VsUIDpiHelper.h e chamar as funções estáticas da classe VsUI::DpiHelper:  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  Não use as funções auxiliares em nível de módulo ou classe variáveis estáticas. A biblioteca também usa estatísticas para sincronização de threads e você pode enfrentar problemas de ordem de inicialização. Converta essas estatísticas para variáveis de membro não estáticos, ou encapsulá-los em uma função (de modo que eles obtenham construídos no primeiro acesso).  
  
 Para acessar as funções do auxiliar DPI de código gerenciado será executado dentro do ambiente do Visual Studio:  
  
-   O projeto consumidor deve referenciar a versão mais recente do MPF de Shell. Por exemplo:  
  
    ```c#  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   Certifique-se de que o projeto tem referências a **System.Windows.Forms**, **PresentationCore**, e **PresentationUI**.  
  
-   No código, use o **Microsoft.VisualStudio.PlatformUI** namespace e chamar funções estáticas da classe DpiHelper. Para tipos com suporte (pontos, tamanhos, retângulos e assim por diante), existem desde expandido de funções de extensão que retornam novos objetos. Por exemplo:  
  
    ```c#  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Lidando com grau de seleção de imagem WPF na interface do usuário zoom  
 No WPF, bitmaps são redimensionados automaticamente pelo WPF para o nível de zoom atual DPI usando um algoritmo de alta qualidade bicúbica (padrão), que funciona bem para imagens ou capturas de tela grande, mas não é apropriado para os ícones de item de menu porque ela introduz o grau de seleção percebido.  
  
 Recomendações:  
  
-   Para arte de imagem e faixas logotipo, o padrão <xref:System.Windows.Media.BitmapScalingMode>modo de redimensionamento poderia ser usado.</xref:System.Windows.Media.BitmapScalingMode>  
  
-   Para itens de menu e imagens iconografia, o <xref:System.Windows.Media.BitmapScalingMode>deve ser usado quando ele não faz outros artefatos de distorção eliminar o grau de seleção (no % 200 e 300%).</xref:System.Windows.Media.BitmapScalingMode>  
  
-   • Para zoom grande níveis não múltiplos de 100% (por exemplo, 250% ou % de 350), dimensionando imagens iconografia com resultados bicúbica no difusa e Desbotado da interface do usuário. Um resultado melhor é obtido pela primeira dimensionar a imagem com NearestNeighbor para o múltiplo maior de 100% (por exemplo, 200% ou 300%) e dimensionamento com bicúbica dali. Consulte o caso especial: prescaling imagens do WPF para DPI grande níveis para obter mais informações.  
  
 A classe DpiHelper no namespace Microsoft.VisualStudio.PlatformUI fornece um membro <xref:System.Windows.Media.BitmapScalingMode>que pode ser usado para associação.</xref:System.Windows.Media.BitmapScalingMode> Ele permitirá que o shell do Visual Studio controlar o modo de dimensionamento em todo o produto uniformemente, dependendo do fator de dimensionamento de DPI de bitmap.  
  
 Para usá-lo em XAML, adicione:  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Já o shell do Visual Studio define essa propriedade em caixas de diálogo e janelas de nível superior. Interface de usuário baseada no WPF em execução no Visual Studio já será herdá-la. Se a configuração não propaga as partes específicas da interface do usuário, ele poderá ser definido no elemento raiz da interface do usuário/WPF XAML. Locais em que isso ocorre incluem pop-ups em elementos com os pais do Win32, e as janelas de designer de processam, como o Blend.  
  
 Algumas interfaces do usuário podem dimensionar independentemente do nível de zoom DPI de conjunto de sistema, como o editor de texto do Visual Studio e designers baseado no WPF (WPF de área de trabalho e da Windows Store). Nesses casos, DpiHelper.BitmapScalingMode não deve ser usado. Para corrigir esse problema no editor, a equipe IDE criada uma propriedade personalizada chamada RenderOptions.BitmapScalingMode. Defina o valor da propriedade HighQuality ou NearestNeighbor dependendo do nível de zoom combinados do sistema e a interface do usuário.  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Caso especial: prescaling imagens do WPF para níveis DPI grande  
 Para níveis de zoom muito grandes que não sejam múltiplos de 100% (por exemplo, 250%, 350% e assim por diante), dimensionando imagens de iconografia com resultados bicúbica na interface do usuário e Desbotado. A impressão dessas imagens ao lado do texto é praticamente o mesmo que uma ilusão ótica. As imagens parecem ser mais próxima ao olho e fora de foco em relação ao texto. O resultado de dimensionamento nesse tamanho ampliada pode ser melhorado, dimensionar a imagem com NearestNeighbor para o múltiplo maior de 100% (por exemplo, 200% ou 300%) e dimensionamento com bicúbica no restante (um adicional % de 50).  
  
 Este é um exemplo das diferenças nos resultados, onde a primeira imagem é dimensionada com o maior dimensionamento duplo algoritmo 100%-> 200%-> 250%, e o outro com o Bicúbico 100%-> 250%.  
  
 ![DPI emite exemplo de escala Double](../extensibility/media/dpi-issues-double-scaling-example.png "DPI emite duplo exemplo de escala")  
  
 Para habilitar a interface do usuário usar esse dimensionamento duplo, a marcação XAML para exibir cada elemento de imagem precisa ser modificado. Os exemplos a seguir demonstram como usar o dimensionamento dupla no WPF no Visual Studio usando a biblioteca de DpiHelper e Shell.12/14.  
  
 Etapa 1: Prescale a imagem para 200%, 300% e assim por diante usando NearestNeighbor.  
  
 Prescale a imagem usando qualquer um conversor aplicado em uma associação, ou com uma extensão de marcação XAML. Por exemplo:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 Se a imagem também precisa ter temas (a maioria, se não todos, deve), a marcação pode usar um conversor de diferente que primeiro temas da imagem e, em seguida, o dimensionamento previamente. A marcação pode usar <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter>ou <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>, dependendo da saída de conversão desejada.</xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter> </xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter>  
  
```xaml  
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />  
  
<Image Width="16" Height="16">  
  <Image.Source>  
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">  
      <Binding Path="Icon" />  
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"    
               RelativeSource="{RelativeSource Self}" />  
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />  
    </MultiBinding>  
  </Image.Source>  
</Image>  
```  
  
 Etapa 2: Verifique o tamanho final está correto para o DPI atual.  
  
 Como o WPF dimensionará a interface do usuário para o DPI atual usando a propriedade BitmapScalingMode definir o UIElement, um controle de imagem usando uma imagem prescaled como sua fonte aparecerá duas ou três vezes maior do que ele deve. A seguir estão algumas maneiras de combater esse efeito:  
  
-   Se você souber a dimensão da imagem original em 100%, você pode especificar o tamanho exato do controle de imagem. Esses tamanhos refletirá que o tamanho da interface do usuário antes de dimensionamento é aplicado.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   Se o tamanho da imagem original não for conhecido, um LayoutTransform pode ser usado para dimensionar o objeto de imagem final. Por exemplo:  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## <a name="enabling-hdpi-support-to-the-weboc"></a>Habilitando o suporte a HDPI para o WebOC  
 Por padrão, controles de WebOC (como o controle WebBrowser no WPF, ou a interface IWebBrowser2) não habilitam a detecção de HDPI e suporte. O resultado será um controle inserido com o conteúdo de vídeo que é muito pequeno em uma tela de alta resolução. O seguinte descreve como habilitar o suporte de DPI alto em uma instância de WebOC web específico.  
  
 Implementar a interface IDocHostUIHandler (consulte o artigo do MSDN sobre o [IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx) interface):  
  
```idl  
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]  
public interface IDocHostUIHandler  
{  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowContextMenu(  
        [In, MarshalAs(UnmanagedType.U4)] int dwID,  
        [In] POINT pt,  
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,  
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowUI(  
        [In, MarshalAs(UnmanagedType.I4)] int dwID,  
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,  
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,  
        [In, MarshalAs(UnmanagedType.Interface)] object frame,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int HideUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int UpdateUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ResizeBorder(  
        [In] COMRECT rect,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc,  
        bool fFrameWindow);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateAccelerator(  
        [In] ref MSG msg,  
        [In] ref Guid group,  
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetOptionKeyPath(  
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,  
        [In, MarshalAs(UnmanagedType.U4)] int dw);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetDropTarget(  
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,  
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateUrl(  
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,  
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,  
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int FilterDataObject(  
        IDataObject pDO,  
        out IDataObject ppDORet);  
    }   
```  
  
 Opcionalmente, implemente a interface ICustomDoc (consulte o artigo do MSDN sobre o [ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx) interface):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 Associe a classe que implementa IDocHostUIHandler com documentos do WebOC. Se você implementou a interface ICustomDoc acima, como propriedade de documento do WebOC é válida, convertê-lo em um ICustomDoc e chamar o método SetUIHandler, passando a classe que implementa IDocHostUIHandler.  
  
```c#  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 Se você não implementou a interface ICustomDoc, em seguida, assim que a propriedade de documento do WebOC é válida, você precisará convertê-lo para um IOleObject e chamar o método SetClientSite, transmitindo a classe que implementa IDocHostUIHandler. Defina o sinalizador DOCHOSTUIFLAG_DPI_AWARE no DOCHOSTUIINFO passado para a chamada do método do GetHostInfo:  
  
```c#  
public int GetHostInfo(DOCHOSTUIINFO info)  
{  
    // This is what the default site provides.  
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;  
    // Add the DPI flag to the defaults  
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;  
    return S_OK;  
}  
```  
  
 Isso deve ser tudo o que você precisa obter o controle WebOC para oferecer suporte a HPDI.  
  
## <a name="tips"></a>Dicas  
  
1.  Se a propriedade de documento no controle WebOC for alterado, talvez seja necessário reassociar o documento com a classe IDocHostUIHandler.  
  
2.  Se os itens acima não funcionar, há um problema conhecido com o WebOC não pegar a alteração para o sinalizador DPI. A maneira mais confiável de corrigir isso é alternar o zoom ótico do WebOC duas chamadas de significado com dois valores diferentes para a porcentagem de zoom. Além disso, se essa solução alternativa é necessária, pode ser necessário para executá-lo em cada chamada de navegar.  
  
    ```c#  
    // browser2 is a SHDocVw.IWebBrowser2 in this case  
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values  
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;  
    if (cmdTarget != null)  
    {  
        object commandInput = zoomPercent;  
        cmdTarget.Exec(IntPtr.Zero,  
                       OLECMDID_OPTICAL_ZOOM,  
                       OLECMDEXECOPT_DONTPROMPTUSER,  
                       ref commandInput,  
                       ref commandOutput);  
    }  
    ```
