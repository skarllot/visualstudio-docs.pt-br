---
title: "Instru&#231;&#245;es passo a passo: capturando informa&#231;&#245;es de gr&#225;fico de forma program&#225;tica | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5adeff9-afaf-4047-b5ce-ef0aefe710eb
caps.latest.revision: 21
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Instru&#231;&#245;es passo a passo: capturando informa&#231;&#245;es de gr&#225;fico de forma program&#225;tica
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Diagnóstico de gráficos para capturar informações gráficas de um aplicativo Direct3D de forma programática.  
  
 Captura programática é útil em cenários como:  
  
-   Iniciar captura programaticamente quando seu aplicativo de elementos gráficos não use swapchain presente, como quando ele processa uma textura.  
  
-   Iniciar captura programaticamente quando seu aplicativo não seja processada, como quando ele usa DirectCompute para executar cálculos.  
  
-   Chamar `CaptureCurrentFrame`quando um problema de renderização é difícil de prever e capturar em testes manuais, mas pode ser programaticamente previsto usando informações sobre o estado do aplicativo em tempo de execução.  
  
##  <a name="CaptureDX11_2"></a> Captura programática no Windows 8.1  
 Esta parte do passo a passo demonstra a captura programática em aplicativos que usam a API DirectX 11.2 no Windows 8.1, que usa o método de captura robusta. Para obter informações sobre como usar a captura programática em aplicativos que usam versões anteriores do DirectX em Windows 8.0, consulte [Captura programática no Windows 8.0 e versões anteriores](#CaptureDX11_1) posteriormente neste passo a passo.  
  
 Esta seção mostra como executar essas tarefas:  
  
-   Preparando seu aplicativo para usar a captura programática  
  
-   Obtendo a interface IDXGraphicsAnalysis  
  
-   Capturando informações de gráficos  
  
> [!NOTE]
>  As implementações anteriores da Captura programática dependiam das ferramentas remotas para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para fornecer a funcionalidade de captura, o Windows 8.1 dá suporte à captura diretamente por meio do Direct3D 11.2. Como resultado, você não precisa instalar as ferramentas remotas para a captura programática no Windows 8.1.  
  
### Preparando seu aplicativo para usar a captura programática  
 Para usar a captura programática em seu aplicativo, ele deve incluir os cabeçalhos necessários. Esses cabeçalhos são parte do SDK do Windows 8.1.  
  
##### Para incluir cabeçalhos de captura programática  
  
-   Inclua estes cabeçalhos no arquivo de origem em que você irá definir a interface IDXGraphicsAnalysis:  
  
    ```  
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    >  Não inclua o arquivo de cabeçalho vsgcapture. h— que dá suporte à captura programática no Windows 8.0 e versões anteriores — para realizar a captura programática em seus aplicativos do Windows 8.1. Esse cabeçalho é incompatível com o DirectX 11.2. Se esse arquivo é incluído após o d3d11\_2.h cabeçalho for incluído, o compilador emite um aviso. Se vsgcapture. h incluído antes d3d11\_2.h, o aplicativo não será iniciado.  
  
    > [!NOTE]
    >  Se a junho de 2010 DirectX SDK está instalado em seu computador e o caminho de inclusão do projeto contém `%DXSDK_DIR%include\x86`, movê\-lo para o final do caminho de inclusão. Faça o mesmo para o caminho da biblioteca.  
  
#### Windows Phone 8,1  
 Como o SDK do Windows Phone 8.1 não inclui o DXProgrammableCapture.h cabeçalho, você precisará definir o `IDXGraphicsAnalysis` interface por conta própria, para que você possa usar o `BeginCapture()` e `EndCapture()` métodos. Inclua os outros cabeçalhos conforme descrito na seção anterior.  
  
###### Para definir a interface IDXGraphicsAnalysis  
  
-   Defina a interface IDXGraphicsAnalysis no mesmo arquivo em que você incluiu os arquivos de cabeçalho.  
  
    ```  
    interface DECLSPEC_UUID("9f251514-9d4d-4902-9d60-18988ab7d4b5") DECLSPEC_NOVTABLE  
    IDXGraphicsAnalysis : public IUnknown  
    {  
        STDMETHOD_(void, BeginCapture)() PURE;  
        STDMETHOD_(void, EndCapture)() PURE;  
    };  
    ```  
  
 Para sua conveniência, você pode executar essas etapas em um novo arquivo de cabeçalho e, em seguida, incluí\-lo onde for necessário em seu aplicativo.  
  
### Obtendo a interface IDXGraphicsAnalysis  
 Antes de capturar informações de gráficos do DirectX 11.2, você precisa obter a interface de depuração DXGI.  
  
> [!IMPORTANT]
>  Ao usar a captura programática, você ainda deve executar seu aplicativo em Diagnóstico de gráficos \(Alt \+ F5 no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\) ou o [Ferramenta de captura de linha de comando](../debugger/command-line-capture-tool.md).  
  
##### Para obter a interface IDXGraphicsAnalysis  
  
-   Use o seguinte código para ligar a interface IDXGraphicsAnalysis à interface de depuração DXGI.  
  
    ```  
    IDXGraphicsAnalysis* pGraphicsAnalysis;  
    HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));  
    ```  
  
     Verifique o `HRESULT` retornado por `DXGIGetDebugInterface1` para garantir que você tenha uma interface válida antes de você usá\-lo:  
  
    ```  
    if (FAILED(getAnalysis))  
    {  
        // Abort program or disable programmatic capture in your app.  
    }  
    ```  
  
    > [!NOTE]
    >  Se `DXGIGetDebugInterface1` retorna `E_NOINTERFACE` \(`erro: E_NOINTERFACE sem suporte para essa interface`\), verifique se o aplicativo estiver em execução no diagnóstico de gráficos \(Alt \+ F5 no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\).  
  
### Capturando informações de gráficos  
 Agora que você tem uma validade `IDXGraphicsAnalysis` interface, você pode usar `BeginCapture` e `EndCapture` para capturar informações gráficas.  
  
##### Para capturar informações gráficas  
  
-   Para começar a capturar informações gráficas, use `BeginCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->BeginCapture();  
    ...  
    ```  
  
     Captura começa imediatamente quando `BeginCapture` é chamado; ele não espera até que o próximo quadro começar. Captura para quando o quadro atual é apresentado, ou quando você chamar `EndCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->EndCapture();  
    ...  
    ```  
  
##  <a name="CaptureDX11_1"></a> Captura programática no Windows 8.0 e versões anteriores  
 Nesta parte do passo a passo demonstra a captura programática em aplicativos para Windows 8.0 e versões anteriores que usam a API do DirectX 11.1, que usa o método de captura herdado. Para obter informações sobre como usar a captura programática em aplicativos que usam o DirectX 11.2 no Windows 8.1, consulte [Captura programática no Windows 8.1](#CaptureDX11_2) anterior neste passo a passo.  
  
 Esta parte mostra estas tarefas:  
  
-   Preparando o computador para usar a captura programática  
  
-   Preparando seu aplicativo para usar a captura programática  
  
-   Configurando o nome e o local do arquivo de log de gráficos  
  
-   Usando o `CaptureCurrentFrame` API  
  
### Preparando o computador para usar a captura programática  
 A API de captura programática usa as ferramentas remotas para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para fornecer a funcionalidade de captura. O computador onde o aplicativo será executado deve ter as ferramentas remotas instaladas, mesmo quando você estiver usando a captura programática em seu computador local.[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] não precisa estar em execução quando você realiza a captura programática em um computador local.  
  
 Para usar os APIs de captura remota em um aplicativo que está sendo executado em um computador, primeiro você precisa instalar as ferramentas remotas para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no computador. Diferentes versões das ferramentas remotas dão suporte a plataformas de hardware diferentes. Para obter informações sobre como instalar as ferramentas remotas, consulte o [página de download de ferramentas remotas](http://go.microsoft.com/fwlink/p/?LinkId=246691) site de downloads da Microsoft.  
  
 Como alternativa, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instala os componentes necessários para realizar a captura remota para aplicativos de 32 bits.  
  
> [!NOTE]
>  Porque a maioria dos aplicativos de área de trabalho do Windows — incluindo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]— não têm suporte em [!INCLUDE[win8](../debugger/includes/win8_md.md)] para dispositivos ARM, usando ferramentas remotas para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] junto com a captura programática API é a única maneira de capturar o diagnóstico de gráficos em dispositivos ARM.  
  
### Preparando seu aplicativo para usar a captura programática  
 Para usar as ferramentas de diagnóstico de gráficos, primeiro você precisa capturar as informações de gráficos que ele depende. Você pode capturar de forma programática as informações usando o `CaptureCurrentFrame` API.  
  
##### Para preparar seu aplicativo para capturar informações gráficas de forma programática  
  
1.  Verifique se o `vsgcapture.h` cabeçalho está incluído no código\-fonte para o aplicativo. Ele pode ser incluído em apenas um único local — por exemplo, no arquivo de código onde você chamará a programação captura API — ou em um arquivo de cabeçalho pré\-compilado para chamar a API de fonte de vários arquivos de código.  
  
2.  No código\-fonte para o aplicativo, sempre que você deseja capturar o restante do quadro atual, chame `g_pVsgDbg->CaptureCurrentFrame()`. Esse método não usa nenhum parâmetro e não retorna um valor.  
  
### Configurando o nome e o local do arquivo de log de gráficos  
 O log de gráficos é criado no local que é definido pelo `DONT_SAVE_VSGLOG_TO_TEMP` e `VSG_DEFAULT_RUN_FILENAME` macros.  
  
##### Para configurar o nome e o local do arquivo de log de gráficos  
  
-   Para impedir que o log de gráficos sejam gravados para o diretório temporário, antes de `#include <vsgcapture.h>` linha, adicione isso:  
  
    ```  
    #define DONT_SAVE_VSGLOG_TO_TEMP  
    ```  
  
     Você pode definir esse valor para gravar o log de gráficos para um local relativo no diretório de trabalho ou em um caminho absoluto se a definição de `VSG_DEFAULT_RUN_FILENAME` é um caminho absoluto.  
  
