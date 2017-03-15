---
title: "Criar uma instalação offline do Visual Studio 2017 RC | Microsoft Docs"
description: "Aprenda a criar uma instalação offline do Visual Studio."
ms.custom: 
ms.date: 02/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- ISO [Visual Studio]
ms.assetid: 7bd7e724-7bfd-43f1-9935-981919be5a00
author: TerryGLee
ms.author: tglee
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
ms.sourcegitcommit: d4d1bd45ce697017480b3f63d0c7feb5ab20d2d6
ms.openlocfilehash: 33e765d205aa7ad8a3d8c5b871863ab659092a77
ms.lasthandoff: 02/22/2017

---
# <a name="create-an-offline-installation-of-visual-studio-2017-rc"></a>Criar uma instalação offline do Visual Studio 2017 RC

## <a name="create-a-layout"></a>Criar um layout
Se você desejar instalar o [Visual Studio 2017 RC](https://www.visualstudio.com/vs/visual-studio-2017-rc/) em outro computador que não tenha acesso à Internet, será possível fazê-lo criando primeiro um layout de instalação offline que contenha todos os arquivos e componentes do Visual Studio de que você precisa.

Em seguida, é possível instalar o Visual Studio no computador de destino usando o layout de instalação offline criado.     

> [!WARNING]
> Atualmente, o SDK do Android não dá suporte a uma experiência de instalação offline. Se você instalar itens de instalação do SDK do Android em um computador que não está conectado à Internet, a instalação poderá falhar. Para obter mais informações sobre isso, vá para a seção [Solucionar problemas de uma instalação offline](#tshootofflineinstall) neste tópico.


#### <a name="to-create-an-offline-installation-layout-of-visual-studio"></a>Para criar um layout de instalação offline do Visual Studio
1. Baixe o arquivo executável de instalação do Visual Studio em uma unidade no seu computador local.
  Por exemplo, [baixe o arquivo vs_enterprise.exe](https://www.visualstudio.com/vs/visual-studio-2017-rc/).
2. Execute `vs_enterprise.exe` com os seguintes argumentos (opções) em um prompt de comando:

   a. Adicione `--layout <path>`, em que `<path>` é o local no qual você deseja baixar o layout. Observe que os caminhos relativos (por exemplo, `..\vs2017`) não têm suporte no momento. Por padrão, todas as linguagens são baixadas. (Veja o exemplo A.)

   b. Restrinja o download a um subconjunto de idiomas disponíveis, fornecendo o argumento `--lang <language>`, em que `<language>` é um ou mais idioma-localidades.  (Veja o exemplo B e o exemplo C.)

   c. Restrinja o download a um subconjunto de Cargas de trabalho e Componentes fornecendo o argumento `--add <package ID>`. Isso baixará somente as cargas de trabalho e os componentes (e suas dependências) especificados. (Veja o exemplo D e o exemplo E.)

   Para obter uma lista completa de IDs de componente e de carga de trabalho classificadas por produto do Visual Studio, consulte nossa página [Visual Studio 2017 Workload and Component IDs (IDs de componente e de carga de trabalho do Visual Studio 2017)](https://aka.ms/vs2017componentids).

### <a name="examples"></a>Exemplos
**Exemplo A**: baixe todas as cargas de trabalho e componentes para todos os idiomas
  > ```vs_enterprise.exe --layout C:\vs2017```

**Exemplo B**: baixe todas as cargas de trabalho e componentes para um idioma  
  > ```vs_enterprise.exe --layout C:\vs2017 --lang en-US```

**Exemplo C**: baixe todas as cargas de trabalho e componentes para vários idiomas
  > ```vs_enterprise.exe --layout C:\vs2017 --lang en-US de-DE ja-JP```

**Exemplo D**: baixe uma carga de trabalho para todos os idiomas
  > ```vs_enterprise.exe --layout C:\vs2017 --add Microsoft.VisualStudio.Workload.Azure ```

**Exemplo E**: baixe duas cargas de trabalho e um componente opcional para três idiomas
  > ```vs_enterprise.exe --layout C:\vs2017 --add Microsoft.VisualStudio.Workload.Azure Microsoft.VisualStudio.Workload.ManagedDesktop Component.GitHub.VisualStudio --lang en-US de-DE ja-JP ```

  > [!WARNING]
  > O parâmetro --layout falhará se o nome do arquivo .exe de instalação incluir numerais. Para resolver esse problema, é necessário remover os numerais do nome do arquivo – por exemplo, renomeie *vs_community__198521760.1486960229.exe* como ***vs_community.exe***.

### <a name="language-locales"></a>Localidades de idioma

| Localidade de idioma | Linguagem |
| -----   | ----- |
| cs-CZ    | Tcheco |
| de-DE    | Alemão |
| pt-BR    | Inglês |
| es-ES    | Espanhol |
| fr-FR    | Francês |
| it-IT    | Italiano |
| ja-JP    | Japonês |
| ko-KR    | Coreano |
| pl-PL    | Polonês |
| pt-BR    | Português - Brasil |
| ru-RU    | Russo |
| tr-TR    | Turco |
| zh-CN    | Chinês – Simplificado |
| zh-TW    | Chinês – Tradicional |


## <a name="install-from-a-layout"></a>Instalar com base em um layout
#### <a name="to-install-visual-studio-from-an-offline-installation-layout"></a>Para instalar o Visual Studio com base em um layout de instalação offline
1. No computador de destino, navegue até a pasta **Certificados**, que está na pasta Layout.
2. Clique com botão direito do mouse e instale cada certificado na pasta **Certificados**.

  (Se você for solicitado a inserir uma senha depois de instalar um certificado, clique em **Continuar**.)  
3. Execute `vs_enterprise.exe` na pasta **Layout**.

Observação: se você estiver instalando com base em um layout parcial e selecionar cargas de trabalho, componentes ou linguagens não disponíveis no layout, a instalação tentará baixá-los.  Se você não tiver acesso à Internet, a instalação desses itens falhará.

> [!CAUTION]
> Atualmente, o layout de instalação offline cria alguns arquivos com permissões restritas (ACLs) que impedem o acesso por todos os usuários.  Certifique-se de ajustar as permissões (ACLs) para que elas concedam Acesso de leitura a outros usuários *antes* de você compartilhar a instalação offline.

## <a name="update-an-installation-layout"></a>Atualizar um layout de instalação
À medida que forem disponibilizadas atualizações para o Visual Studio 2017 RC, será possível executar o comando `--layout` novamente, apontando para a mesma pasta de layout, a fim de garantir que a pasta contenha os componentes mais recentes. Somente os componentes que tiverem sido atualizados desde a última vez em que `--layout` foi executado serão baixados.

## <a id="tshootofflineinstall"> </a>Solucionar problemas de uma instalação offline
Quando você faz instalação offline de seu cache de instalação offline, você pode ver mensagens de aviso sobre não ser possível instalar alguns componentes e pacotes. A tabela a seguir inclui soluções possíveis para esses cenários.

| Componente ou pacote | Solução |
| -------------------- | -------- |
|Instalação do SDK do Android (nível de API)| Você deve ter uma conexão com a Internet para instalar os pacotes de SDK do Android (nível de API). Se você estiver em uma rede restrita, será necessário permitir o acesso às seguintes URLs ao instalar o Visual Studio: <br><br> - http://dl.google.com:443 <br>- http://dl-ssl.google.com:443 <br>  - https://dl-ssl.google.com/android/repository/*<br><br>Para obter mais informações sobre como solucionar possíveis problemas com configurações de proxy, consulte a postagem de blog [Visual Studio install failures (Android SDK Setup) behind a Proxy (Falhas de instalação do Visual Studio (instalação do SDK do Android) por trás de um proxy)](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/).  |  

 > [!IMPORTANT]
 > Embora o Visual Studio 2017 RC, de modo geral, tenha suporte para uso em um ambiente de produção, as cargas de trabalho e componentes que estão marcados como "Visualização" na interface do usuário da instalação não têm suporte para uso em ambiente de produção.

 ## <a name="see-also"></a>Consulte também
 * [Instalar o Visual Studio](install-visual-studio.md)
 * [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Relatar um problema com o Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

