---
title: "Disponibilidade de Funcionalidades em vers&#245;es do Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio, disponibilidade de recursos"
ms.assetid: cb2728da-7705-4dea-a1c3-12a0388cb652
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Disponibilidade de Funcionalidades em vers&#245;es do Visual Studio
A tabela a seguir mostra se determinados recursos têm suporte nas versões listadas do Visual Studio Professional.  
  
-   "Sim" significa que a versão do Visual Studio inclui o recurso.  
  
-   "Adicione" significa que a versão do Visual Studio não inclui o recurso, mas está disponível e você pode obter mais informações, clique no link.  
  
-   "Não" significa que a versão do Visual Studio não inclui o recurso.  
  
||Visual Studio 2010<br /><br /> e<br /><br /> Visual Studio 2010 SP1|[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|[!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]|  
|-|---------------------------------------------------------|-------------------------------------------------------------------|--------------------------------------------------------------|  
|Versões com suporte do .NET Framework|2.0, 3.0, 3.5 SP1, 4|2.0, 3.0, 3.5 SP1, 4, 4.5|2.0, 3.0, 3.5 SP1, 4, 4.5 E 4.5.1|  
|Servidor Web local|Sim|Sim|Sim|  
|SQL Server Express|2008|2008|2008|  
|Conectar\-se às versões do SQL Server por meio do Gerenciador de servidores|2000, 2005, 2008|2000, 2005, 2008|2000, 2005, 2008|  
|ASP.NET AJAX <sup>1</sup>|Sim|Sim|Sim|  
|Controlador de exibição de modelo do ASP.NET|Sim|Sim|Sim|  
|Dados dinâmicos do ASP.NET|Sim|Sim|Sim|  
|MSBuild|Sim|Sim|Sim|  
|ADO.NET Entity Framework|Sim|Sim|Sim|  
|Serviços de dados ADO.NET|Sim|Sim|Sim|  
|Ferramentas do Microsoft Azure|Adicionar|Adicionar||  
|Dispositivos inteligentes|Não|Não||  
|Computação paralela|Yes <sup>2</sup>|Sim|Sim|  
|Windows Communication Foundation|Sim|Sim|Sim|  
|Windows Presentation Foundation|Sim|Sim|Sim|  
|Serviços de aplicativos de Internet ricos do .NET|[Adicionar](http://go.microsoft.com/fwlink/?LinkID=230768)|Sim|Sim|  
|O Silverlight 1|Sim|Sim|Sim|  
|O Silverlight 2|Não|Sim|Sim|  
|Silverlight 3|Sim|Sim|Sim|  
|Silverlight 4|[Adicionar](http://go.microsoft.com/fwlink/?LinkID=153710)|Sim|Sim|  
|Silverlight 5|[Add](http://go.microsoft.com/fwlink/?LinkID=215392), SP1 only.|Sim|Sim|  
|IronPython|[Adicionar](http://go.microsoft.com/fwlink/?LinkID=183863)|[Adicionar](http://go.microsoft.com/fwlink/?LinkID=183863)|[Adicionar](http://go.microsoft.com/fwlink/?LinkID=183863)|  
|IronRuby|[Adicionar](http://go.microsoft.com/fwlink/?LinkID=183864)|[Adicionar](http://go.microsoft.com/fwlink/?LinkID=183864)|[Adicionar](http://go.microsoft.com/fwlink/?LinkID=183864)|  
|Visual Studio Tools para Office|Yes <sup>4</sup><br /><br /> \(Office 2007, Office 2010\)|Sim <sup>4</sup>\(Office 2010\)|Sim <sup>4</sup>\(Office 2013\)|  
|Projetos de relatório|Sim|Sim|Sim|  
|Assistente de relatório|Sim|Sim|Sim|  
|LINQ \(Consulta Integrada à Linguagem\)|Sim|Sim|Sim|  
|Desenvolvimento do SharePoint|Sim, direcionando o SharePoint 2010|Sim, direcionando o SharePoint 2010|Sim, direcionando o SharePoint 2013|  
|Suporte do .NET framework 4 Client Profile|Sim|Não|Não|  
  
1.  ASP.NET AJAX:  
  
     No servidor: Os controles estão incluídos no ASP.NET 3.5 e já estão o **Toolbox** no Visual Studio. Se você estiver usando uma versão anterior do ASP.NET, por exemplo, o ASP.NET 2.0, em seguida, você pode baixar o [ASP.NET AJAX Extensions](http://go.microsoft.com/fwlink/?LinkID=75360).  
  
     Cliente: A biblioteca do cliente ASP.NET AJAX está incluída no ASP.NET 3.5 SP1.  
  
2.  Computação paralela:  
  
     As extensões paralelas contêm a tarefa paralela TPL \(biblioteca\), PLINQ \(Parallel LINQ\) e as estruturas de dados de simultaneidade; Esses componentes estão incluídos no .NET Framework 4. As bibliotecas equivalentes para desenvolvimento em C\+\+ nativo são o tempo de execução de simultaneidade e a biblioteca de agentes, que são incluídos no Visual Studio 2010. Os aprimoramentos do criador de perfil e o depurador também estão incluídos no Visual Studio 2010.  
  
3.  IronPython e IronRuby:  
  
     Em sites do CodePlex para IronPython e IronRuby, várias versões estão disponíveis. Selecione a versão que se aplica ao seu ambiente. O requisito mínimo para ambas as linguagens é o .NET Framework 2.0 SP1.  
  
4.  Visual Studio Tools para compatibilidade do Office \(VSTO\) e funcionalidade do suplemento:  
  
    ||Visual Studio 2010|[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|[!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]|  
    |-|------------------------|-------------------------------------------------------------------|--------------------------------------------------------------|  
    |Nível de documento|Word 2007, o Word 2010, o Excel 2007 e Excel 2010|O Word 2010, o Excel 2010|O Word 2013, Excel 2013|  
    |Nível de aplicativo|Word 2007, o Word 2010, o Excel 2007, Excel 2010, o InfoPath 2007, InfoPath 2010, Outlook 2007, Outlook 2010, PowerPoint 2007, PowerPoint 2010, Visio 2007, Visio 2010, Project 2007, Project 2010|Word 2010, o Excel 2010, o InfoPath 2010, Outlook 2010, PowerPoint 2010, Visio 2010, Project 2010|Word 2013, Excel 2013, InfoPath 2013, Outlook 2013, 2013 do PowerPoint, Visio 2013 e Project 2013|