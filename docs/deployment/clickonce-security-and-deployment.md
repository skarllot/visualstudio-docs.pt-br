---
title: "Seguran&#231;a e implanta&#231;&#227;o do ClickOnce | Microsoft Docs"
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
  - "implantação ClickOnce"
  - "implantando aplicativos [ClickOnce]"
  - "publicando, ClickOnce"
  - "Aplicativos do Windows, implantação ClickOnce"
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
caps.latest.revision: 32
caps.handback.revision: 32
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Seguran&#231;a e implanta&#231;&#227;o do ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]é uma tecnologia de implantação que permite que você crie aplicativos AutoAtualizáveis baseados no Windows que podem ser instalados e executados com interação mínima do usuário. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornece suporte completo para a publicação e atualização de aplicativos implantados com a tecnologia de ClickOnce, se você tiver desenvolvido seus projetos com Visual Basic e C\# Visual.  Para obter informações sobre como implantar aplicativos do Visual C\+\+, consulte [ClickOnce Implantação para aplicativos do Visual C\+\+](/visual-cpp/ide/clickonce-deployment-for-visual-cpp-applications).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]implantação supera três grandes problemas na implantação:  
  
-   **Dificuldades na atualização de aplicativos.** Com a implantação de Microsoft Windows Installer, sempre que um aplicativo é atualizado, o usuário pode instalar uma atualização, um arquivo msp e aplicá\-lo para o produto instalado; com [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação, você pode fornecer atualizações automaticamente.  Somente as partes do aplicativo que foram alterados são baixadas e, em seguida, o aplicativo atualizado é reinstalado a partir de uma nova pasta lado a lado.  
  
-   **Impacto para o computador do usuário.** Com a implantação do Windows Installer, aplicativos quase sempre utilizam componentes compartilhados, com a possibilidade de conflitos de versão; com [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação, cada aplicativo é independente e não pode interferir com outros aplicativos.  
  
-   **Permissões de segurança.** Implantação do Windows Installer requer permissões administrativas e permite que somente a instalação do usuário limitado;  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]implantação permite que os usuários não administrativos instalar e concede somente essas permissões de segurança de acesso ao código necessárias para o aplicativo.  
  
 No passado, esses problemas, às vezes, causados aos desenvolvedores decide criar aplicativos da Web em vez de aplicativos baseados no Windows, sacrificar uma interface do usuário avançada para facilitar a instalação.  Usando aplicativos implantados usando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], você pode ter o melhor de ambas as tecnologias.  
  
