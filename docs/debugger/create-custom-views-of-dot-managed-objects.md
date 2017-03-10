---
title: "Exibindo tipos de dados personalizados | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.data.elements"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Arquivo autoexp.dat"
  - "tipos de dados personalizados"
  - "tipos de dados [C#], personalizado"
  - "depurador, expandindo tipos de dados"
  - "código gerenciado, tipos de dados personalizados"
  - "Arquivo mcee_cs.dat"
  - "Arquivo mcee_mc.dat"
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exibindo tipos de dados personalizados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode personalizar o modo como o Visual Studio exibe tipos de dados nas janelas variáveis do depurador.  
  
## Atributos  
 No C\# e no Visual Basic, você pode adicionar expansões para dados personalizados usando <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> e <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
 No código do [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], o Visual Basic não dá suporte ao atributo DebuggerBrowsable.  Essa restrição é removida em versões mais recentes do .NET Framework.  
  
## Visualizadores  
 Você pode escrever um visualizador para exibir qualquer tipo de dados gerenciados.  Para obter mais informações, consulte [Como escrever um visualizador](../debugger/how-to-write-a-visualizer.md).  
  
## Código nativo  
 Para o código nativo, você pode adicionar expansões de tipo de dados personalizados ao arquivo autoexp.dat, que está localizado no diretório Arquivos de Programas\\Microsoft Visual Studio 11.0\\Common7\\Packages\\Debugger.  As instruções sobre como escrever regras de `autoexp` estão localizadas no próprio arquivo.  
  
> [!CAUTION]
>  A estrutura desse arquivo e a sintaxe de regras de autoexp podem ser alteradas de uma versão do Visual Studio para a seguinte.  
  
 As exibições de tipo nativo também podem ser personalizadas para gravar um suplemento do avaliador de expressão.  Para obter mais informações, consulte [EEAddIn Sample: Debugging Expression Evaluator Add\-In](http://msdn.microsoft.com/pt-br/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## Consulte também  
 [Usando o atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Inspeção e Windows QuickWatch](../debugger/watch-and-quickwatch-windows.md)   
 [Melhorando a depuração com os atributos de exibição do depurador](../Topic/Enhancing%20Debugging%20with%20the%20Debugger%20Display%20Attributes.md)