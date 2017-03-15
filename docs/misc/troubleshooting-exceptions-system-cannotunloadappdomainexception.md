---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.CannotUnloadAppDomainException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
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
  - "Classe CannotUnloadAppDomainException"
ms.assetid: eeee07c3-fdbc-4c91-859b-a419d23be9ba
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.CannotUnloadAppDomainException
Um <xref:System.CannotUnloadAppDomainException> exceção é lançada quando há uma tentativa de descarregar um destes procedimentos:  
  
-   O domínio de aplicativo padrão, que deve permanecer carregado em todo o tempo de vida do aplicativo  
  
-   Um domínio de aplicativo com um thread em execução que não é possível interromper a execução imediatamente  
  
-   Um domínio de aplicativo que já foi descarregado  
  
## Dicas associadas  
 **Verifique se você não está tentando descarregar o domínio de aplicativo que é o padrão, tem um thread em execução ou que já foi descarregado.**  
 Qualquer uma dessas condições fará com que essa exceção seja lançada. Para obter mais informações, consulte <xref:System.AppDomain.Unload%2A>.  
  
## Consulte também  
 <xref:System.CannotUnloadAppDomainException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)