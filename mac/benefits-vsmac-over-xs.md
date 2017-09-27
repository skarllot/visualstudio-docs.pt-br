---
title: "Benefícios do Visual Studio para Mac em relação ao Xamarin Studio"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 6ACF5FD4-D5C1-4050-95E3-467C753F25F1
ms.translationtype: HT
ms.sourcegitcommit: f6c7e290f0abc2c32456e076420a7695ae868ba6
ms.openlocfilehash: 655795fd64958805e0137d7e231391c59f676776
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---

# <a name="benefits-of-visual-studio-for-mac-over-xamarin-studio"></a>Benefícios do Visual Studio para Mac em relação ao Xamarin Studio 
 
O Visual Studio para Mac substituiu o Xamarin Studio como um IDE completo no Mac. Ele fornece recursos que permitem desenvolver aplicativos Web e serviços, aplicativos de plataforma cruzada móveis e de área de trabalho e jogos. Além disso, ele torna a integração com o Azure muito fácil, seja para publicar no Azure ou criar no Azure Functions. Ele tem tudo o que você esperaria de um IDE moderno, incluindo um editor de código-fonte completo, um depurador poderoso, um espaço de trabalho personalizável, integração com o GIT e um sistema avançado de extensão, todos projetados nativamente para o Mac. 

Outros recursos incluem: 

* IntelliSense de C# baseado em Roslyn, refatoração, analisadores e correções de código 
* Gerenciamento de pacotes baseado em NuGet 
* Formato de projeto compatível com o Visual Studio 
* Mecanismo de build do MSBuild 
* Teste de unidade integrado 
* Suporte imediato para F# 

