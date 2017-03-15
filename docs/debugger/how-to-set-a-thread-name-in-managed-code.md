---
title: "Como definir um nome de thread no c&#243;digo gerenciado | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurando [Visual Studio], threads"
  - "nomes de thread"
  - "Propriedade Thread.Name"
  - "threading [Visual Studio], nomes"
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como definir um nome de thread no c&#243;digo gerenciado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A nomeação de thread é possível em qualquer edição do Visual Studio.  A nomeação de thread é útil para manter o controle de threads na janela **Threads**.  Como a janela **Threads** não está disponível nas edições do Visual Studio Express, a nomeação de thread tem pouca utilidade nas edições Express.  
  
 Para definir um nome do thread no código gerenciado, use a propriedade <xref:System.Threading.Thread.Name%2A>.  
  
## Exemplo  
  
```  
Public Class Needle  
    ' This method will be called when the thread is started.  
    Sub Baz()  
        Console.WriteLine("Needle Baz is running on another thread")  
    End Sub  
End Class  
  
Sub Main()  
    Console.WriteLine("Thread Simple Sample")  
    Dim oNeedle As New Needle()  
   ' Create a Thread object.   
    Dim oThread As New System.Threading.Thread(AddressOf oNeedle.Baz)  
    ' Set the Thread name to "MainThread".  
    oThread.Name = "MainThread"  
    ' Starting the thread invokes the ThreadStart delegate  
    oThread.Start()  
End Sub  
```  
  
## Consulte também  
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Como definir um nome de thread em código nativo](../debugger/how-to-set-a-thread-name-in-native-code.md)