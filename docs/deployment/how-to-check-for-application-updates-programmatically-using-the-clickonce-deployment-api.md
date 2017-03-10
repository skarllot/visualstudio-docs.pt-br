---
title: "Como verificar se h&#225; atualiza&#231;&#245;es do aplicativo programaticamente usando a API de implanta&#231;&#227;o do ClickOnce | Microsoft Docs"
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
  - "atualizações do aplicativo"
  - "implantação ClickOnce, atualizações"
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como verificar se h&#225; atualiza&#231;&#245;es do aplicativo programaticamente usando a API de implanta&#231;&#227;o do ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce fornece duas maneiras para atualizar um aplicativo quando ele é implantado.  O primeiro método, você pode configurar a implantação de ClickOnce para verificar automaticamente as atualizações em determinados intervalos.  O segundo método, você pode escrever código que usa o <xref:System.Deployment.Application.ApplicationDeployment> classe para verificar se há atualizações com base em um evento, como, por exemplo, uma solicitação do usuário.  
  
 Os procedimentos a seguir mostram alguns códigos para executar uma atualização através de programação e também descrevem como configurar a implantação de ClickOnce para ativar as verificações de atualização através de programação.  
  
 Para atualizar um aplicativo ClickOnce programaticamente, você deve especificar um local para atualizações.  Às vezes, isso é conhecido como um provedor de implantação.  Para obter mais informações sobre a definição dessa propriedade, consulte [Escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
>  Você também pode usar a técnica descrita abaixo para implantar seu aplicativo em um único local mas atualizá\-lo a partir de outro.  Para obter mais informações, consulte [Como especificar um local alternativo para atualizações da implantação](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### Para verificar atualizações programaticamente  
  
1.  Crie um novo aplicativo do Windows Forms usando suas ferramentas de linha de comando ou visual preferenciais.  
  
2.  Criar qualquer botão, o item de menu ou outro item de interface de usuário você deseja que os usuários selecionem para verificar se há atualizações.  A partir do manipulador de eventos do item, chame o método a seguir para verificar e instalar atualizações.  
  
     [!CODE [ClickOnceAPI#6](../CodeSnippet/VS_Snippets_Winforms/ClickOnceAPI#6)]  
  
3.  Compile seu aplicativo.  
  
### Usando o Mage para implantar um aplicativo que verifica se há atualizações programaticamente  
  
-   Siga as instruções para implantar seu aplicativo usando o Mage conforme explicado na [Instruções passo a passo: implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  Ao chamar Mage para gerar o manifesto de implantação, certifique\-se de usar a opção de linha de comando `providerUrl`e para especificar a URL onde ClickOnce deve verificar as atualizações.  Se seu aplicativo irá atualizar a partir de [http:\/\/www.adatum.com\/MyApp](http://www.adatum.com/MyApp), por exemplo, a sua chamada para gerar o manifesto de implantação pode parecer com isso:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### Usando o MageUI.exe para implantar um aplicativo que verifica se há atualizações programaticamente  
  
-   Siga as instruções para implantar seu aplicativo usando o Mage conforme explicado na [Instruções passo a passo: implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  No  **Opções de implantação** guia, defina a  **Local iniciar** campo ao manifesto do aplicativo ClickOnce deve verificar as atualizações.  Sobre o  **Opções de atualização** guia, limpar o  **Este aplicativo deve verificar as atualizações** caixa de seleção.  
  
## Segurança do .NET Framework  
 Seu aplicativo deve ter permissões de confiança total para usar a atualização através de programação.  
  
## Consulte também  
 [Como especificar um local alternativo para atualizações da implantação](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)