-   Para salvar o log de gráficos para um local diferente ou dar a ele um nome de arquivo diferente antes de `#include <vsgcapture.h>` linha, adicione isso:  
  
    ```  
    #define VSG_DEFAULT_RUN_FILENAME <filename>  
    ```  
  
     Se você não executar essa etapa, o nome do arquivo é vsglog. Se você não definiu `DONT_SAVE_VSGLOG_TO_TEMP`, em seguida, o local do arquivo é relativo ao diretório temp; caso contrário, ele é relativo ao diretório de trabalho ou em outro local se você tiver especificado um nome de arquivo absoluto.  
  
 Para [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicativos, o local do diretório temporário é específico para cada usuário e o aplicativo e geralmente é encontrado em um local como C:\\users\\*nome de usuário*\\AppData\\Local\\Packages\\*nome de família de pacote*\\tempstate\\.. Para aplicativos de desktop, o local do diretório temporário é específico para cada usuário e geralmente é encontrado em um local como C:\\Users\\*nome de usuário*\\appdata\\local\\temp\\..  
  
> [!NOTE]
>  Para gravar em um local específico, você deve ter permissões para gravar nesse local; Caso contrário, ocorrerá um erro. Tenha em mente que [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicativos são mais restritos do que os aplicativos de desktop sobre onde eles podem gravar dados e podem exigir configuração adicional para gravação em determinados locais.  
  
### Capturando as informações gráficas  
 Após ter preparado o aplicativo para Captura programática e, opcionalmente, configurado o local e o nome dos gráficos de arquivo de log, compilar o aplicativo e, em seguida, executar ou depurar para capturar dados; não iniciar o diagnóstico de gráficos [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] quando você usa a API de captura programática. O log de gráficos é gravado no local especificado. Se você quiser manter essa versão do log, movê\-lo para outro local. Caso contrário, ele será substituído quando você executa o aplicativo novamente.  
  
> [!TIP]
>  Você ainda possa capturar informações gráficas manualmente enquanto você estiver usando a captura programática — com o aplicativo no foco, basta pressionar **Print Screen**. Você pode usar essa técnica para capturar informações gráficas adicionais não são capturadas pela API de captura programática.  
  
## Próximas etapas  
 Este passo a passo demonstrou como capturar informações gráficas de forma programática. Como uma próxima etapa, considere esta opção:  
  
-   Aprenda a analisar informações gráficas capturadas usando as ferramentas de diagnóstico de gráficos. Consulte [Visão Geral](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## Consulte também  
 [Passo a passo: capturando informações de gráficos](../debugger/walkthrough-capturing-graphics-information.md)   
 [Capturando informações de gráficos](../debugger/capturing-graphics-information.md)   
 [Ferramenta de captura de linha de comando](../debugger/command-line-capture-tool.md)