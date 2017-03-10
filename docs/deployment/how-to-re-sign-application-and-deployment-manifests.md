---
title: "Como assinar manifestos de aplicativo e implanta&#231;&#227;o novamente | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "implantação ClickOnce, assinando manifestos"
  - "implantando aplicativos [ClickOnce], assinando manifestos"
  - "implantando aplicativos, assinando manifestos"
  - "aplicativos do Office, assinando manifestos"
  - "desenvolvimento do Office no Visual Studio, assinando manifestos"
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como assinar manifestos de aplicativo e implanta&#231;&#227;o novamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Depois de fazer alterações às propriedades de implantação no manifesto do aplicativo para aplicativos Windows Forms, aplicativos de Windows Presentation Foundation de \(xbap\) ou soluções do Office, você deve assinar manifestos de aplicativos e implantação com um certificado novamente.  Esse processo ajuda a garantir que os arquivos violados não estão instalados em computadores de usuário final.  
  
 Outro cenário onde você pode assinar novamente os manifestos é quando os clientes desejam assinar o aplicativo e manifestos de implantação com seus próprios certificados.  
  
## Assinar novamente o aplicativo e implantação manifestos.  
 Este procedimento pressupõe que você já fez alterações ao seu arquivo de manifesto do aplicativo \(. manifest\).  Para obter mais informações, consulte [Como: alterar as propriedades de implantação](http://msdn.microsoft.com/pt-br/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### Para assinar novamente o aplicativo e implantação manifesta com Mage  
  
1.  Abrir um  **Prompt de comando do Visual Studio** janela.  
  
2.  Altere os diretórios para a pasta que contém os arquivos de manifesto que você deseja assinar.  
  
3.  Digite o seguinte comando para assinar o arquivo de manifesto do aplicativo.  Substitua ManifestFileName com o nome do arquivo de manifesto e a extensão.  Substitua o certificado com o caminho relativo ou totalmente qualificado do arquivo de certificado e senha com a senha do certificado.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Por exemplo, você pode executar o comando a seguir para assinar um manifesto de aplicativo para um add\-in, um aplicativo do Windows Forms ou um aplicativo de navegador de Windows Presentation Foundation.  Os certificados temporários criados por Visual Studio não são recomendados para implantação em ambientes de produção.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Digite o seguinte comando para atualizar e assinar o arquivo de manifesto de implantação, substituindo os nomes de espaço reservado como na etapa anterior.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Por exemplo, você pode executar o comando a seguir para atualizar e assinar um manifesto de implantação para um suplemento do Excel, um aplicativo Windows Forms ou um aplicativo de navegador de Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Opcionalmente, copie o manifesto de implantação mestre \(publish\\*appname*. Application\) para seu diretório de implantação da versão \(publish\\Application de programas \\*appname*\_*versão*\).  
  
## Assinar novamente o aplicativo e manifestos de implantação e atualização  
 Este procedimento pressupõe que você já fez alterações no seu aplicativo \(. manifest\) do arquivo de manifesto, mas existem outros arquivos que foram atualizados.  Quando os arquivos são atualizados, o hash que representa o arquivo também deve ser atualizado.  
  
#### Para atualizar e assinar novamente o aplicativo e implantação manifesta com Mage  
  
1.  Abrir um  **Prompt de comando do Visual Studio** janela.  
  
2.  Altere os diretórios para a pasta que contém os arquivos de manifesto que você deseja assinar.  
  
3.  Remova a extensão de arquivo. Deploy dos arquivos na pasta de saída de publicar.  
  
4.  Digite o seguinte comando para atualizar o manifesto do aplicativo com os hashes de novos para os arquivos atualizados e assinar o arquivo de manifesto do aplicativo.  Substitua ManifestFileName com o nome do arquivo de manifesto e a extensão.  Substitua o certificado com o caminho relativo ou totalmente qualificado do arquivo de certificado e senha com a senha do certificado.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Por exemplo, você pode executar o comando a seguir para assinar um manifesto de aplicativo para um add\-in, um aplicativo do Windows Forms ou um aplicativo de navegador de Windows Presentation Foundation.  Os certificados temporários criados por Visual Studio não são recomendados para implantação em ambientes de produção.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Digite o seguinte comando para atualizar e assinar o arquivo de manifesto de implantação, substituindo os nomes de espaço reservado como na etapa anterior.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Por exemplo, você pode executar o comando a seguir para atualizar e assinar um manifesto de implantação para um suplemento do Excel, um aplicativo Windows Forms ou um aplicativo de navegador de Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Adicione a extensão de arquivo. Deploy volta para os arquivos, exceto arquivos de manifesto do aplicativo e implantação.  
  
7.  Opcionalmente, copie o manifesto de implantação mestre \(publish\\*appname*. Application\) para seu diretório de implantação da versão \(publish\\Application de programas \\*appname*\_*versão*\).  
  
## Consulte também  
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md)   
 [Como habilitar configurações de segurança do ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Como definir uma zona de segurança para um aplicativo ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Como definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Como depurar um aplicativo ClickOnce com permissões restritas](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Como adicionar um fornecedor confiável a um computador cliente para aplicativos ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Como configurar o comportamento do prompt confiável do ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)