Os benefícios listados neste guia indicados como **Versão prévia** só estão disponíveis no [Canal alfa](https://docs.microsoft.com/en-us/visualstudio/mac/update#Changing_the_Updater_channel). 

## <a name="language-support"></a>Suporte ao idioma 

Escrever código C# 7 no seu Mac é oferecido somente no Visual Studio para Mac.

## <a name="net-core"></a>.NET Core  

O [.NET Core](https://www.microsoft.com/net/core#macos) é uma plataforma para a criação de aplicativos executados no Windows, Linux e Mac. O Visual Studio para Mac tem suporte para carregar, criar, executar e depurar projetos do .NET Core. 

.NET Core é instalado com o Visual Studio para Mac e funciona prontamente.

O suporte do .NET Core inclui: 

* IntelliSense de C# e F #. 
* Modelos de projeto do .NET Core para aplicativos da Web, de biblioteca e de console. 
* Suporte total à depuração, incluindo pontos de interrupção, pilha de chamadas, janela de inspeção, etc. 
* Referências de pacotes NuGet e restauração baseada em MSBuild. 
* Suporte integrado a teste de unidade para executar e depurar testes com a Plataforma de Testes do Visual Studio incluída no SDK do .NET Core. 
* Migração do formato antigo project.json. 
* Suporte a projeto padrão do .NET.

## <a name="web-development"></a>Desenvolvimento para a Web  

### <a name="aspnet-core"></a>ASP.NET Core 

O Visual Studio para Mac inclui modelos prontos de ASP.NET Core para projetos MVC e API da Web.
 
![HTML IntelliSense](media/benefits-vsmac-over-xs-image3.png)

O Visual Studio para Mac adiciona suporte a novas ferramentas da Web para arquivos HTML, CSS e JSON. 

### <a name="html"></a>HTML 

* Novo modelo HTML. 
* Recuo inteligente e formatação aprimorados. 
* Colorização aperfeiçoada. 
* IntelliSense aprimorado. 
* Dobramento de código (deve ser habilitado). 
* Comando Unminify. 
* Modelos de código aprimorados (trechos de código). 
* Envolver seleção com `<div>`. 
* A opção para cima/para baixo move o texto selecionado para cima/baixo. 

### <a name="css"></a>CSS 

* Recuo inteligente e formatação aprimorados. 
* Colorização aperfeiçoada. 
* IntelliSense aprimorado. 
* Dobramento de código. 
* Muitos modelos de código (trechos de código). 
* A opção para cima/para baixo move o texto selecionado para cima/baixo. 

### <a name="json"></a>JSON 
* Selecionador de esquema com acesso ao schemastore.org. 
* Validação com base no esquema. 
* IntelliSense com base no esquema. 
* Recuo inteligente e formatação aprimorados. 
* Colorização aperfeiçoada. 
* Inserir/remover marca de comentário. 
* Injeção de aspas e correspondência de chaves. 
* A opção para cima/para baixo move o texto selecionado para cima/baixo. 

## <a name="publishing-to-azure"></a>Publicação no Azure

Com o Visual Studio para Mac, é possível publicar seus serviços e aplicativos Web do ASP.NET Core para o Serviço de Aplicativo do Azure. 

![Publicar no Azure](media/benefits-vsmac-over-xs-image1.png)

### <a name="azure-functions-preview"></a>Azure Functions (**Versão prévia**)

O Azure Functions é uma solução para executar com facilidade pequenas partes de código, também chamadas funções, na nuvem. O Visual Studio para Mac permite codificar e depurar localmente suas Azure Functions. Para começar, procure por Azure Functions na Nuvem na caixa de diálogo Novo Projeto. 

### <a name="docker-support-preview"></a>Suporte ao Docker (**Versão prévia**)

Agora você pode publicar aplicativos ASP.NET Core para contêineres do Docker e executá-los de um Serviço de Aplicativo do Azure. 

Para habilitar o suporte ao Docker em seu projeto, clique com o botão direito em seu aplicativo Web ASP.NET Core e selecione **Adicionar > Adicionar suporte ao Docker**. 

Para publicar seu aplicativo Web em um contêiner do Docker, use o fluxo de trabalho **Publicar > Publicar no Azure** introduzido no Visual Studio para Mac.

## <a name="source-editor-improvements"></a>Melhorias no editor de código-fonte 

Além do C# IntelliSense baseado em Roslyn, refatoração, analisadores e correções de código, o editor de código-fonte do Visual Studio para Mac fornece as seguintes melhorias em relação ao Xamarin Studio: 

### <a name="language-bundles"></a>Pacotes de linguagem 

O Visual Studio para Mac tem suporte para os pacotes de linguagem TextMate (`.tmBundle`) e sublime 3 (`.sublime`), você pode usar para adicionar: 

* Temas de cores do editor 
* Trechos de código 
* Gramáticas para novas linguagens, habilitando o realce e o IntelliSense básico 

Você pode adicionar esses pacotes em **Preferências > Editor de Texto > Pacotes de Linguagem**. 

### <a name="color-theme-support"></a>Suporte a temas de cores 

Há suporte para seguintes formatos de temas de cores no Visual Studio para Mac: 

* Visual Studio (`.vssettings`) 
* Xamarin studio (`.json`) 
* TextMate (`tmTheme`) 

## <a name="unity"></a>Unity 

[Unity](https://unity3d.com/) é uma ferramenta de criação de jogos que você pode usar para criar jogos 2D e 3D de plataforma cruzada de alta qualidade para todas as principais plataformas: celulares, área de trabalho, consoles, dispositivos RA e VR e até mesmo na Web. 

A partir do Unity 5.6.1, você pode usar o Visual Studio para Mac para escrever e depurar seus jogos Unity. Para começar, defina o Visual Studio como editor de script do Unity 5.6.1. 

As ferramentas para Unity incluem: 

* Suporte a scripts escritos em C#. 
* Painel de soluções do Unity. 
* Depuração com um clique do Unity Editor. 
* IntelliSense para mensagens do Unity. 
* Coloração de código C# para sombreadores do Unity. 
* Acesso à documentação do Unity. 

## <a name="xamarin"></a>Xamarin 

Embora os recursos de plataforma cruzada do Xamarin sempre tenham sido um recurso de primeira classe do Xamarin Studio, alguns recursos Xamarin só estão disponíveis no Visual Studio para Mac 

### <a name="android"></a>Android 

* [Gerenciador de SDK do Android](https://developer.xamarin.com/guides/android/application_fundamentals/using-the-sdk-manager/)  
* O Android O será compatível somente com o Visual Studio para Mac, não o Xamarin Studio 

### <a name="ios-and-mac"></a>iOS e Mac 

* [Atualizações de fluxo de trabalho de assinatura de iOS ](https://developer.xamarin.com/guides/cross-platform/macios/apple-account-management/) 
    * Criar identidades de assinatura e instalá-las no Conjunto de chaves local. 
    * Criar perfis de provisionamento. 
    * Adicionar uma identidade de assinatura a um perfil existente.
    *  Provisionar dispositivos: registrar um dispositivo no Apple Developer Portal e adicioná-los a um perfil de provisionamento.
* iOS 11, watchOS 4 e tvOS 2 serão compatíveis somente com o Visual Studio para Mac, não o Xamarin Studio 
* O MacOS High Sierra será compatível somente com o Visual Studio para Mac, não o Xamarin Studio 

### <a name="cross-platform"></a>Plataforma cruzada 

* [Xamarin Live Player](https://developer.xamarin.com/guides/cross-platform/live/) (**Versão prévia**) 
* [Xamarin IoT](https://developer.xamarin.com/guides/cross-platform/iot/) (**Versão prévia**) 
 
