---
title: "Implantando pr&#233;-requisitos para aplicativos de 64 bits | Microsoft Docs"
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
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "64 bits [Visual Studio]"
  - "aplicativos de 64 bits [Visual Studio]"
  - "programação de 64 bits [Visual Studio]"
  - "implantando aplicativos [Visual Studio], 64 bits"
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Implantando pr&#233;-requisitos para aplicativos de 64 bits
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A implantação do ClickOnce oferece suporte à instalação de aplicativos em plataformas de 64 bits.  As plataformas de destino são plataformas **x86** para 32 bits, **x64** para máquinas compatíveis com o conjunto de instruções AMD64 e EM64T e **Itanium** para o processador Itanium de 64 bits.  
  
## Pré\-requisitos  
 A tabela a seguir lista os redistribuíveis que você pode usar como pré\-requisitos para a instalação do seu aplicativo de 64 bits.  
  
 Se você selecionar um pré\-requisito que não tem componentes de 64 bits, poderá ver um aviso informando que os pacotes selecionados não estão disponíveis para a plataforma de 64 bits.  
  
|Redistribuível|Suporte a x64|Suporte a IA64|  
|--------------------|-------------------|--------------------|  
|[!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)]|Sim|Não|  
|Bibliotecas de tempo de execução do Visual C\+\+ 2010 \(IA64\)|Não|Sim|  
|Bibliotecas de tempo de execução do Visual C\+\+ 2010 \(x64\)|Sim|Não|  
|Microsoft .NET Framework 4 \(x86 e x64\)|Sim||  
|Perfil de cliente do Microsoft .NET Framework 4 \(x86 e x64\)|Sim||  
  
## Consulte também  
 [Implantando aplicativos, serviços e componentes](../deployment/deploying-applications-services-and-components.md)   
 [Como instalar pré\-requisitos com um aplicativo ClickOnce](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [Aplicativos de 64 bits](../Topic/64-bit%20Applications.md)