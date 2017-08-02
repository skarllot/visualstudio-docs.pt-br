---
title: Instalar e configurar | Microsoft Docs
ms.custom: 
ms.date: 04/13/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: d353d8a0a41ad487191b79aa68f26585cf9902b4
ms.contentlocale: pt-br
ms.lasthandoff: 05/13/2017

---
# <a name="setup-and-install"></a>Instalar e configurar
Para criar aplicativos nativos do iOS, Android e Windows de uma base de código comum C#/.NET usando Xamarin, você precisa do seguinte:  
  
-   Para trabalhar com aplicativos do Windows e Android: um computador de desenvolvimento do Windows com o Visual Studio 2017 ou 2015 com o Xamarin instalado. Você também pode usar o Visual Studio 2013, seguindo as instruções para [instalação direta do Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com). 
  
-   Para trabalhar com aplicativos do iOS: um Mac com macOS Serra 10.12 ou acima, com Xcode e Xamarin instalados.  
  
 Você poderá configurar os computadores Windows e Mac ao mesmo tempo e, enquanto os instaladores estiverem em execução, poderá analisar [Saiba mais sobre desenvolvimento móvel com Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) para ler e inspecionar o material básico necessário.  
 
Se você tiver problemas para usar o Xamarin depois de fazer essa configuração e instalação, envie sua pergunta para [forums.xamarin.com](http://forums.xamarin.com/).
  
> [!NOTE]
>  A partir de 31 de março de 2016, todo o conteúdo do Xamarin é incluído com todas as edições do Visual Studio sem custo adicional e ele não precisa de uma licença separada. O Xamarin Studio Community para Mac também é gratuito para estudantes, desenvolvedores de OSS e pequenas equipes. Observe que, para as instalações existentes do Visual Studio que são configuradas com licenças do Xamarin mais antigas, você deve atualizar o Xamarin para a versão 4.0.3.214 ou superior. Para fazer isso, vá para **Ferramentas > Opções > Xamarin > Outros**, clique no link **Verificar Agora** e baixe a atualização 4.0.3.214. Quando você reiniciar o Visual Studio, vá para **Ferramentas > Conta do Xamarin...**  e você deverá ver o status atualizado.  
  
##  <a name="prereq"></a> Pré-requisitos  
  
###  <a name="for-targeting-windows-and-android"></a>Para direcionamento ao Windows e ao Android 
  
1.  Recomendado: um computador físico com Windows (não uma VM) executando o Windows 8 ou posterior, para obter o melhor desempenho do emulador do Android. (Já mencionamos que você precisa de um computador físico e não de uma VM?)  
  
2.  Você poderá usar um computador Windows 7 ou anterior e, nesse caso, você usará o Xamarin Player para Android como o emulador. 
    
3. Para qualquer configuração, você também pode executar aplicativos diretamente em dispositivos físicos conectados.  
  
### <a name="for-targeting-ios"></a>Para direcionamento ao iOS  
  
1.  Uma rede Mac ou Mac mini com macOS Serra executando macOS 10.12 ou posterior (necessário para Xcode 8.3).  
  
2.  Ao usar o Visual Studio em um computador com Windows (7+) como seu principal ambiente de desenvolvimento, um Mac em rede é necessário apenas para compilar e depurar aplicativos iOS, anexar o simulador de iOS ou dispositivos vinculados e usar o designer de storyboard no Visual Studio para criar a interface do usuário. Os modelos mais antigos do Mac são totalmente suficientes para esta função secundária.  
  
##  <a name="windows"></a> Instalação do Windows (Visual Studio e Xamarin)  
  
> [!TIP]
>  Essas instruções se aplicam ao Visual Studio 2017. Para Visual Studio 2015, confira [MSDN](https://msdn.microsoft.com/en-us/library/mt613162.aspx). Para usar o Xamarin com o Visual Studio 2013 (A Atualização 2 é necessária), siga as instruções para [instalação direta do Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com).  
  
1.  [Baixe e inicie o instalador para qualquer edição do Visual Studio 2017](https://www.visualstudio.com/downloads/) (Community, Professional ou Enterprise). O Visual Studio 2017 Community é a versão gratuita; as edições Professional e Enterprise poderão ser usadas em uma base de avaliação por 30 dias, após os quais você precisará adquirir uma licença.  
  
    1.  Se você já tiver o Visual 2017 Studio instalado, execute o **Instalador do Visual Studio** no menu **Iniciar**.
  
2.  No instalador, clique no botão **Opções adicionais** (ícone de três barras) _ao lado de_ **Inicialização** e, então, escolha **Modificar**.:  
  
     ![Como escolher a opção Modificar na instalação do Visual Studio](~/docs/cross-platform/media/cross-plat-xamarin-setup-1a.png "Instalação 1 entre várias plataformas do Xamarin")  
  
3.  Verifique as seguintes caixas:  
  
    1.  **Celular e Jogos > Desenvolvimento Móvel com o .NET**. Isso também selecionará automaticamente várias ferramentas Android em Ferramentas Comuns e Kits de desenvolvimento de Software. Essa opção também deve atualizar uma instalação existente do Xamarin.  
  
         ![Selecione a opção Desenvolvimento Móvel em Jogos e Desenvolvimento Móvel](~/docs/cross-platform/media/cross-plat-xamarin-setup-2a.png "Instalação 2 entre várias plataformas do Xamarin")  
  
    2. (Opcional) **Windows > Desenvolvimento da Plataforma Universal do Windows**. Isso inclui opções de instalação de imagens de emulador que levarão mais tempo para baixar; você sempre pode retornar ao instalador do Visual Studio para adicioná-las mais tarde. 
  
4.  Clique no botão **Modificar** e permita que o processo seja executado. Novamente, isso levará algum tempo para ser concluído; durante esse período, você pode continuar com as instruções de configuração do Mac e percorrer [Saiba mais sobre desenvolvimento móvel com Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).  
  
5.  Depois que a instalação for concluída, inicie o Visual Studio e entre com sua conta da Microsoft se solicitado (é a mesma conta que você usa com o Windows).  
      
6.  Para testar aplicativos Android, use o [Emulador do SDK do Android](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/android-sdk-emulator/) se você não tiver dispositivos físicos. Consulte a observação abaixo.  
  
 **Observação sobre emuladores em computadores Windows:** já que as CPUs dão suporte apenas a uma tecnologia de virtualização por vez, é melhor ter apenas uma em uso em um computador de desenvolvimento. Há três tecnologias de virtualização principais, que são Hyper-V (usada pelo emulador do Visual Studio para Android e pelo emulador do Windows Phone), Virtual Box (usada pelo Genymotion) e Intel HAXM (usada pelo emulador do SDK do Android). Devido a vários problemas entre o Hyper-V e o Virtual Box, é melhor usar emuladores de um único tipo em um determinado computador, por isso as recomendações acima para usar o Hyper-V em computadores Windows 8 e superiores e emuladores Intel HAXM no Windows 7 e anteriores e também ao executar o Windows no Mac.  
  
##  <a name="mac"></a> Configuração do Mac (Apple ID, Xcode e Xamarin)  
  
1.  Crie uma ID Apple gratuita em [https://appleid.apple.com](https://appleid.apple.com/) caso ainda não tenha uma. Isso é necessário para instalar e entrar no Xcode.  
  
2.  Baixe e instale o Xcode de [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/) e adicione sua ID Apple, conforme descrito em [Adicionar sua conta para XCode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).  
  
3.  Baixe e instale o Xamarin, seguindo as instruções em [Instalando e configurando o Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (xamarin.com).  
  
4.  Depois de concluir a instalação do Xamarin nos computadores Windows e Mac, siga as instruções em [Conectando ao Mac](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) (xamarin.com) para que você possa trabalhar com o iOS e o Mac usando do Visual Studio no computador Windows.  
  
     Observe que ambos os computadores devem estar na mesma rede local.
