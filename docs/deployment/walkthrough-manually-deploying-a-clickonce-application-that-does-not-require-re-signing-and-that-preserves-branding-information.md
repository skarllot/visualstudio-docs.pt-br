---
title: "Instru&#231;&#245;es passo a passo: implantando manualmente um aplicativo ClickOnce que n&#227;o requer nova assinatura e que preserva informa&#231;&#245;es de identidade visual | Microsoft Docs"
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
  - "identidade visual"
  - "Aplicativos ClickOnce, implantados por outros"
  - "implantação ClickOnce, manualmente"
  - "implantação ClickOnce, ferramentas SDK"
  - "implantações de cliente"
  - "manifestos [ClickOnce]"
  - "implantações ClickOnce manuais"
  - "identidade visual e implantação múltipla de ClickOnce"
  - "informações de identidade visual preservadas"
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: implantando manualmente um aplicativo ClickOnce que n&#227;o requer nova assinatura e que preserva informa&#231;&#245;es de identidade visual
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando você cria um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo e dê a ele a um cliente para publicar e implantar, o cliente teve tradicionalmente atualizar o manifesto de implantação e assinar novamente a ele. Enquanto ainda é o método preferencial na maioria dos casos, o.NET Framework 3.5 permite que você crie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantações que podem ser implantadas por clientes, sem a necessidade de gerar um novo manifesto de implantação.  Para obter mais informações, consulte [Implantando aplicativos ClickOnce para servidores de teste e produção sem assinar novamente](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md).  
  
 Quando você cria um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo e dê a ele a um cliente para publicar e implantar, o aplicativo pode usar a identificação de marca do cliente ou pode preservar a sua marca.  Por exemplo, se o aplicativo for um único aplicativo proprietário, você talvez queira preservar sua marca.  Se o aplicativo é altamente personalizado para cada cliente, convém usar a identificação de marca do cliente.  A.NET Framework 3.5 permite preservar sua marca, informações sobre a editora e assinatura de segurança ao conceder para implantar um aplicativo para uma organização.  Para obter mais informações, consulte [Criando aplicativos ClickOnce para a implantação por terceiros](../deployment/creating-clickonce-applications-for-others-to-deploy.md).  
  
