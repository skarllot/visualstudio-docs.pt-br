---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Deployment.Application.InvalidDeploymentException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Classe InvalidDeploymentException"
ms.assetid: 4361e053-8eaf-44e3-b8ac-95516d8d1832
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Deployment.Application.InvalidDeploymentException
Um <xref:System.Deployment.Application.InvalidDeploymentException> exceção é lançada quando o aplicativo ou seus manifestos de aplicativo e implantação não são válidos.  
  
## Dicas associadas  
 **Verifique se que os manifestos deste aplicativo são válidos.**  
 Um manifesto de aplicativo é um arquivo XML que descreve e identifica os assemblies lado a lado compartilhados e privados que um aplicativo deve se vincular em tempo de execução. Eles devem ser as mesmas versões de assembly que foram usadas para testar o aplicativo. Manifestos de aplicativo também podem descrever metadados para arquivos que são particulares ao aplicativo.  
  
 **Use o recurso do ClickOnce para implantar o aplicativo.**  
 Use o ClickOnce para publicar aplicativos em um servidor Web ou rede arquivo compartilhamento para instalação simplificada. Para obter mais informações, consulte [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md).  
  
## Consulte também  
 <xref:System.Deployment.Application.InvalidDeploymentException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Solução de problemas de implantações do ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Implantação do ClickOnce para o Windows Forms](../Topic/ClickOnce%20Deployment%20for%20Windows%20Forms.md)