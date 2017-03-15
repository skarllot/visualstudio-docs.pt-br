---
title: Instalar o Visual Studio 2017 RC | Microsoft Docs
description: Saiba como instalar o Visual Studio, passo a passo.
ms.custom: 
ms.date: 11/18/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio Preview
- install Visual Studio
- installing Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
ms.assetid: 8d4297e4-9f43-4f12-95ec-22e61154480e
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
ms.sourcegitcommit: 5e1ab0284a11fb9ecf30694d22b8bb5dc7a52a6d
ms.openlocfilehash: 997a1e0966c5e08314c616dba76842120ab50d63

---
# <a name="install-visual-studio-2017-rc"></a>Instalar o Visual Studio 2017 RC
Bem-vindo a uma nova maneira de instalar o Visual Studio! Em nossa versão mais recente, tornamos mais fácil para você selecionar e instalar apenas os recursos necessários — e reduzimos os requisitos mínimos do Visual Studio para que ele seja instalado mais rapidamente e com menos impacto no sistema do que nunca.  

 Quer saber mais sobre quais são as outras novidades no RC? Consulte nossas [notas de versão](https://www.visualstudio.com/news/releasenotes/vs15-relnotes). E para obter informações mais detalhadas sobre como reformulamos a experiência de instalação, consulte nossas postagens no blog, “[Faster and leaner Visual Studio installer](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer/)” (Instalador do Visual Studio mais rápido e enxuto) e “[Anatomy of a low-impact Visual Studio installation](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install/)” (Anatomia de uma instalação do Visual Studio de baixo impacto).  

 Pronto para instalar? Guiaremos você no processo, passo a passo. Vamos começar.  

## <a name="install-the-installer"></a>Instalar o instalador  
 Quando você baixar o Visual Studio 2017 RC, receberá um arquivo bootstrapper que por sua vez instala nosso novo instalador leve. Esse novo instalador inclui tudo o que você precisa para personalizar a instalação.  

> [!IMPORTANT]
> Se tiver uma versão de visualização do Visual Studio 2017 instalada em seu computador, você deverá removê-la antes de instalar o Visual Studio 2017 RC.

1.  [Baixe o Visual Studio Enterprise 2017 RC](https://www.visualstudio.com/vs/visual-studio-2017-rc/) e clique em **Salvar**.  Em seguida, da pasta **Downloads**, execute o arquivo `vs_Enterprise.exe`.  

     Se você receber um aviso de Controle de Conta de Usuário, clique em **Sim**.  

2.  Solicitaremos sua confirmação dos [Termos de Licença](https://www.visualstudio.com/support/legal/mt591984) da Microsoft e a [Política de Privacidade](https://www.visualstudio.com/dn948229) da Microsoft. Clique em **Instalar** para continuar.  

  ![Termos de Licença e Política de Privacidade](media/01-installingdev15prev4-licensetermsandprivacystatement.png "Termos de Licença e Política de Privacidade da Microsoft")  

3.  Você verá várias telas de status que mostram o progresso da instalação. Depois que instalador concluir a instalação, é hora de escolher os conjuntos de recursos — ou cargas de trabalho — desejados.

## <a name="install-workloads"></a>Instalar as cargas de trabalho  
 Agora, você pode personalizar a instalação usando as cargas de trabalho. Selecione uma ou mais das cargas de trabalho desejadas. Cada carga de trabalho contém os recursos necessários para a linguagem de programação ou plataforma de sua preferência.  

 Aqui está como obtê-las.  

1.  Encontre a carga de trabalho desejada na tela **Instalando o Visual Studio**.  

  ![Caixa de diálogo de instalação do Visual Studio 2017 RC](../ide/media/willow1.png "Instalando o Visual Studio 2017")

     Por exemplo, escolha a carga de trabalho de desenvolvimento do .NET Desktop. Ela vem com o editor de núcleo padrão, que inclui o suporte à edição de código básico para mais de 20 linguagens, a capacidade de abrir e editar o código de qualquer pasta sem precisar de um projeto e o controle do código-fonte integrado.  

2.  Depois de selecionar as cargas desejadas, clique em **Instalar**.  

    Em seguida, serão exibidas telas de status que mostram o progresso da instalação do Visual Studio.

3.  Depois que as novas cargas de trabalho e os componentes forem instalados, clique em **Inicializar**.

## <a name="install-individual-components"></a>Instalar componentes individuais

Se você não quiser usar o recurso Cargas de Trabalho útil para personalizar a instalação do Visual Studio, clique na opção **Componentes individuais** do Instalador do Visual Studio, selecione o desejado e siga os prompts.

  ![Visual Studio 2017 — Instalar componentes individuais](media/vs2017install-IndividualComponents.PNG "Instalar componentes individuais do Visual Studio")

## <a name="install-language-packs"></a>Instalar pacotes de idiomas

Para instalar o Visual Studio 2017 RC em um idioma de sua escolha, clique na opção **Pacotes de idioma** do Instalador do Visual Studio e siga os prompts.

  ![Visual Studio 2017 — Instalar pacotes de idiomas](media/vs2017install-LanguagePacks.PNG "Instalar pacotes de idiomas do Visual Studio")

### <a name="change-the-installer-language"></a>Alterar o idioma do instalador

Por padrão, o programa de instalação tenta corresponder ao idioma do sistema operacional quando executado pela primeira vez. O instalador se lembrará dessa configuração. Você pode alterar essa configuração executando o instalador da linha de comando. Por exemplo, você pode forçar o instalador a ser executado em inglês executando `vs_installer.exe --locale en-US`. Essa configuração será lembrada quando o instalador for executado da próxima vez. O instalador dá suporte aos seguintes tokens de idioma: zh-CN, zh-TW, cs-CZ, en-US, fr-FR, de-DE, it-IT, ja-JP, ko-KR, pl-PL, pt-BR, ru-RU, es-ES e tr-TR.


  > [!IMPORTANT]
  > Embora o Visual Studio 2017 RC, de modo geral, tenha suporte para uso em um ambiente de produção, as cargas de trabalho e componentes que estão marcados como "Visualização" na interface do usuário da instalação não têm suporte para uso em ambiente de produção.

## <a name="see-also"></a>Consulte também  
* [Modificar o Visual Studio 2017 RC](modify-visual-studio.md)
* [Uninstall Visual Studio 2017 RC](uninstall-visual-studio.md) (Desinstalar o Visual Studio 2017 RC)
* [Visual Studio Administrator Guide](visual-studio-administrator-guide.md) (Guia do administrador do Visual Studio)
* [How to Report a Problem with Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md) (Como relatar um problema com o Visual Studio 2017)



<!--HONumber=Feb17_HO4-->