> [!NOTE]
>  Esta explicação passo a passo você cria implantações manualmente usando a ferramenta de linha de comando Mage ou a ferramenta gráfica MageUI.exe.  Para obter mais informações sobre implantações manuais, consulte [Instruções passo a passo: implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Pré-requisitos  
 Para executar as etapas nesta explicação passo a passo, você precisa do seguinte:  
  
-   Um aplicativo Windows Forms que você está pronto para implantar.  Este aplicativo será ser conhecido como WindowsFormsApp1.  
  
-   Visual Studio ou o SDK do Windows.  
  
### Para implantar um aplicativo de ClickOnce com vários de implantação e suporte de identidade visual usando o Mage  
  
1.  Abra um prompt de comando Visual Studio ou um [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] prompt de comando e altere para o diretório no qual você armazenará seus [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] arquivos.  
  
2.  Crie um diretório chamado após a versão atual da sua implantação.  Se esta for a primeira vez que você estiver implantando o aplicativo, você provavelmente escolherá 1.0.0.0.  
  
    > [!NOTE]
    >  A versão da sua implantação pode ser distinta da versão de seus arquivos de aplicativo.  
  
3.  Crie uma subpasta chamada bin e copiar todos os arquivos do aplicativo aqui, incluindo arquivos executáveis, assemblies, recursos e arquivos de dados.  
  
4.  Gere o manifesto de aplicativo com uma chamada para Mage.  
  
    ```  
    mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
    ```  
  
5.  Assinar o manifesto do aplicativo com o seu certificado digital.  
  
    ```  
    mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
    ```  
  
6.  Gere o manifesto de implantação com uma chamada para Mage.  Por padrão, o Mage marcará seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação como um aplicativo instalado, de modo que ele pode ser executado tanto on\-line e off\-line.  Para tornar o aplicativo disponível somente quando o usuário está online, use o `-i` argumento com um valor de  `f`.  Uma vez que este aplicativo será aproveitar o recurso de implantação de vários, excluir o `-providerUrl` argumento para Mage.  \(Nas versões do.NET Framework anterior à versão 3.5, excluindo `-providerUrl` para um aplicativo offline resultará em erro.\)  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
    ```  
  
7.  Não assine o manifesto de implantação.  
  
8.  Forneça todos os arquivos para o cliente, quem irá implantar o aplicativo em sua rede.  
  
9. Neste ponto, o cliente deve assinar o manifesto de implantação com o seu próprio certificado gerado automaticamente.  Por exemplo, se o cliente trabalha para uma empresa chamada Adventure Works, ele pode gerar um certificado auto\-assinado usando a ferramenta Makecert.  Em seguida, use a ferramenta Pvk2pfx.exe para combinar os arquivos criados pelo Makecert em um arquivo PFX que pode ser passado para Mage.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. Em seguida, o cliente usa esse certificado para assinar o manifesto de implantação.  
  
    ```  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. O cliente implanta o aplicativo para seus usuários.  
  
### Para implantar um aplicativo de ClickOnce com vários de implantação e suporte de identidade visual usando MageUI.exe  
  
1.  Abra um prompt de comando Visual Studio ou um [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] prompt de comando e navegue até o diretório no qual você armazenará seus [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] arquivos.  
  
2.  Crie uma subpasta chamada bin e copiar todos os arquivos do aplicativo aqui, incluindo arquivos executáveis, assemblies, recursos e arquivos de dados.  
  
3.  Crie um subdiretório nomeado de acordo com a versão atual da sua implantação.  Se esta for a primeira vez que você estiver implantando o aplicativo, você provavelmente escolherá 1.0.0.0.  
  
    > [!NOTE]
    >  A versão da sua implantação pode ser distinta da versão de seus arquivos de aplicativo.  
  
4.  Mova o diretório \\bin para o diretório que você criou na etapa 2.  
  
5.  Inicie a ferramenta gráfica MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
6.  Criar um novo manifesto de aplicativo selecionando  **arquivo**,  **nova**,  **O manifesto de aplicativo** no menu.  
  
7.  No padrão  **nome** Insira o nome e número de versão desta implantação.  Além disso, fornecer um valor para  **Publisher**, que será usado como o nome da pasta para o link de atalho do aplicativo no menu Iniciar quando ele for implantado.  
  
8.  Selecione o  **Opções de aplicativos** guia e clique em  **O manifesto de aplicativo de uso para confiar em informações**.  Isso permitirá a identificação de marca de terceiros para este [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  
  
9. Selecione o  **arquivos** guia e clique no  **Procurar** o botão ao lado da caixa de texto do diretório de aplicativo.  
  
10. Selecione o diretório que contém seus arquivos de aplicativo que você criou na etapa 2 e, em seguida, clique em  **OK** na caixa de diálogo de seleção de pasta.  
  
11. Clique no  **popular** botão para adicionar todos os seus arquivos de aplicativo à lista de arquivos.  Se seu aplicativo contém mais de um arquivo executável, marcar o arquivo executável para essa implantação como o aplicativo de inicialização principal selecionando  **Ponto de entrada** da  **Tipo de arquivo** na lista suspensa.  \(Se seu aplicativo contém apenas um arquivo executável, MageUI.exe será marcá\-la para você.\)  
  
12. Selecione o  **as permissões necessárias** e selecione o nível de confiança que você precisa declarar seu aplicativo.  O padrão é  **Confiança total**, que poderão ser apropriado para a maioria dos aplicativos.  
  
13. Selecione  **arquivo**,  **Salvar** no menu e salvar o manifesto do aplicativo.  Você será solicitado para assinar o manifesto de aplicativo quando você salvá\-lo.  
  
14. Se você tiver um certificado armazenado como um arquivo no seu sistema de arquivos, use o  **sinal que o arquivo de certificado** opção e selecione o certificado do sistema de arquivos usando as reticências \(**...**\) botão.  
  
     \- ou \-  
  
     Se o seu certificado é mantido em um armazenamento de certificados que pode ser acessado a partir do seu computador, selecione o  **sinal com opção de certificado armazenado**e selecione o certificado da lista fornecida.  
  
15. Selecione  **arquivo**,  **nova**,  **O manifesto de implantação** no menu para criar seu manifesto de implantação e no  **nome** da sala, forneça um nome e número de versão \(1.0.0.0 neste exemplo\).  
  
16. Alterne para o  **atualização** guia e especificar com que freqüência você deseja que este aplicativo para atualizar.  Se seu aplicativo usa a [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API de implantação para verificar se há atualizações propriamente dito, desmarque a caixa de seleção  **esse aplicativo deve verificar as atualizações**.  
  
17. Alterne para o  **Aplicativo referência** guia.  Você pode preencher previamente todos os valores nesta guia clicando o  **Selecione manifesto** botão e selecionando o manifesto do aplicativo que você criou nas etapas anteriores.  
  
18. Escolha  **Salvar** e salvar o manifesto de implantação em disco.  Você será solicitado para assinar o manifesto de aplicativo quando você salvá\-lo.  Clique em  **Cancelar** para salvar o manifesto sem assiná\-lo.  
  
19. Forneça todos os arquivos do aplicativo para o cliente.  
  
20. Neste ponto, o cliente deve assinar o manifesto de implantação com o seu próprio certificado gerado automaticamente.  Por exemplo, se o cliente trabalha para uma empresa chamada Adventure Works, ele pode gerar um certificado auto\-assinado usando a ferramenta Makecert.  Em seguida, use a ferramenta Pvk2pfx.exe para combinar os arquivos criados pelo Makecert em um arquivo PFX que pode ser passado para MageUI.exe.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. Com o certificado gerado, o cliente agora assina o manifesto de implantação abrindo o manifesto de implantação em MageUI.exe e, em seguida, salvá\-lo.  Quando for exibida a caixa de diálogo de assinatura, o cliente seleciona  **sinal que o arquivo de certificado** opção e escolhe o arquivo PFX, ele foi salvo no disco.  
  
22. O cliente implanta o aplicativo para seus usuários.  
  
## Próximas etapas  
  
## Consulte também  
 [Mage.exe \(Ferramenta de Geração e Edição de Manifesto\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(Ferramenta de Geração e Edição de Manifesto, cliente gráfico\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)   
 [Makecert.exe \(Ferramenta de Criação de Certificado\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md)