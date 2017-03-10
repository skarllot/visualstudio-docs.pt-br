---
title: "ClickOnce e Authenticode | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Arquivos .pfx"
  - "Implantação do ClickOnce, Authenticode"
  - "Authenticode, ClickOnce"
  - "Implantação do ClickOnce, certificados"
  - "Implantação do ClickOnce, segurança"
ms.assetid: ab5b6712-f32a-4e33-842f-e88ab4818ccf
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce e Authenticode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Authenticode* é uma tecnologia da Microsoft que usa criptografia padrão do setor para assinar código do aplicativo com certificados digitais que verificam a autenticidade do Editor do aplicativo. Por meio de Authenticode para implantação de aplicativos, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] reduz o risco de um cavalo de Troia. Um cavalo de Troia é um vírus ou outro programa prejudicial que um terceiro mal\-intencionado geralmente como um programa legítimo provenientes de uma fonte confiável, estabelecida. Assinatura [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantações com um certificado digital é uma etapa opcional para verificar que os assemblies e arquivos não são alterados.  
  
 As seções a seguir descrevem os diferentes tipos de certificados digitais usados em Authenticode, como os certificados são validados usando certificado CAs \(autoridades\), a função de carimbo de hora em certificados e os métodos de armazenamento disponível para certificados.  
  
## Authenticode e assinatura de código  
 Um *certificado digital* é um arquivo que contém uma pública\/privada chave criptográfica, junto com os metadados que descrevem o publicador para quem o certificado foi emitido e a agência que emitiu o certificado.  
  
 Há vários tipos de certificados Authenticode. Cada um é configurado para diferentes tipos de assinatura. Para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos, você deve ter um certificado Authenticode que é válido para a assinatura de código. Se você tentar entrar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo com outro tipo de certificado, como um certificado digital de email, ele não funcionará. Para obter mais informações, consulte [Introdução à assinatura de código](http://go.microsoft.com/fwlink/?LinkId=179452).  
  
 Você pode obter um certificado de assinatura de código em uma destas três maneiras:  
  
-   Compre um de um fornecedor de certificado.  
  
-   Receba um de um grupo em sua organização responsável pela criação de certificados digitais.  
  
-   Gerar seu próprio certificado com MakeCert.exe, que é incluído com o [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  
  
### Como usar autoridades de certificação ajuda os usuários  
 Normalmente é chamado de um certificado gerado usando o utilitário MakeCert.exe um *self\-cert* ou um *teste cert*. Esse tipo de certificado funciona da mesma forma que um arquivo. snk funciona no .NET Framework. Ele consiste exclusivamente em um par de chaves criptográficas pública\/privada e não contém nenhuma informação verificável sobre o publicador. Você pode usar certificados de autoatendimento para implantar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos com alta confiança em uma intranet. No entanto, quando esses aplicativos são executados em um computador cliente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] identificará como proveniente de um editor desconhecido. Por padrão, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos assinados com certificados de autoatendimento e implantados pela Internet não é possível utilizar a implantação de aplicativos confiáveis.  
  
 Por outro lado, se você receber um certificado de uma autoridade de certificação, como um fornecedor de certificado ou a um departamento dentro da sua empresa, o certificado oferece mais segurança para seus usuários. Ele não só identifica o Editor de software assinado, mas ele verifica essa identidade, verificando a autoridade de certificação que assinou. Se a autoridade de certificação não é a autoridade raiz, Authenticode serão também "cadeia" volta para a autoridade raiz para verificar se a autoridade de certificação está autorizada para emitir certificados. Para maior segurança, você deve usar um certificado emitido por uma autoridade de certificação sempre que possível.  
  
 Para obter mais informações sobre como gerar certificados de autoatendimento, consulte [Makecert.exe \(Ferramenta de Criação de Certificado\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md).  
  
### Carimbos de hora  
 Os certificados usados para assinar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos expiram após um determinado período de tempo, normalmente há doze meses. Para eliminar a necessidade de constantemente assinar novamente os aplicativos com novos certificados, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] suporta o carimbo de hora. Quando um aplicativo é assinado com um carimbo de hora, seu certificado continuará a ser aceito mesmo após a expiração, contanto que o carimbo de hora é válido. Isso permite que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos com certificados expirados, mas os carimbos de hora válidos, baixar e executar. Ele também permite que aplicativos instalados com certificados expirados para continuar a baixar e instalar atualizações.  
  
 Para incluir um carimbo de hora em um servidor de aplicativos, um servidor de carimbo de hora deve estar disponível. Para obter informações sobre como selecionar um servidor de carimbo de hora, consulte [Como assinar manifestos de aplicativo e implantação](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
### Atualizar certificados expirados  
 Em versões anteriores do .NET Framework, atualizando um aplicativo cujo certificado expirou pode fazer com que o aplicativo parar de funcionar. Para resolver esse problema, use um dos seguintes métodos:  
  
-   Atualize o .NET Framework versão 2.0 SP1 ou posterior no Windows XP, versão 3.5 ou posterior no Windows Vista.  
  
-   Desinstalar o aplicativo e reinstalar uma nova versão com um certificado válido.  
  
-   Crie um conjunto de linha de comando que atualiza o certificado. Informações passo a passo sobre esse processo podem ser encontradas em [925521 de artigo de suporte Microsoft](http://go.microsoft.com/fwlink/?LinkId=179454).  
  
### Armazenamento de certificados  
  
-   Você pode armazenar certificados em um arquivo. pfx no seu sistema de arquivos, ou você pode armazená\-los dentro de um contêiner de chave. Um usuário em um domínio do Windows pode ter um número de contêineres de chave. Por padrão, MakeCert.exe irá armazenar certificados em seu contêiner de chave particular, a menos que você especifique que ela deve salvá\-lo em um. pfx em vez disso. Mage.exe e MageUI.exe, o [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] Ferramentas para criar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantações, permitem que você use certificados armazenados em qualquer modo.  
  
## Consulte também  
 [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md)   
 [Mage.exe \(Ferramenta de Geração e Edição de Manifesto\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)