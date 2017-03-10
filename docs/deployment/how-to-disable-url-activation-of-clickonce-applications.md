---
title: "Como desabilitar a ativa&#231;&#227;o de aplicativos ClickOnce pela URL | Microsoft Docs"
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
  - "implantação ClickOnce, ativação de URL"
  - "disallowUrlActivation"
  - "ativação de URL, Aplicativos ClickOnce"
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como desabilitar a ativa&#231;&#227;o de aplicativos ClickOnce pela URL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Normalmente, um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo será iniciado automaticamente imediatamente após a instalação de um servidor Web.  Por motivos de segurança, você pode optar por desabilitar esse comportamento e informar aos usuários para iniciar o aplicativo a partir de **Iniciar** menu em vez disso.  O procedimento a seguir descreve como desabilitar a ativação de URL.  
  
 Essa técnica pode ser usada apenas para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos instalados no computador do usuário de um servidor Web.  Ele não pode ser usado para aplicativos somente online, que podem ser iniciados apenas por meio de sua URL.  Para obter mais informações sobre a diferença entre os aplicativos instalados e somente online, consulte [Escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Este procedimento usa o [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] ferramenta MageUI.exe.  Para obter mais informações sobre essa ferramenta, consulte [MageUI.exe \(Ferramenta de Geração e Edição de Manifesto, cliente gráfico\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md).  Você também pode executar esse procedimento usando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Procedimento  
  
#### Para desabilitar a ativação de URL para seu aplicativo  
  
1.  Abra o manifesto de implantação no MageUI.exe.  Se você ainda não tiver criado um, siga as etapas no [Instruções passo a passo: implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Selecione o **Opções de implantação** guia.  
  
3.  Limpar o **executar automaticamente o aplicativo após a instalação do** caixa de seleção.  
  
4.  Salve e assinar o manifesto.  
  
## Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)