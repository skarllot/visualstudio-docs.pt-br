---
title: "Erro MSB8031 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSB8031"
ms.assetid: ebfaca51-fd91-4b04-8194-b4fdededd5fe
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB8031 (MSBuild)
MSB8031  
  
 Para usar codificação em projetos MFC de MBCS, você deve baixar e instalar uma biblioteca adicional.  
  
 Versões MBCS das DLLs MFC não estão incluídas no Visual Studio, mas eles estão disponíveis no suplemento MFC MBCS DLL, que pode ser baixado se você for um cliente do Visual Studio. Se você não instalar o suplemento e tente criar um projeto que usa o conjunto de caracteres MBCS, o vinculador não localizará as DLLs e a compilação falhará.  
  
### Para corrigir este erro  
  
1.  [Baixar o complemento de DLL do MFC MBCS](http://go.microsoft.com/fwlink/?LinkId=299009) do MSDN Centro de Download ou se for prático fazer isso, converter o projeto para o conjunto de caracteres UNICODE.  
  
## Consulte também  
 [Suplemento MFC MBCS DLL](/visual-cpp/mfc/mfc-mbcs-dll-add-on)