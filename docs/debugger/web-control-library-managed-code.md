---
title: "Biblioteca de Controles da Web (c&#243;digo gerenciado) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "depurando [Visual Studio], bibliotecas de controles da Web"
  - "depurando DLLs"
ms.assetid: 2413883f-9e88-406d-b874-0ed743b75d40
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Biblioteca de Controles da Web (c&#243;digo gerenciado)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O modelo de projeto da Biblioteca de Controles da Web cria uma DLL.  Como a biblioteca de classe é uma DLL, você não pode executá\-la diretamente.  Você deve criar uma página do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] que insira o controle.  Para obter mais informações, consulte [Web Control Library Template](http://msdn.microsoft.com/pt-br/00666b07-71d2-4ace-a13c-cc130a3ce372).  
  
### Para depurar uma Biblioteca de Controles da Web \(método 1\)  
  
1.  Abra um projeto existente da Biblioteca de Controles da Web ou crie um novo.  
  
2.  Crie uma página do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] que insira o controle.  
  
3.  No site que está hospedando o agente de teste do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], crie um subdiretório chamado `/Code`.  
  
4.  Copie o código\-fonte do controle no subdiretório `/Code`.  
  
5.  Abra o código\-fonte no subdiretório `/Code` e defina pontos de interrupção.  
  
6.  Abra uma janela do navegador com uma URL que aponte para o agente de teste.  Um ponto de interrupção no controle será atingido e você poderá iniciar a depuração.  
  
### Para depurar uma Biblioteca de Controles da Web \(método 2\)  
  
1.  Crie o projeto de aplicativo host e o projeto de controle da Web na mesma solução.  
  
2.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no aplicativo host e escolha **Adicionar Referência**.  
  
3.  Adicione uma referência ao projeto de controle da Web.  
  
## Consulte também  
 [Aplicativos Web ASP.NET](../debugger/debugging-preparation-aspnet-web-applications.md)