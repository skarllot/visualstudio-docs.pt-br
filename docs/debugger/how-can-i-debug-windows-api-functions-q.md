---
title: "Como depurar fun&#231;&#245;es de API do Windows? | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.api"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "APIs, depuração"
  - "depurando [C++], Funções de API do Windows"
  - "símbolos do NT e depurando funções de API do Windows"
  - "Funções de API do Windows, depuração"
  - "API do Windows, depurando funções de API"
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como depurar fun&#231;&#245;es de API do Windows?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se você desejar depurar uma função de API do Windows que tenha os símbolos do NT carregados, deverá fazer o seguinte.  
  
### Para definir um ponto de interrupção em uma função de API do Windows com os símbolos do NT carregados  
  
-   Digite o nome da função junto com o nome da DLL em que a função reside.  No código de 32 bits, use a forma decorada do nome da função.  Para definir um ponto de interrupção no **MessageBeep**, por exemplo, você deverá inserir o seguinte.  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     Para obter o nome decorado, consulte [Viewing Decorated Names](http://msdn.microsoft.com/pt-br/f79e2717-a4db-4d12-a689-69830cce2be0).  
  
## Consulte também  
 [Perguntas frequentes de depuração do código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)