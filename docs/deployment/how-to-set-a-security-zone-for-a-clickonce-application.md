---
title: "Como definir uma zona de seguran&#231;a para um aplicativo ClickOnce | Microsoft Docs"
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
  - "Implantação do ClickOnce, configurações de segurança"
  - "segurança de acesso do código, os aplicativos ClickOnce"
  - "zonas de segurança, os aplicativos ClickOnce"
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como definir uma zona de seguran&#231;a para um aplicativo ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ao definir permissões de segurança para um aplicativo ClickOnce de acesso ao código, você precisa para começar com um conjunto básico de permissões no **segurança** página do **Project Designer**.  
  
 Na maioria dos casos, você também pode escolher a **Internet** zona que contém um conjunto limitado de permissões, ou o **Intranet Local** zona que contém um conjunto maior de permissões. Se seu aplicativo exigir permissões personalizadas, você pode fazer isso escolhendo a **personalizado** zona de segurança. Para obter mais informações sobre como configurar permissões personalizadas, consulte [Como definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
### Para definir uma zona de segurança  
  
1.  Com um projeto selecionado no **Solution Explorer**, diante o **projeto** menu clique **propriedades**.  
  
2.  Clique o **segurança** guia.  
  
3.  Selecione o **Ativar configurações de segurança do ClickOnce** caixa de seleção.  
  
4.  Selecione o **é um aplicativo de confiança parcial** botão de opção.  
  
     Controles de **permissões de segurança do ClickOnce** seção estão habilitados.  
  
5.  No **seu aplicativo será instalado a partir de zona** lista suspensa, selecione uma zona de segurança.  
  
## Consulte também  
 [Como definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)