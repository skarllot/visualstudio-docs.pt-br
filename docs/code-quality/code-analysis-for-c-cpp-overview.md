---
title: "An&#225;lise de c&#243;digo para vis&#227;o geral do C/C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Diretivas (#pragma), análise de código"
  - "anotações, análise de código"
  - "integração de compilação, análise de código"
  - "C, análise de código"
  - "análise de código C/C++"
  - "C++, análise de código"
  - "políticas de check-in, análise de código"
  - "ferramenta de análise de código"
  - "análise de código, C/C++"
  - "linha de comando, análise de código"
  - "IDE, análise de código"
  - "diretiva pragma, análise de código"
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
caps.latest.revision: 25
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# An&#225;lise de c&#243;digo para vis&#227;o geral do C/C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A ferramenta de análise de código C\/C\+\+ fornece aos desenvolvedores informações sobre defeitos possíveis em seu código\-fonte C\/C\+\+.  Os erros de codificação comuns relatados pela ferramenta incluem excesso de buffer, memória não inicializada, o ponteiro nulo cancelará, e vazamentos de memória e de recurso.  
  
## Integração de IDE \(ambiente de desenvolvimento integrado\)  
 Para fazer isso natural para que os desenvolvedores usam a ferramenta de análise, é totalmente integrado de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE.  Durante o processo de compilação, todos os avisos gerados para o código\-fonte são exibidas na Lista de erros.  Você pode navegar no código\-fonte que causou o aviso, e você pode exibir informações adicionais sobre a causa e as possíveis soluções do problema.  
  
## Suporte de \#pragma  
 Os desenvolvedores podem usar a diretiva de `#pragma` para tratar avisos como erros; habilitar ou desabilitar, avisos e suprima avisos para linhas de código individuais.  Para obter mais informações, consulte [How to: Enable and Disable Code Analysis for Specific C\/C\+\+ Warnings](http://msdn.microsoft.com/pt-br/910b8518-71f1-4b2e-b012-70647795642a).  
  
## Suporte de anotação  
 As anotações melhorar a precisão da análise de código.  As anotações fornecem informações adicionais sobre condições de pré e POST em parâmetros e em tipos de retorno de função.  Para obter mais informações, consulte [Como especificar informações de código adicionais usando \_\_analysis\_assume](../Topic/How%20to:%20Specify%20Additional%20Code%20Information%20by%20Using%20__analysis_assume.md)  
  
## Ferramenta de análise de execução como parte da política de check\-in  
 Talvez você queira exigir que todos os registros do código\-fonte satisfazem determinadas políticas.  Em particular, você deseja garantir que a análise esteve executada como uma etapa de compilação local a mais recente.  Para obter mais informações sobre como habilitar uma política de check\-in de análise de código, consulte [Criando e usando políticas de check\-in de análise do código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## Integração da compilação da equipe  
 Você pode usar os recursos integrados do sistema de compilação para executar a ferramenta de análise de código como uma etapa do processo de criação de [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)].  Para obter mais informações, consulte [Compilar o aplicativo](../Topic/Build%20the%20application.md).  
  
## Suporte de linha de comando  
 A integração de adição ao valor máximo no ambiente de desenvolvimento, os desenvolvedores também podem usar a ferramenta de análise de linha de comando, conforme mostrado no seguinte exemplo:  
  
 `C:\>cl /analyze Sample.cpp`