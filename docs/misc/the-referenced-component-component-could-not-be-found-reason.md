---
title: "O componente referenciado &#39;componente&#39; n&#227;o foi encontrado. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.referencenotfound"
ms.assetid: 35491b4d-e3e4-4e7c-8ac1-3adb09c1ef58
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# O componente referenciado &#39;componente&#39; n&#227;o foi encontrado. &lt;reason&gt;
O sistema de projeto não pôde resolver uma referência específica.  Duas vezes neste item de lista de tarefas definir foco para Solution Explorer e selecione a referência que não pôde ser resolvida.  
  
 Editar o  [ReferencePaths](http://msdn.microsoft.com/pt-br/8e549b39-7256-456a-8fd7-089b23facf9c) propriedade tal que apropriado diretórios estão incluídos no caminho.  
  
 Este erro pode ocorrer se você mover um projeto para outro computador.  O `ReferencePath` propriedade é armazenada como um caminho absoluto.  Se referência R1 reside no c:\\R\\R1.dll no computador A, o. vbproj.user ou. csproj.user arquivo armazenará c:\\R como parte do `ReferencePath` propriedade.  Se, no entanto, no computador B, R1 residir em d:\\R\\R1.dll, o sistema do projeto não poderá localizar R1 porque d:\\R não está no caminho de referência.  
  
 Um cenário semelhante é o cenário de controle de código fonte.  Se você se inscrever em um projeto, a. vbproj.user \(ou. csproj.user\) arquivo não é copiado para o computador porque não está armazenado no controle de origem.  Portanto, o valor inicial de `ReferencePath` propriedade ficará em branco e quaisquer referências que dependem do `ReferencePath` resolução será resolvida.  Para obter mais informações, consulte "Gerenciando dependências" em  *desenvolvimento em equipe com Visual Studio.NET e Visual SourceSafe*.  
  
 Este erro também pode ser causado se um projeto referenciado não está na solução atual.  
  
 Quando este erro, o projeto pode não ser compilado.  
  
 Para obter mais informações sobre solucionar referências de assembly, consulte [Solucionando Problemas de Referências Quebradas](../ide/troubleshooting-broken-references.md).  
  
## Consulte também  
 [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md)