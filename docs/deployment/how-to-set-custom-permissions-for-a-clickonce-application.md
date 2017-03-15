---
title: "Como definir permiss&#245;es personalizadas para um aplicativo ClickOnce | Microsoft Docs"
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
  - "Aplicativos ClickOnce, permissões"
  - "permissões de aplicativos ClickOnce"
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como definir permiss&#245;es personalizadas para um aplicativo ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode implantar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo que usa as permissões padrão para as zonas da Internet ou Intranet Local. Como alternativa, você pode criar uma zona personalizada para as permissões específicas que o aplicativo precisa. Você pode fazer isso ao personalizar as permissões de segurança no **segurança** página do **Project Designer**.  
  
### Para personalizar uma permissão  
  
1.  Com um projeto selecionado no **Solution Explorer**, diante o **projeto** menu, clique em **propriedades**.  
  
2.  Clique o **segurança** guia.  
  
3.  Selecione o **Ativar configurações de segurança do ClickOnce** caixa de seleção.  
  
4.  Selecione o **é um aplicativo de confiança parcial** botão de opção.  
  
     Controles de **permissões de segurança do ClickOnce** seção estão habilitados.  
  
5.  Do **seu aplicativo será instalado a partir de zona** lista suspensa, clique em **\(personalizada\)**.  
  
6.  Clique em **Editar permissões XML**.  
  
     O arquivo App. é aberto no Editor XML.  
  
7.  Antes do `</applicationRequestMinimum>` elemento, adicione o código XML para as permissões que seu aplicativo requer.  
  
    > [!NOTE]
    >  Você pode usar o `ToXml` método de uma permissão definida para gerar o código XML para o manifesto do aplicativo. Por exemplo, para gerar o XML para o <xref:System.Security.Permissions.EnvironmentPermission> conjunto de permissões, chame o <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> método. Para obter mais informações sobre a estrutura da permissão definida XML, consulte [PONTA: como: importar um conjunto de permissões usando um arquivo XML](http://msdn.microsoft.com/pt-br/dea16b54-c108-408a-ac36-cdc05f746236).  
  
## Consulte também  
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)