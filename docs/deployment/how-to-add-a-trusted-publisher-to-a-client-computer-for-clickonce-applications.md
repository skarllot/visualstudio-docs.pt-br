---
title: "Como adicionar um fornecedor confi&#225;vel a um computador cliente para aplicativos ClickOnce | Microsoft Docs"
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
  - "implantação de aplicativos confiáveis, editores confiáveis"
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como adicionar um fornecedor confi&#225;vel a um computador cliente para aplicativos ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Com a implantação de aplicativos confiáveis, você pode configurar computadores cliente para que seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos executados com um nível mais alto de confiança sem avisar o usuário. Os procedimentos a seguir mostram como usar a ferramenta de linha de comando CertMgr.exe para adicionar um certificado de editor para o repositório editores confiáveis em um computador cliente.  
  
 Os comandos usados variam um pouco dependendo se a autoridade de certificação \(CA\) que emitiu o certificado é parte de raiz confiável do cliente. Se um computador cliente do Windows faz parte de um domínio, ele conterá, em uma lista, autoridades de certificação que são considerados raízes confiáveis. Esta lista geralmente é configurada pelo administrador do sistema. Se seu certificado foi emitido por um essas raízes confiáveis, ou por uma autoridade de certificação que esteja associado a um desses raízes confiáveis, você pode adicionar o certificado ao armazenamento de raiz confiável do cliente. Se, por outro lado, o certificado não foi emitido por uma dessas raízes confiáveis, você deve adicionar o certificado ao armazenamento raiz confiável do cliente e editores confiáveis.  
  
> [!NOTE]
>  Você deve adicionar certificados dessa maneira em cada computador cliente que você planeja implantar uma [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo que requer permissões elevadas. Adicione os certificados manualmente ou através de um aplicativo que você distribuir aos seus clientes. Você só precisa configurar esses computadores de uma vez, após o qual você pode implantar qualquer número de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos assinados com o mesmo certificado.  
  
 Você também pode adicionar um certificado a um repositório programaticamente usando o <xref:System.Security.Cryptography.X509Certificates.X509Store> classe.  
  
 Para obter uma visão geral da implantação de aplicativos confiáveis, consulte [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md).  
  
### Para adicionar um certificado ao armazenamento de editores confiáveis sob a raiz confiável  
  
1.  Obter um certificado digital de uma autoridade de certificação.  
  
2.  Exporte o certificado no formato Base64 x. 509 \(. cer\). Para obter mais informações sobre os formatos de certificado, consulte [Exportar um certificado](http://go.microsoft.com/fwlink/?LinkId=164793).  
  
3.  No prompt de comando nos computadores cliente, execute o seguinte comando:  
  
     **certmgr.exe\-adicionar chaves públicas \- c \-s \- r localMachine TrustedPublisher**  
  
### Para adicionar um certificado ao armazenamento de editores confiáveis em uma raiz diferente  
  
1.  Obter um certificado digital de uma autoridade de certificação.  
  
2.  Exporte o certificado no formato Base64 x. 509 \(. cer\). Para obter mais informações sobre os formatos de certificado, consulte [Exportar um certificado](http://go.microsoft.com/fwlink/?LinkId=164793).  
  
3.  No prompt de comando nos computadores cliente, execute o seguinte comando:  
  
     **certmgr.exe\-adicionar good.cer \- c \-s \- r localMachine raiz**  
  
     **certmgr.exe\-adicionar good.cer \- c \-s \- r localMachine TrustedPublisher**  
  
## Consulte também  
 [Instruções passo a passo: implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md)   
 [Como habilitar configurações de segurança do ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Como definir uma zona de segurança para um aplicativo ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Como definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Como depurar um aplicativo ClickOnce com permissões restritas](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [How to: Add a Trusted Publisher to a Client Computer for ClickOnce Applications](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Como assinar manifestos de aplicativo e implantação novamente](../deployment/how-to-re-sign-application-and-deployment-manifests.md)   
 [Como configurar o comportamento do prompt confiável do ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)