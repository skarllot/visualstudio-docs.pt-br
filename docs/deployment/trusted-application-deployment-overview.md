---
title: "Vis&#227;o geral da implanta&#231;&#227;o de aplicativos confi&#225;veis | Microsoft Docs"
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
  - "Implantação do ClickOnce, instalar sem avisar"
  - "Implantação do ClickOnce, segurança"
  - "implantação de aplicativo confiável"
ms.assetid: b24a1702-8fbe-45b1-87a0-9618a0708f1d
caps.latest.revision: 31
caps.handback.revision: 31
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vis&#227;o geral da implanta&#231;&#227;o de aplicativos confi&#225;veis
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico fornece uma visão geral de como implantar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos que têm permissões elevadas usando a tecnologia de implantação de aplicativos confiáveis.  
  
 Confiável parte da implantação de aplicativo a [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tecnologia de implantação, torna mais fácil para as organizações de qualquer tamanho de conceder permissões adicionais a um aplicativo gerenciado de maneira mais segura e mais segura, sem nenhum aviso ao usuário. Com a implantação de aplicativos confiáveis, uma organização pode configurar apenas um computador cliente para ter uma lista de editores confiáveis, que são identificados usando certificados Authenticode. Daí em diante, qualquer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo assinado por um destes trusted publishers recebe um nível mais alto de confiança.  
  
> [!NOTE]
>  Confiável a que implantação de aplicativos requer configuração única do computador do usuário. Em ambientes de área de trabalho gerenciados, essa configuração pode ser executada usando a diretiva global. Se este for não o que você deseja para seu aplicativo, use elevação de permissões. Para obter mais informações, consulte [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## Noções básicas sobre implantação de aplicativos confiáveis  
 A tabela a seguir mostra os objetos e funções que estão envolvidas na implantação de aplicativos confiáveis.  
  
|Objeto ou função|Descrição|  
|----------------------|---------------|  
|administrador|A entidade organizacional responsável por atualizar e manter os computadores cliente|  
|Gerenciador de confiança|O subsistema dentro o common language runtime \(CLR\) responsável por impor a segurança do aplicativo cliente.|  
|Publisher|A entidade que grava e mantém o aplicativo.|  
|implantador|A entidade que empacota e distribui o aplicativo para usuários.|  
|certificado|Uma assinatura criptográfica que consiste em uma chave pública e privada; Geralmente, emitidos por uma autoridade de certificação \(CA\) que pode comprovar sua autenticidade.|  
|Certificado Authenticode|Um certificado com metadados incorporados descrever, entre outras coisas, os usos para o qual o certificado pode ser empregado.|  
|autoridade de certificação|Uma organização que verifica a identidade de editores e emite os certificados são inseridos com metadados do publicador.|  
|autoridade raiz|Uma autoridade de certificação que autoriza a outras autoridades de certificação para emitir certificados.|  
|contêiner de chave|Um espaço de armazenamento lógico no Microsoft Windows para o armazenamento de certificados.|  
|editor confiável|Um publicador cujo certificado Authenticode foi adicionado a uma lista de certificados confiáveis \(CTL\) em um computador cliente.|  
  
 Em organizações maiores, o publicador e o implantador são frequentemente duas entidades separadas:  
  
-   O Editor é o grupo que cria o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  
  
-   O implantador é o grupo, geralmente o departamento de TI \(tecnologia\) de informações, que distribui [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo para desktops corporativos.  
  
 Você deve seguir estas etapas para tirar proveito da implantação de aplicativos confiáveis:  
  
1.  Obter um certificado para o publicador.  
  
2.  Adicione o publicador para o repositório editores confiáveis em todos os clientes.  
  
3.  Criar seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  
  
4.  Assinar o manifesto de implantação com o certificado do Editor.  
  
5.  Publica a implantação do aplicativo em computadores cliente.  
  
### Obter um certificado para o publicador  
 Certificados digitais são um componente principal do sistema de segurança e autenticação do Microsoft Authenticode. Authenticode é uma parte padrão do sistema operacional Windows. Todos os [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos devem ser assinados com um certificado digital, independentemente se eles participarem de implantação de aplicativos confiáveis. Para obter uma explicação completa do funcionamento do Authenticode com [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], consulte [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md).  
  
### Adicionar o publicador para o repositório editores confiáveis  
 Para o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo receber um nível mais alto de confiança, você deve adicionar o certificado como um editor confiável para cada computador cliente no qual o aplicativo será executado. Para executar essa tarefa é uma configuração única. Depois de concluído, você pode implantar tantos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos assinados com um certificado de editor como quiser e eles serão executados com confiança alta.  
  
 Se você estiver implantando seu aplicativo em um ambiente de área de trabalho gerenciado; Por exemplo, uma intranet corporativa executando o sistema operacional Windows; Você pode adicionar editores confiáveis ao armazenamento do cliente, criando uma nova lista de certificados confiáveis \(CTL\) com a diretiva de grupo. Para obter mais informações, consulte [criar uma lista de certificados confiáveis para um objeto de diretiva de grupo](http://go.microsoft.com/fwlink/?LinkId=102576).  
  
 Se não estiver implantando seu aplicativo em um ambiente de área de trabalho gerenciado, você tem as seguintes opções para adicionar um certificado ao armazenamento de editores confiáveis:  
  
-   O <xref:System.Security.Cryptography?displayProperty=fullName> namespace.  
  
-   CertMgr.exe, que é um componente do Internet Explorer e, portanto, existe no Windows 98 e todas as versões posteriores. Para obter mais informações, consulte [Certmgr.exe \(ferramenta Gerenciador de Certificados\)](../Topic/Certmgr.exe%20\(Certificate%20Manager%20Tool\).md).  
  
### Criar um aplicativo ClickOnce  
 Um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo é um [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] aplicativo cliente combinados com os arquivos de manifesto que descrevem o aplicativo e fornecem parâmetros de instalação. Você pode ativar o seu programa em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos usando o **publicar** do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Como alternativa, você pode gerar todos os arquivos necessários para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação usando as ferramentas incluídas com o [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Para obter etapas detalhadas sobre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação, consulte [Instruções passo a passo: implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
 Implantação de aplicativos confiáveis é específica para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], e só pode ser usada com [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos.  
  
### Assinar a implantação  
 Depois de obter seu certificado, você deve usá\-lo para assinar sua implantação. Se você estiver implantando seu aplicativo usando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Assistente de publicação, o assistente irá gerar automaticamente um certificado de teste para você se você não especificou um certificado por conta própria. Você também pode usar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] janela do Designer de projeto, no entanto, para fornecer um certificado fornecido por uma autoridade de certificação.  Consulte também [como: publicar um aplicativo ClickOnce usando o Assistente de publicação](http://msdn.microsoft.com/library/31kztyey\(v=vs.110\)) ou [como: publicar um aplicativo ClickOnce usando o Assistente de publicação](http://msdn.microsoft.com/library/31kztyey\(v=vs.110\)).  
  
> [!CAUTION]
>  Não é recomendável que o aplicativo ser implantado com um certificado de teste.  
  
 Você também pode assinar o aplicativo usando as ferramentas de Mage.exe ou MageUI.exe SDK. Para obter mais informações, consulte [Instruções passo a passo: implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Para obter uma lista completa de opções de linha de comando relacionadas à assinatura de implantação, consulte [Mage.exe \(Ferramenta de Geração e Edição de Manifesto\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md).  
  
### Publicar o aplicativo  
 Assim que tiver assinado o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestos, o aplicativo está pronto para publicar no seu local de instalação. O local de instalação pode ser um servidor Web, um compartilhamento de arquivos ou no disco local. Quando um cliente acessa o manifesto de implantação pela primeira vez, o Gerenciador de confiança deve escolher se o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo tenha autoridade ou não seja executado em um nível mais alto de confiança por um instalado confiável publicador. O Gerenciador de confiança faz esta escolha comparando o certificado usado para assinar a implantação com os certificados armazenados no editor confiável do cliente armazenar. Se o Gerenciador de confiança encontrar uma correspondência, o aplicativo é executado com confiança alta.  
  
## Elevação de permissões e implantação de aplicativos confiáveis  
 Se o fornecedor atual não for um fornecedor confiável, o Gerenciador de confiança usará elevação de permissões para consultar o usuário sobre se ele deseja conceder que permissões elevadas do seu aplicativo. No entanto, se a elevação de permissões é desabilitada pelo administrador, o aplicativo não pode obter permissão para executar. O aplicativo não será executado e nenhuma notificação será exibida para o usuário. Para obter mais informações sobre a elevação de permissões, consulte [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## Limitações de implantação de aplicativos confiáveis  
 Você pode usar a implantação de aplicativos confiáveis para conceder confiança elevada [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos implantados pela Web ou por meio de um compartilhamento de arquivo corporativo. Você não precisa usar a implantação de aplicativos confiáveis para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos distribuídos em um CD, porque, por padrão, esses aplicativos recebem confiança total.  
  
## Consulte também  
 [Mage.exe \(Ferramenta de Geração e Edição de Manifesto\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [Instruções passo a passo: implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)