---
title: "Vis&#227;o geral de biblioteca do Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Biblioteca do Visual Studio, visão geral"
ms.assetid: 48910975-7202-462f-a656-de67a4f8b14d
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Vis&#227;o geral de biblioteca do Visual Studio
Biblioteca de Visual Studio é um conjunto de classes de C\+\+ baseado em modelo para simplificar a criação de VSPackages em C\+\+ nativo.  Biblioteca de Visual Studio inclui o código\-fonte completo, como um conjunto de arquivos de cabeçalho do C\+\+.  Os arquivos de cabeçalho estão instalados em  *caminho de instalação do SDK do Visual Studio*\\VisualStudioIntegration \\Common\\Source\\CPP\\VSL\\Include\\.  
  
> [!NOTE]
>  Biblioteca de Visual Studio baseia\-se sobre a biblioteca de ATL \(Active Template\) para o suporte a objetos COM.  Para obter mais informações, consulte [Introdução a ATL](/visual-cpp/atl/introduction-to-atl).  
  
 Biblioteca de Visual Studio oferece suporte a testes de unidade, para seu próprio código e para o seu código.  Alguns testes de unidade são incluídos, da seguinte maneira:  
  
-   Visual Studio testes de unidade de biblioteca estão instalados em  *caminho de instalação do SDK do Visual Studio*\\VisualStudioIntegration\\Common\\Source\\CPP\\VSL\\UnitTest\\.  
  
-   As classes base para testes de unidade para o seu código estão em  *caminho de instalação do SDK do Visual Studio*\\VisualStudioIntegration\\Common\\Source\\CPP\\VSL\\Include\\VSLUnitTest.h.  
  
 Implementações falsas de interfaces COM e Visual Studio mais usados estão nos arquivos de cabeçalho, VSLMockSystemInterfaces.h e VSLMockVisualStudioInterfaces.h, que estão instalados nas  *caminho de instalação do SDK do Visual Studio*\\VisualStudioIntegration\\Common\\Source\\CPP\\VSL\\Include\\.  
  
## Consulte também  
 [Desenvolvendo os VSPackages usando a biblioteca do Visual Studio](../misc/developing-vspackages-by-using-the-visual-studio-library.md)