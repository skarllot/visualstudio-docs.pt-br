---
title: Criar um instalador offline para o Visual Studio 2017 | Microsoft Docs
description: Saiba como criar um instalador offline para o Visual Studio.
ms.custom: 
ms.date: 03/07/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- offline installer [Visual Studio]
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
ms.sourcegitcommit: 91fde66abf2f325ef0a6a0a2fd30e36981f44033
ms.openlocfilehash: acb47946c29d99cb53b34d67fe8a26f5611307f9
ms.lasthandoff: 03/08/2017

---
# <a name="create-an-offline-installer-for-visual-studio-2017"></a>Criar um instalador offline para o Visual Studio 2017
Sabemos que muitos clientes desejam um instalador offline para o [Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=844067). Embora não ofereçamos uma imagem ISO, é fácil criar uma pasta que pode ser usada para instalar no modo offline.

Veja como.

## <a name="download-the-setup-file-you-want"></a>Baixar o arquivo de configuração desejado
**[Baixe](https://www.visualstudio.com/downloads?utm_source=mscom&utm_campaign=msdocs)** a edição do Visual Studio desejada. Lembre-se de clicar em **Salvar** e, em seguida, clique em **Abrir pasta**.

O arquivo de instalação &mdash; ou para ser mais específico, um arquivo bootstrapper &mdash; corresponderá a um dos listados a seguir.

|Edição | Arquivo|  
|-------------|-----------------------|  
|Visual Studio Enterprise |**vs_enterprise.exe**|  
|Visual Studio Professional |**vs_professional.exe**|  
|Comunidade Visual Studio |**vs_community.exe**|

## <a name="create-an-offline-installation-folder"></a>Criar uma pasta de instalação offline
Para criar uma instalação offline com todos os idiomas e recursos, use um dos comandos dos exemplos a seguir.

(Lembre-se de executar o comando no diretório de Download. Normalmente, ele é `C:\Users\<username>\Downloads` em um computador que executa o Windows 10).

- Para o Visual Studio Enterprise, execute: <br>  ```vs_enterprise.exe --layout c:\vs2017offline```
- Para o Visual Studio Professional, execute: <br> ```vs_professional.exe --layout c:\vs2017offline```
- Para o Visual Studio Community, execute: <br> ```vs_community.exe --layout c:\vs2017offline```

Para obter mais exemplos, consulte a seção [Como personalizar o instalador offline](#how-to-customize-your-offline- installer) nesta página.

## <a name="install-from-the-offline-installation-folder"></a>Instalar por meio da pasta de instalação offline
Execute a instalação offline agora ou mais tarde: isso fica a seu critério. Mas quando fizer isso, siga estas etapas.

  1. Instale os certificados (eles estão na pasta Certificates, que está na pasta Layout. Basta clicar com o botão direito do mouse em cada um deles para instalá-los.)

  2. Execute o arquivo de instalação. Por exemplo, execute: <br> ```c:\vs2017offline\vs_enterprise.exe```

## <a name="additional-tips-for-offline-installers"></a>Dicas adicionais para instaladores offline
É fácil personalizar ou atualizar o instalador offline. Vamos mostrar como fazer isso. E se algo der errado com o instalador offline, também temos solução de problemas e informações de suporte para você.

### <a name="how-to-customize-your-offline-installer"></a>Como personalizar o instalador offline
Há várias opções que podem ser usadas para personalizar o instalador offline. Estes são alguns exemplos de como personalizá-lo por [localidade de idioma](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

 - Para baixar todas as cargas de trabalho e todos os componentes para um único idioma, execute: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
 - Para baixar todas as cargas de trabalho e todos os componentes para vários idiomas, execute: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
 - Para baixar uma carga de trabalho para todos os idiomas, execute <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure ```
 - Para baixar duas cargas de trabalho e um componente opcional para três idiomas, execute: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure Microsoft.VisualStudio.Workload.ManagedDesktop Component.GitHub.VisualStudio --lang en-US de-DE ja-JP ``` Para saber mais sobre as opções que podem ser usadas para personalizar a instalação, consulte nossa página [Usar parâmetros de linha de comando para instalar o Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md).


### <a name="how-to-update-an-offline-installer"></a>Como atualizar um instalador offline
Talvez você deseje atualizar o instalador offline em uma data posterior. Veja como.
* Para atualizar uma instância do Visual Studio instalada por meio de uma pasta de instalação offline, execute o instalador do Visual Studio e, em seguida, clique em **Atualizar**.
* Para atualizar a pasta de instalação offline para que ela inclua as últimas atualizações, execute o comando ```--layout``` novamente. Lembre-se de apontar para a mesma pasta usada anteriormente; dessa forma, somente os componentes que foram atualizados desde a última execução de ```--layout``` serão baixados.


Se desejar atualizar a instalação offline, execute o comando `--layout` novamente. Lembre-se de apontar para a mesma pasta usada anteriormente; dessa forma, somente os componentes que foram atualizados desde a última execução de `--layout` serão baixados.

### <a name="how-to-troubleshoot-an-offline-installer"></a>Como solucionar problemas de um instalador offline
Às vezes, as coisas dão errado. Esta é uma tabela de problemas conhecidos e algumas soluções alternativas que podem ajudar.

| Problema       | Item                   | Solução |
| ----------- | ---------------------- | -------- |
| Você recebe uma mensagem de aviso informando que não é possível instalar alguns componentes e pacotes.  | Instalação do SDK do Android (nível de API) | Se desejar incluir pacotes do SDK do Android (Nível de API), será necessário ter uma conexão com a Internet ao criar o instalador offline. Se estiver em uma rede restrita, será necessário permitir o acesso às seguintes URLs: <br><br> - http://dl.google.com:443 <br> - http://dl-ssl.google.com:443 <br>  - https://dl-ssl.google.com/android/repository/*<br><br>Para obter mais informações sobre como solucionar possíveis problemas com configurações de proxy, consulte a postagem de blog [Visual Studio install failures (Android SDK Setup) behind a Proxy (Falhas de instalação do Visual Studio (instalação do SDK do Android) por trás de um proxy)](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/).  |  
| Os usuários não têm acesso aos arquivos. | permissões (ACLs) | Lembre-se de ajustar as permissões (ACLs) para que elas concedam acesso de Leitura aos outros usuários *antes* de você compartilhar a instalação offline. |
| Falha na instalação de novas cargas de trabalho, novos componentes ou idiomas.  | `--layout`  | Verifique se você tem acesso à Internet se estiver instalando com base em um layout parcial e selecione as cargas de trabalho, os componentes ou idiomas que não estão disponíveis no layout anterior. |

### <a name="how-to-get-support-for-your-offline-installer"></a>Como obter suporte para o instalador offline
Caso tenha um problema com a instalação offline, gostaríamos de saber a respeito. A melhor maneira de fazer isso é usando a ferramenta [Relatar um Problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Ao usar essa ferramenta, é possível enviar-nos a telemetria e os logs necessários para nos ajudar a diagnosticar e corrigir o problema.

Também temos outras opções de suporte disponíveis. Para obter uma lista delas, consulte nossa página [Fale conosco](../ide/how-to-report-a-problem-with-visual-studio-2017.md).


## <a name="see-also"></a>Consulte também
* [Instalar o Visual Studio](install-visual-studio.md)
* [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Carga de trabalho do Visual Studio e IDs do componente](workload-and-component-ids.md)

