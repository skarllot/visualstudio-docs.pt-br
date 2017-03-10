---
title: "Instru&#231;&#245;es passo a passo: implantando um aplicativo ClickOnce manualmente | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implantação ClickOnce, manualmente"
  - "implantação ClickOnce, ferramentas SDK"
  - "implantando aplicativos [ClickOnce], implantações ClickOnce manuais"
  - "Mage.exe, implantações ClickOnce manuais"
  - "MageUI.exe, implantações ClickOnce manuais"
  - "manifestos [ClickOnce]"
  - "implantações ClickOnce manuais"
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
caps.latest.revision: 49
caps.handback.revision: 47
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: implantando um aplicativo ClickOnce manualmente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se você não pode usar Visual Studio para implantar seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo, ou você precisa usar os recursos de implantação avançada, como a implantação de aplicativos confiáveis, você deve usar a ferramenta de linha de comando Mage para criar seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestos.  Esta explicação passo a passo descreve como criar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação usando a versão de linha de comando \(Mage\) ou a versão gráfica \(MageUI.exe\) da ferramenta de edição e geração de manifesto.  
  
## Pré-requisitos  
 Esta explicação passo a passo tem alguns pré\-requisitos e as opções que você precisa escolher antes de criar uma implantação.  
  
-   Instale Mage e MageUI.exe.  
  
     Mage e MageUI.exe fazem parte do [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  Você deve ativa o [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] instalado ou a versão do [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] incluído com o Visual Studio.  Para obter mais informações, consulte [SDK do Windows](http://go.microsoft.com/fwlink/?LinkId=158044) no MSDN.  
  
-   Fornece um aplicativo ser implantado.  
  
     Esta explicação passo a passo presume que você tenha um aplicativo do Windows que você está pronto para implantar.  Este aplicativo será ser conhecido como AppToDeploy.  
  
-   Determine como a implantação será distribuída.  
  
     As opções de distribuição incluem: Web, compartilhamento de arquivos ou CD.  Para obter mais informações, consulte [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md).  
  
-   Determine se o aplicativo requer um nível elevado de confiança.  
  
     Se seu aplicativo requer confiança total — por exemplo, acesso total ao sistema do usuário — você pode usar o `-TrustLevel` opção de Mage para defini\-la.  Se você quiser definir uma permissão personalizada definida para seu aplicativo, copiar a seção de permissão de Internet ou intranet de outro manifesto, modificá\-lo para atender às suas necessidades e adicioná\-lo ao manifesto do aplicativo usando um editor de texto ou MageUI.exe.  Para obter mais informações, consulte [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md).  
  
-   Obter um certificado Authenticode.  
  
     Você deve assinar sua implantação com um certificado Authenticode.  Você pode gerar um certificado de teste usando as ferramentas de Visual Studio, MageUI.exe, ou Makecert e Pvk2Pfx.exe, ou você pode obter um certificado de uma autoridade de certificação \(CA\).  Se você optar por usar a implantação de aplicativos confiáveis, você também deve executar uma instalação única do certificado em todos os computadores de clientes.  Para obter mais informações, consulte [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md).  
  
-   Certifique\-se de que o aplicativo não tem um manifesto com informações do UAC.  
  
     Você precisará determinar se seu aplicativo contém um manifesto com informações de controle de conta de usuário \(UAC\), como um `<dependentAssembly>` elemento.  Para examinar um manifesto de aplicativo, você pode usar o Windows Sysinternals [o Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035) utilitário.  
  
     Se seu aplicativo contém um manifesto com detalhes do UAC, você deve ser reconstruirá sem as informações do UAC.  Para um projeto C\# em Visual Studio, abra as propriedades do projeto e selecione a guia do aplicativo.  No  **de manifesto** lista suspensa, selecione  **criar um aplicativo sem um manifesto**.  Para um projeto de Visual Basic em Visual Studio, abra as propriedades do projeto, selecione a guia do aplicativo e clique em  **Exibir configurações UAC**.  No arquivo de manifesto aberto, remova todos os elementos dentro do único `<asmv1:assembly>` elemento.  
  
-   Determine se o aplicativo necessita de pré\-requisitos no computador cliente.  
  
     [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]aplicativos implantados a partir de Visual Studio podem incluir um bootstrapper de pré\-requisito de instalação \(Setup. exe\) com sua implantação.  Esta explicação passo a passo cria dois manifestos necessários para uma [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação.  Você pode criar um bootstrapper pré\-requisito usando o [Tarefa GenerateBootstrapper](../msbuild/generatebootstrapper-task.md).  
  
### Para implantar um aplicativo com a ferramenta de linha de comando Mage  
  
1.  Criar um diretório onde você armazenará seus [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] arquivos de implantação.  
  
2.  No diretório de implantação que você acabou de criar, crie um subdiretório de versão.  Se esta for a primeira vez que você estiver implantando o aplicativo, nomeie o subdiretório versão 1.0.0.0.  
  
    > [!NOTE]
    >  A versão da sua implantação pode ser diferente da versão do seu aplicativo.  
  
3.  Copie todos os arquivos do aplicativo para o subdiretório de versão, incluindo arquivos executáveis, assemblies, recursos e arquivos de dados.  Se necessário, você pode criar subpastas adicionais que contêm arquivos adicionais.  
  
4.  Abrir o [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] ou Visual Studio command prompt e altere para o subdiretório de versão.  
  
5.  Crie o manifesto do aplicativo com uma chamada para Mage.  A instrução a seguir cria um manifesto de aplicativo para o código compilado para ser executado no processador Intel x86.  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    >  Certifique\-se de incluir o ponto \(.\) após a `-FromDirectory` opção, que indica o diretório atual.  Se você não incluir o ponto, você deve especificar o caminho para os arquivos de aplicativo.  
  
6.  Assinar o manifesto do aplicativo com o seu certificado Authenticode.  Substitua  *mycert.pfx* com o caminho para o arquivo de certificado.  Substitua  *passwd* com a senha para o arquivo de certificado.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
7.  Alterar para a raiz do diretório de implantação.  
  
8.  Gere o manifesto de implantação com uma chamada para Mage.  Por padrão, o Mage marcará seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação como um aplicativo instalado, de modo que ele pode ser executado tanto on\-line e off\-line.  Para tornar o aplicativo disponível somente quando o usuário está online, use o `-Install` opção com um valor de `false`.  Se você usa o padrão e os usuários instalarão o seu aplicativo de um site da Web ou compartilhamento de arquivo, certifique\-se de que o valor da `-ProviderUrl` o manifesto de pontos de opção para o local do aplicativo no servidor Web ou compartilhamento.  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. Assinar o manifesto de implantação com o seu certificado Authenticode.  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
10. Copie todos os arquivos no diretório de implantação para a mídia ou o destino de implantação.  Isso pode ser uma pasta em um site da Web ou site FTP, um compartilhamento de arquivo ou um CD\-ROM.  
  
11. Fornece aos usuários com a URL, UNC ou mídia física necessária para instalar o aplicativo.  Se você fornecer uma URL ou um UNC, você deve oferecer a seus usuários o caminho completo para o manifesto de implantação.  Por exemplo, se AppToDeploy for implantado para http:\/\/webserver01\/ no diretório AppToDeploy, o caminho completo do URL seria http:\/\/webserver01\/AppToDeploy\/AppToDeploy.application.  
  
### Para implantar um aplicativo com a ferramenta gráfica de MageUI.exe  
  
1.  Criar um diretório onde você armazenará seus [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] arquivos de implantação.  
  
2.  No diretório de implantação que você acabou de criar, crie um subdiretório de versão.  Se esta for a primeira vez que você estiver implantando o aplicativo, nomeie o subdiretório versão 1.0.0.0.  
  
    > [!NOTE]
    >  A versão da sua implantação é provavelmente diferente da versão do seu aplicativo.  
  
3.  Copie todos os arquivos do aplicativo para o subdiretório de versão, incluindo arquivos executáveis, assemblies, recursos e arquivos de dados.  Se necessário, você pode criar subpastas adicionais que contêm arquivos adicionais.  
  
4.  Inicie a ferramenta gráfica de MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
5.  Criar um novo manifesto de aplicativo selecionando  **arquivo**,  **nova**,  **O manifesto de aplicativo** no menu.  
  
6.  No padrão  **nome** de tabulação, digite o nome e número de versão desta implantação.  Especifique também o  **processador** que o aplicativo é criado, como, por exemplo, x86.  
  
7.  Selecione o  **arquivos** guia e clique nas reticências \(**...**\) botão ao lado do  **diretório de aplicativo** caixa de texto.  Aparece uma caixa de diálogo Procurar pasta.  
  
8.  Selecione o subdiretório de versão que contém os arquivos do aplicativo e clique em  **OK**.  
  
9. Se você implantará a partir do Internet Information Services \(IIS\), selecione o  **quando estiver preenchendo adiciona a extensão. Deploy a qualquer arquivo que não têm** caixa de seleção.  
  
10. Clique no  **popular** botão para adicionar todos os seus arquivos de aplicativo à lista de arquivos.  Se seu aplicativo contém mais de um arquivo executável, marcar o arquivo executável para essa implantação como o aplicativo de inicialização principal selecionando  **Ponto de entrada** da  **Tipo de arquivo** na lista suspensa.  \(Se seu aplicativo contém apenas um arquivo executável, MageUI.exe será marcá\-la para você.\)  
  
11. Selecione o  **as permissões necessárias** e selecione o nível de confiança que você precisa de seu aplicativo para assert.  O padrão é  **FullTrust**, que será adequado para a maioria dos aplicativos.  
  
12. Selecione  **arquivo**,  **Salvar como** no menu.  Uma caixa de diálogo Opções de assinatura será exibida solicitando que você assinar o manifesto de aplicativo.  
  
13. Se você tiver um certificado armazenado como um arquivo no seu sistema de arquivos, use o  **sinal com o arquivo de certificado** opção e selecione o certificado do sistema de arquivos usando as reticências \(**...**\) botão.  Digite sua senha do certificado.  
  
     \- ou \-  
  
     Se o seu certificado é mantido em um armazenamento de certificados acessível a partir de seu computador, selecione o  **assinar com certificado armazenado** opção e selecione o certificado na lista fornecida.  
  
14. Clique em  **OK** para assinar seu manifesto de aplicativo.  É exibida a caixa de diálogo Salvar como.  
  
15. Na caixa de diálogo Salvar como, especifique o diretório de versão e, em seguida, clique em  **Salvar**.  
  
16. Selecione  **arquivo**,  **nova**,  **O manifesto de implantação** no menu para criar seu manifesto de implantação.  
  
17. Sobre o  **nome** especifique um nome e número de versão para essa implantação \(1.0.0.0 neste exemplo\).  Especifique também o  **processador** que o aplicativo é criado, como, por exemplo, x86.  
  
18. Selecione o  **Descrição** guia e especificar valores para  **Publisher** e  **reconhecesset**.  \(**Produto** é o nome dado ao seu aplicativo no menu Iniciar do Windows quando seu aplicativo for instalado em um computador cliente para uso offline.\)  
  
19. Selecione o  **Opções de implantação** guia e de  **Local iniciar** texto, especifique o local do manifesto do aplicativo no servidor Web ou compartilhamento.  Por exemplo, \\\\myServer\\myShare\\AppToDeploy.application.  
  
20. Se você adicionou a extensão. Deploy em uma etapa anterior, selecione também  **extensão de nome de arquivo. Deploy uso** aqui.  
  
21. Selecione o  **Opções de atualização de** guia e especifique com que freqüência você gostaria que este aplicativo para atualizar.  Se seu aplicativo usa <xref:System.Deployment.Application.UpdateCheckInfo> para verificar se há atualizações propriamente dito, desmarque o  **esse aplicativo deve verificar as atualizações** caixa de seleção.  
  
22. Selecione o  **Aplicativo referência** guia e, em seguida, clique no  **Selecione manifesto** botão.  Aparece uma caixa de diálogo Abrir.  
  
23. Selecione o manifesto do aplicativo que você criou anteriormente e, em seguida, clique em  **Abrir**.  
  
24. Selecione  **arquivo**,  **Salvar como** no menu.  Uma caixa de diálogo Opções de assinatura será exibida solicitando que você assinar o manifesto de implantação.  
  
25. Se você tiver um certificado armazenado como um arquivo no seu sistema de arquivos, use o  **sinal com o arquivo de certificado** opção e selecione o certificado do sistema de arquivos usando as reticências \(**...**\) botão.  Digite sua senha do certificado.  
  
     \- ou \-  
  
     Se o seu certificado é mantido em um armazenamento de certificados acessível a partir de seu computador, selecione o  **assinar com certificado armazenado** opção e selecione o certificado na lista fornecida.  
  
26. Clique em  **OK** para assinar seu manifesto de implantação.  É exibida a caixa de diálogo Salvar como.  
  
27. No  **Salvar como** caixa de diálogo, mover para cima de um diretório para a raiz da sua implantação e clique  **Salvar**.  
  
28. Copie todos os arquivos no diretório de implantação para a mídia ou o destino de implantação.  Isso pode ser uma pasta em um site da Web ou site FTP, um compartilhamento de arquivo ou um CD\-ROM.  
  
29. Fornece aos usuários com a URL, UNC ou mídia física necessária para instalar o aplicativo.  Se você fornecer uma URL ou um UNC, você deve oferecer a seus usuários o caminho completo, o manifesto de implantação.  Por exemplo, se AppToDeploy for implantado para http:\/\/webserver01\/ no diretório AppToDeploy, o caminho completo do URL seria http:\/\/webserver01\/AppToDeploy\/AppToDeploy.application.  
  
## Próximas etapas  
 Quando você precisa implantar uma nova versão do aplicativo, criar um novo diretório chamado após a nova versão — por exemplo, o 1.0.0.1—and copiar os novos arquivos de aplicativo para o novo diretório.  Em seguida, você precisará seguir as etapas anteriores para criar e assinar um novo manifesto de aplicativo e atualizar e assinar o manifesto de implantação.  Tenha cuidado para especificar a mesma versão superior em ambas as Mage `-New` e `–Update` chamadas, como [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] atualiza apenas as versões superiores, com o mais significativo de inteiro mais à esquerda.  Se você usou o MageUI.exe, você poderá atualizar o manifesto de implantação ao abri\-lo, selecionando o  **Aplicativo referência** guia, clicando no  **Selecione manifesto** botão e, em seguida, selecionando o manifesto de aplicativo atualizado.  
  
## Consulte também  
 [Mage.exe \(Ferramenta de Geração e Edição de Manifesto\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(Ferramenta de Geração e Edição de Manifesto, cliente gráfico\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)   
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Manifesto de aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)