## O que é um aplicativo de ClickOnce?  
 A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo é qualquer Windows Presentation Foundation \(XBAP\), Windows Forms \(. exe\), o aplicativo de console \(. exe\) ou solução do Office \(. dll\) publicado com [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tecnologia.  Você pode publicar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo de três maneiras diferentes: a partir de uma página da Web, de um compartilhamento de arquivo de rede ou mídia como, por exemplo, um CD\-ROM.  A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo pode ser instalado no computador de um usuário final e executado localmente, mesmo quando o computador está off\-line, ou ele pode ser executado em um modo somente online sem permanentemente instalar qualquer coisa no computador do usuário final.  Para obter mais informações, consulte [Escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]aplicativos podem ser independentes; eles podem verificar as versões mais recentes, como eles se tornam disponíveis e substituem automaticamente qualquer arquivo atualizado.  O desenvolvedor pode especificar o comportamento de atualização; um administrador de rede também pode controlar atualizar estratégias, por exemplo, marcando uma atualização como obrigatória.  As atualizações podem também ser revertidas para uma versão anterior do usuário final ou por um administrador.  Para obter mais informações, consulte [Escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Porque [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos são isolados, instalação ou execução de um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo não é possível interromper aplicativos existentes.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]os aplicativos são independentes; cada [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo está instalado e executado a partir de um seguro por usuário, cache por aplicativo.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]aplicativos executados em zonas de segurança da Internet ou Intranet.  Se necessário, o aplicativo pode solicitar permissões de segurança elevadas.  Para obter mais informações, consulte [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## Como funciona a segurança de ClickOnce  
 O núcleo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] segurança é baseada em certificados, diretivas de segurança de acesso de código e o prompt de confiança de ClickOnce.  
  
### Certificados  
 Certificados Authenticode são usados para verificar a autenticidade do Editor do aplicativo.  Usando o Authenticode para implantação de aplicativos, o ClickOnce ajuda a impedir que um programa mal\-intencionado representando a mesmo como um programa legítimo proveniente de uma fonte confiável estabelecida.  Opcionalmente, os certificados também podem ser usados para assinar o aplicativo e manifestos de implantação para provar que os arquivos não foi adulterados.  Para obter mais informações, consulte [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md).  Certificados também podem ser usados para configurar computadores cliente ter uma lista de editores confiáveis.  Se um aplicativo proveniente de um editor confiável, ele pode ser instalado sem qualquer interação do usuário.  Para obter mais informações, consulte [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md).  
  
### Segurança de Acesso de código  
 Code access security ajuda a limitar o acesso que código tem a recursos protegidos.  Na maioria dos casos, você pode escolher as zonas da Internet ou Intranet Local, para limitar as permissões.  Uso o  **Security** de página na  **projetoDesigner** para solicitar a zona apropriada para o aplicativo.  Você também pode depurar aplicativos com permissões restritas para emular a experiência do usuário final.  Para obter mais informações, consulte [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
### Prompt confiável ClickOnce  
 Se o aplicativo solicita mais permissões do que a zona permite, o usuário final pode ser solicitado a tomar uma decisão de confiança.  O usuário final pode decidir se os aplicativos de ClickOnce como, por exemplo, aplicativos Windows Forms, aplicativos de Windows Presentation Foundation, aplicativos de console, aplicativos de navegador XAML e soluções do Office são confiáveis para executar.  Para obter mais informações, consulte [Como configurar o comportamento do prompt confiável do ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## Como funciona a implantação de ClickOnce  
 O núcleo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] a arquitetura de implantação é baseada em dois arquivos de manifesto XML: um manifesto de aplicativo e um manifesto de implantação.  Os arquivos são usados para descrever onde os aplicativos de ClickOnce são instalados a partir, como eles são atualizados e quando elas são atualizadas.  
  
### Publicando aplicativos ClickOnce  
 O manifesto do aplicativo descreve o aplicativo propriamente dito.  Isso inclui os assemblies, as dependências e os arquivos que compõem o aplicativo, as permissões necessárias e o local onde as atualizações estarão disponíveis.  O desenvolvedor do aplicativo autores o manifesto do aplicativo usando o Assistente de publicação na Visual Studio ou a geração de manifesto e a ferramenta de edição \(Mage\) in a [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  Para obter mais informações, consulte [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md).  
  
 O manifesto de implantação descreve como o aplicativo é implantado.  Isso inclui o local do manifesto do aplicativo e a versão do aplicativo que os clientes devem executar.  
  
### Ajuda para Distribuir Aplicativos ClickOnce  
 Depois de criado, o manifesto de implantação é copiado para o local de implantação.  Isso pode ser um servidor Web, compartilhamento de arquivos de rede ou mídia como, por exemplo, um CD.  O manifesto do aplicativo e todos os arquivos de aplicativo também são copiados para um local de implantação que está especificado no manifesto de implantação.  Isso pode ser o mesmo que o local de implantação, ou pode ser um local diferente.  Ao usar o  **Assistente de publicação** em Visual Studio, as operações de cópia são executadas automaticamente.  
  
### Instalando aplicativos de ClickOnce  
 Depois de ser implantado para o local de implantação, os usuários finais podem baixar e instalar o aplicativo clicando no ícone que representa o arquivo de manifesto de implantação em uma página da Web ou em uma pasta.  Na maioria dos casos, o usuário final é apresentado com uma caixa de diálogo perguntando ao usuário para confirmar a instalação, depois que ela possa prosseguir e o aplicativo é iniciado sem intervenção adicional.  Em casos onde o aplicativo requer permissões elevadas, ou se o aplicativo não está assinado por um certificado confiável, a caixa de diálogo também solicita que o usuário para conceder permissão antes de continua a instalação.  Apesar de ClickOnce instalações por usuário, elevação de permissões pode ser necessária se não existem pré\-requisitos que exigem privilégios de administrador.  Para obter mais informações sobre permissões elevadas, consulte [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md).  
  
 Certificados podem ser confiáveis no nível de máquina ou enterprise, para que os aplicativos de ClickOnce assinados com um certificado confiável podem instalar silenciosamente.  Para obter mais informações sobre certificados confiáveis, consulte [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md).  
  
 O aplicativo pode ser adicionado para o usuário  **Iniciar** menu e obtenha o  **Adicionar ou remover programas** grupo na  **Painel de controle**.  Ao contrário de outras tecnologias de implantação, nada é adicionado a  **Arquivos de programa** pasta ou o registro e sem direitos administrativos são necessários para instalação  
  
> [!NOTE]
>  Também é possível impedir que o aplicativo seja adicionado à  **Iniciar** menu e  **Adicionar ou remover programas** group, em vigor tornando\-se comportam como um aplicativo da Web.  Para obter mais informações, consulte [Escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
### Atualização de aplicativos de ClickOnce  
 Quando os desenvolvedores de aplicativos criam uma versão atualizada do aplicativo, eles gerar um novo manifesto de aplicativo e copiar arquivos para um local de implantação — normalmente uma pasta irmã para a pasta de implantação do aplicativo original.  O administrador atualiza o manifesto de implantação para apontar para o local da nova versão do aplicativo.  
  
> [!NOTE]
>  O  **Assistente de publicação** no Visual Studio, pode ser usado para executar essas etapas.  
  
 Além do local de implantação, o manifesto de implantação também contém um local de atualização \(um página da Web ou arquivo compartilhamento de rede\), onde o aplicativo verifica versões atualizadas.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] **Publicar** propriedades são usadas para especificar quando e com que freqüência o aplicativo deve verificar as atualizações.  O comportamento de atualização pode ser especificado no manifesto de implantação, ou pode ser apresentado como opções de usuário na interface do usuário do aplicativo por meio do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] APIs.  Além disso,  **Publicar** propriedades podem ser empregadas para tornar as atualizações obrigatórias ou reverter para uma versão anterior.  Para obter mais informações, consulte [Escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
### Instaladores de terceiros  
 Você pode personalizar seu instalador ClickOnce para instalar os componentes de terceiros com o seu aplicativo.  Você deve ter o pacote redistribuível \(arquivo. exe ou. msi\) e descrever o pacote com um manifesto de produto neutralidade de idioma e um manifesto do pacote de idioma específico.  Para obter mais informações, consulte [Criando pacotes de bootstrapper](../deployment/creating-bootstrapper-packages.md).  
  
## Ferramentas de ClickOnce  
 A tabela a seguir mostra as ferramentas que você pode usar para gerar, editar, assinar e assinar novamente os manifestos de aplicativo e implantação.  
  
|Ferramenta|Descrição|  
|----------------|---------------|  
|[Página Segurança, Designer de Projeto](../ide/reference/security-page-project-designer.md)|Os manifestos de aplicativo e implantação de sinais.|  
|[Página de Publicação, Designer de Projeto](../ide/reference/publish-page-project-designer.md)|Gera e edita os manifestos de aplicativo e implantação para aplicativos de Visual Basic e C\# Visual.|  
|[Mage.exe \(Ferramenta de Geração e Edição de Manifesto\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)|Gera os manifestos de aplicativo e implantação para aplicativos de Visual Basic, Visual C\+\+ e Visual C\#.<br /><br /> Assina e re\-signs os manifestos de aplicativo e implantação.<br /><br /> Pode ser executado a partir de scripts em lotes e o prompt de comando.|  
|[MageUI.exe \(Ferramenta de Geração e Edição de Manifesto, cliente gráfico\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)|Gera e edita os manifestos de aplicativo e implantação.<br /><br /> Assina e re\-signs os manifestos de aplicativo e implantação.|  
|[Tarefa GenerateApplicationManifest](../msbuild/generateapplicationmanifest-task.md)|Gera o manifesto do aplicativo.<br /><br /> Pode ser executado a partir do MSBuild.  Para obter mais informações, consulte [Referência do MSBuild](../msbuild/msbuild-reference.md).|  
|[Tarefa GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)|Gera o manifesto de implantação.<br /><br /> Pode ser executado a partir do MSBuild.  Para obter mais informações, consulte [Referência do MSBuild](../msbuild/msbuild-reference.md).|  
|[Tarefa SignFile](../msbuild/signfile-task.md)|Os manifestos de aplicativo e implantação de sinais.<br /><br /> Pode ser executado a partir do MSBuild.  Para obter mais informações, consulte [Referência do MSBuild](../msbuild/msbuild-reference.md).|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|Desenvolva seu próprio aplicativo para gerar os manifestos de aplicativo e implantação.|  
  
 A seguinte tabela mostra a.NET Framework versão necessária para oferecer suporte a aplicativos de ClickOnce nesses navegadores.  
  
|Navegador|.NET Framework versão|  
|---------------|---------------------------|  
|Internet Explorer|2.0, 3.0, 3.5, 3.5 SP1, 4|  
|Firefox|2.0 SP1, 3.5 SP1, 4|  
  
## Consulte também  
 [Implantação do ClickOnce no Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)   
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Implantando componentes do COM com o ClickOnce](../deployment/deploying-com-components-with-clickonce.md)   
 [Compilando aplicativos ClickOnce a partir da linha de comando](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [Depurando aplicativos ClickOnce que usam System.Deployment.Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)