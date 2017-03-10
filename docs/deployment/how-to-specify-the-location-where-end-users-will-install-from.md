---
title: "Como especificar o local de onde os usu&#225;rios finais instalar&#227;o | Microsoft Docs"
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
  - "implantando aplicativos [ClickOnce], especificando uma URL de instalação"
  - "propriedade Instalação do URL"
  - "instalação, especificando uma URL de instalação"
  - "URLs, especificando uma URL de instalação"
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como especificar o local de onde os usu&#225;rios finais instalar&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ao publicar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo, o local em que os usuários acessam para baixar e instalar o aplicativo não é necessariamente o local onde você publica inicialmente o aplicativo.  Por exemplo, em algumas organizações, um desenvolvedor pode publicar um aplicativo para um servidor intermediário e, em seguida, um administrador moveria o aplicativo em um servidor Web.  
  
 Nesse caso, você pode usar o `Installation URL` propriedade para especificar o servidor Web onde os usuários irão fazer download do aplicativo.  Isso é necessário para que o manifesto do aplicativo saiba onde procurar por atualizações.  
  
 O `Installation URL` propriedade pode ser definida na  **Publicar** página da  **Project Designer**.  
  
 **Nota** a `Installation URL` propriedade também pode ser definida usando o  **PublicarAssistente**.  Para obter mais informações, consulte [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md).  
  
### Para especificar um URL de instalação  
  
1.  Com um projeto selecionado no **Solution Explorer**, no menu **Project**, clique em **Properties**.  
  
2.  Clique na guia **Publish**.  
  
3.  No campo URL de instalação, digite o local de instalação usando uma URL totalmente qualificada usando o formato http:\/\/www.microsoft.com\/ApplicationName ou um caminho UNC usando o formato \\\\Server\\ApplicationName.  
  
## Consulte também  
 [Como especificar onde o Visual Studio copiará os arquivos](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)