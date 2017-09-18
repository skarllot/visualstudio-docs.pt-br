---
title: "Instru&#231;&#245;es passo a passo: criando um instalador personalizado para um aplicativo ClickOnce | Microsoft Docs"
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
  - "implantação ClickOnce, instalador personalizado"
  - "instalador personalizado [ClickOnce]"
  - "implantando aplicativos [ClickOnce], instalador personalizado"
  - "InPlaceHostingManager [ClickOnce], instalador personalizado"
  - "instalador [ClickOnce], personalizado"
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
caps.latest.revision: 34
caps.handback.revision: 34
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: criando um instalador personalizado para um aplicativo ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Qualquer aplicativo de ClickOnce com base em um arquivo. exe pode ser instalado silenciosamente e atualizado por um instalador personalizado.  Um instalador personalizado pode implementar a experiência do usuário personalizada durante a instalação, incluindo caixas de diálogo personalizadas para operações de segurança e manutenção.  Para executar operações de instalação, o instalador personalizado usa a <xref:System.Deployment.Application.InPlaceHostingManager> classe.  Esta explicação passo a passo demonstra como criar um instalador personalizado que instala silenciosamente um aplicativo ClickOnce.  
  
## Pré-requisitos  
  
### Para criar um instalador de aplicativo personalizado do ClickOnce  
  
1.  Em seu aplicativo de ClickOnce, adicione referências ao deployment e System.Windows.Forms.  
  
2.  Adicionar uma nova classe ao seu aplicativo e especificar qualquer nome.  Esta explicação passo a passo usa o nome  `MyInstaller`.  
  
3.  Adicione o seguinte `Imports` ou `using` instruções para a parte superior da nova classe.  
  
    ```vb#  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```c#  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  Adicione os seguintes métodos para sua classe.  
  
     Esses métodos chamam <xref:System.Deployment.Application.InPlaceHostingManager> métodos para baixar o manifesto de implantação, declarar permissões apropriadas, pergunte ao usuário permissão para instalar e então faça o download e instalar o aplicativo para o cache de ClickOnce.  Um instalador personalizado pode especificar que um aplicativo de ClickOnce é pre\-trusted, ou pode adiar a decisão de confiança a <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> chamada de método.  Esse código pre\-trusts o aplicativo.  
  
    > [!NOTE]
    >  Permissões atribuídas pelo pre\-trusting não podem exceder as permissões do código do instalador personalizado.  
  
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-cs[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]  
  
5.  Para tentar a instalação do seu código, chamar o `InstallApplication` método.  Por exemplo, se você nomeou sua classe `MyInstaller`, você pode chamar `InstallApplication` da seguinte maneira.  
  
    ```vb#  
    Dim installer As New MyInstaller()  
    installer.InstallApplication("\\myServer\myShare\myApp.application")  
    MessageBox.Show("Installer object created.")  
    ```  
  
    ```c#  
    MyInstaller installer = new MyInstaller();  
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");  
    MessageBox.Show("Installer object created.");  
  
    ```  
  
## Próximas etapas  
 Um aplicativo de ClickOnce também pode adicionar lógica de atualização personalizada, incluindo uma interface de usuário personalizada para mostrar durante o processo de atualização.  Para obter mais informações, consulte <xref:System.Deployment.Application.UpdateCheckInfo>.  Um aplicativo de ClickOnce também pode suprimir a entrada de menu Iniciar padrão, o atalho e a entrada de adicionar ou remover programas, usando um `<customUX>` elemento.  Para obter mais informações, consulte [Elemento \<entryPoint\>](../deployment/entrypoint-element-clickonce-application.md) e <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.  
  
## Consulte também  
 [Manifesto de aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Elemento \<entryPoint\>](../deployment/entrypoint-element-clickonce-application.md)