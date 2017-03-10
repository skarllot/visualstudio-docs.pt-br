---
title: "Microsoft Language Interface Packs (LIPs) e Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "alternância de idiomas [Visual Studio]"
  - "idiomas, suporte a vários idiomas."
  - "MUI [Visual Studio]"
  - "Interface de Usuário Multilíngue [Visual Studio]"
  - "suporte a vários idiomas [SDK do Visual Studio]"
  - "texto [Visual Studio], várias linguagens"
  - "idioma do texto da Interface de Usuário [Visual Studio]"
  - "Interface de Usuário Multilíngue do Windows"
ms.assetid: dc86304b-65b7-47e6-9314-1dfd02ecfa65
caps.latest.revision: 28
caps.handback.revision: 28
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Microsoft Language Interface Packs (LIPs) e Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Usando um Windows Language Interface Pack \(LIP\), você pode instalar uma versão de idioma do windows e então instalar diversos Pacotes de Idiomas da Interface do Usuário.  Pacotes de idiomas da interface do usuário oferecem uma interface do usuário localizada \(IU\) do sistema operacional.  Por exemplo, você pode instalar um Language Interface Pack em japonês sobre uma versão do Windows em inglês e então alternar o idioma da interface de usuário do Windows entre japonês e inglês.  Usando os LIPs, você pode ter várias versões de idioma do Windows em um computador.  
  
 Em computadores com os LIPs e versões de vários idiomas do Visual Studio instaladas, a alteração da configuração do idioma para exibição do Windows define o Windows e o Visual Studio quando pacotes de idiomas correspondentes são instalados.  
  
## Limitações de instalações multilíngues  
 Quando você instala versões de idioma diferentes do Visual Studio no mesmo computador, você só poderá alternar idiomas entre edições correspondentes.  Por exemplo, se você tiver uma Express Edition instalada em inglês, uma Express Edition instalada em alemão e uma Professional Edition instalada, só poderá alternar idiomas para as Express Editions, e não para a Professional Edition.  
  
 O Visual Studio usa um pacote de idiomas unificado.  Para instalar mais de uma versão de idioma desses produtos, você deve instalar um produto com todos os idiomas primeiro e então instalar um ou mais pacotes de idioma.  
  
> [!NOTE]
>  O Visual Studio não oferece suporte a instalação de várias versões de idioma do produto todos os idiomas no mesmo computador.  Depois de instalar um produto com todos os idiomas, você deverá adicionar versões de idioma usando pacotes de idiomas.  Você ainda pode instalar vários produtos de idiomas completos das edições Express no mesmo computador.  
  
### Suporte para páginas de código  
 Algumas ferramentas do Visual Studio não exibem o texto corretamente quando o texto contém caracteres que não estão na página de código atual.  Em vez disso, os pontos de interrogação aparecem ou texto está corrompido.  As seguintes ferramentas ou áreas são afetadas:  
  
-   Sites implantados usando FTP.  
  
-   Nomes de computador não ASCII em alguns controles.  
  
-   Ferramentas de linha de comando executadas fora do Visual Studio.  
  
-   Assistente de Migração do Visual Basic.  
  
-   Contêiner de teste de controle ActiveX.  
  
-   Visualizador de Objeto OLE\/COM.  
  
-   Ferramenta de depuração ISAPI Web.  
  
-   Os projetos de aplicativos MFC que têm conteúdo da Ajuda HTML.  
  
-   A interface do usuário do Visual SourceSafe\/SCCI voltará para o inglês quando houver uma página de código incompatível.  
  
-   O Visual SourceSafe não dá suporte para nomes de arquivo Unicode.  
  
-   Caracteres Definidos pelo Usuário Final \(zona de uso particular\) não podem ser usados como tokens\/identificadores.  
  
-   Os caracteres Latinos Estendidos\-B não podem ser exibidos em algumas janelas de ferramentas do Visual Studio quando a página de código do Windows estiver definida para um idioma do leste asiático.  
  
-   As execuções de texto que consistem em caracteres de scripts de vários idiomas podem exibir o glifo padrão para alguns caracteres.  
  
-   Copiar e colar cadeias de caracteres de script complexas para controles pode causar a perda do shaping de caractere.  Em vez disso, use o teclado de idioma correspondente para inserir texto.  
  
##### Para exibir corretamente caracteres que não estão incluídos na página de código atual  
  
1.  Clique em **Iniciar**, clique em **Painel de Controle** e então abra **Opções Regionais e de Idiomas** \(ou **Região** no [!INCLUDE[win8](../debugger/includes/win8_md.md)]\).  
  
    > [!NOTE]
    >  Você deve ser um administrador no computador para seguir estas etapas.  
  
2.  Clique na aba **Avançado**.  
  
3.  Na lista **Selecionar uma linguagem para corresponder à versão de linguagem dos programas não Unicode que você deseja usar**, selecione a linguagem que você está usando atualmente.  
  
4.  Clique em **OK**.  
  
## Alterando o idioma usado para o texto da interface do usuário no Visual Studio  
 Quando você instalar versões de vários idiomas do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no mesmo computador, a interface de usuário do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] será padronizada para **Como no Microsoft Windows**.  Essa configuração indica que o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] exibirá o texto da interface do usuário no idioma especificado como o idioma para exibição para o sistema operacional.  
  
> [!NOTE]
>  Se o Visual Studio estiver definido para usar **Como no Microsoft Windows**, e se o pacote de idiomas do Visual Studio correspondente não estiver instalado, o Visual Studio usará o idioma da primeira instalação do Visual Studio.  
  
#### Para definir o idioma usado para o texto da interface do usuário no Visual Studio  
  
1.  No menu **Ferramentas**, clique em **Opções**.  
  
2.  Na caixa de diálogo **Opções**, expanda **Ambiente** e depois clique em **Configurações Internacionais**.  
  
3.  Na lista **Idioma**, escolha o idioma em que o texto da interface de usuário deve aparecer no ambiente de desenvolvimento.  
  
     Para que o texto de interface do usuário no IDE corresponda à configuração de idioma para exibição do sistema operacional, selecione **Como no Microsoft Windows**.  
  
 Você também pode usar o comando devenv para definir o idioma usado para interface do usuário.  Para obter mais informações, consulte [\/LCID](../ide/reference/lcid-devenv-exe.md).  
  
## Consulte também  
 [Caixa de diálogo Configurações Internacionais, Ambiente, Opções](../ide/reference/international-settings-environment-options-dialog-box.md)