---
title: Instalar o Visual Studio 2017 | Microsoft Docs
description: Saiba como instalar o Visual Studio, passo a passo.
ms.custom: 
ms.date: 04/03/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
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
ms.sourcegitcommit: af9699b63fdfb81a274affb78856817520c38b05
ms.openlocfilehash: 47688935cec36db174c3a0c424b1705ae47c6118
ms.lasthandoff: 04/03/2017

---
# <a name="install-visual-studio-2017"></a>Instalar o Visual Studio 2017
Bem-vindo a uma nova maneira de instalar o Visual Studio! Em nossa versão mais recente, tornamos mais fácil para você selecionar e instalar apenas os recursos necessários — e reduzimos os requisitos mínimos do Visual Studio para que ele seja instalado mais rapidamente e com menos impacto no sistema do que nunca.  

 Quer saber mais sobre quais são as outras novidades? Consulte nossas [notas de versão](https://www.visualstudio.com/news/releasenotes/vs15-relnotes). E para obter informações mais detalhadas sobre como reformulamos a experiência de instalação, consulte nossas postagens no blog, “[Faster and leaner Visual Studio installer](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer/)” (Instalador do Visual Studio mais rápido e enxuto) e “[Anatomy of a low-impact Visual Studio installation](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install/)” (Anatomia de uma instalação do Visual Studio de baixo impacto).  

 Pronto para instalar? Guiaremos você no processo, passo a passo. Vamos começar.  

## <a name="install-the-installer"></a>Instalar o instalador  
 Ao baixar o Visual Studio 2017, você receberá um arquivo bootstrapper que, por sua vez, instala nosso novo instalador leve. Esse novo instalador inclui tudo o que você precisa para personalizar a instalação.  

> [!IMPORTANT]
> Se você tiver uma Visualização do Visual Studio 2017 instalada no computador, deverá removê-la antes de instalar o Visual Studio 2017.

1.  **[Baixe o Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)** e clique em **Salvar**. Em seguida, na pasta **Downloads**, execute o arquivo bootstrapper que corresponde à edição escolhida.

  * **vs_enterprise.exe** para Visual Studio Enterprise
  * **vs_professional.exe** para Visual Studio Professional
  * **vs_community.exe** para Visual Studio Community  <br><br>

  Se você receber um aviso de Controle de Conta de Usuário, clique em **Sim**.  

2.  Solicitaremos sua confirmação dos [Termos de Licença](https://www.visualstudio.com/license-terms/) da Microsoft e da [Política de Privacidade](https://go.microsoft.com/fwlink/?LinkID=824704) da Microsoft. Clique em **Instalar** para continuar.  

   ![Termos de Licença e Política de Privacidade](media/vs2017-privacy-and-license-terms.PNG "Termos de Licença e Política de Privacidade da Microsoft")  

3.  Você verá várias telas de status que mostram o progresso da instalação. Depois que instalador concluir a instalação, é hora de escolher os conjuntos de recursos — ou cargas de trabalho — desejados.

## <a name="install-workloads"></a>Instalar as cargas de trabalho  
 Agora, você pode personalizar a instalação usando as cargas de trabalho. Selecione uma ou mais das cargas de trabalho desejadas. Cada carga de trabalho contém os recursos necessários para a linguagem de programação ou plataforma de sua preferência.  

 Aqui está como obtê-las.  

1.  Encontre a carga de trabalho desejada na tela **Instalando o Visual Studio**.  

  ![Caixa de diálogo de instalação do Visual Studio 2017](media/vs2017-workloads.PNG "Instalando o Visual Studio 2017")

     Por exemplo, escolha a carga de trabalho de desenvolvimento de área de trabalho do .NET. Ela vem com o editor de núcleo padrão, que inclui o suporte à edição de código básico para mais de 20 linguagens, a capacidade de abrir e editar o código de qualquer pasta sem precisar de um projeto e o controle do código-fonte integrado.  

2.  Depois de selecionar as cargas desejadas, clique em **Instalar**.  

    Em seguida, serão exibidas telas de status que mostram o progresso da instalação do Visual Studio.

3.  Depois que as novas cargas de trabalho e os componentes forem instalados, clique em **Inicializar**.

## <a name="install-individual-components"></a>Instalar componentes individuais

Se você não quiser usar o recurso Cargas de Trabalho útil para personalizar a instalação do Visual Studio, clique na opção **Componentes individuais** do Instalador do Visual Studio, selecione o desejado e siga os prompts.

  ![Visual Studio 2017 — Instalar componentes individuais](media/vs2017-workloads.PNG "Instalar componentes individuais do Visual Studio")

## <a name="install-language-packs"></a>Instalar pacotes de idiomas

Para instalar o Visual Studio 2017 em um idioma de sua escolha, clique na opção **Pacotes de idioma** do Instalador do Visual Studio e siga os prompts.

  ![Visual Studio 2017 — Instalar pacotes de idiomas](media/vs2017-languages.PNG "Instalar pacotes de idiomas do Visual Studio")

### <a name="change-the-installer-language"></a>Alterar o idioma do instalador

Por padrão, o programa do instalador tenta encontrar a correspondência do idioma do sistema operacional quando ele é executado pela primeira vez. O instalador memoriza essa configuração. Você pode alterar essa configuração executando o instalador da linha de comando. Por exemplo, é possível forçar o instalador a ser executado em inglês usando o seguinte comando: `vs_installer.exe --locale en-US`. O instalador memorizará essa configuração quando for executado na próxima vez. O instalador dá suporte aos seguintes tokens de idioma: zh-CN, zh-TW, cs-CZ, en-US, fr-FR, de-DE, it-IT, ja-JP, ko-KR, pl-PL, pt-BR, ru-RU, es-ES e tr-TR.

## <a name="get-support"></a>Obter suporte
Às vezes, as coisas podem dar errado. Caso a instalação do Visual Studio falhe, consulte o artigo do KB [Solucionando falhas de instalação e atualização do Visual Studio 2017](https://support.microsoft.com/help/4015967/troubleshooting-visual-studio-2017-installation-and-upgrade-failures) para obter dicas de solução de problemas.

## <a name="see-also"></a>Consulte também  
* [Modificar o Visual Studio 2017](modify-visual-studio.md)
* [Desinstalar o Visual Studio 2017](uninstall-visual-studio.md)
* [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
* [How to Report a Problem with Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md) (Como relatar um problema com o Visual Studio 2017)

