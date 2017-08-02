---
title: "Como definir configura&#231;&#245;es de depura&#231;&#227;o e vers&#227;o | Microsoft Docs"
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
  - "vs.debug.builds"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "configurações de compilação, depurar"
  - "configurações de compilação, release"
  - "configurações, release"
  - "depurar compilações"
  - "depurar compilações, alterando definições de configuração"
  - "depurar compilações, alternando para compilação de lançamento"
  - "depurar configurações"
  - "depurando [Visual Studio], depurar configurações"
  - "depurando [Visual Studio], configurações de release"
  - "projetos [Visual Studio], depurar configurações"
  - "projetos [Visual Studio], configurações de release"
  - "compilações de lançamento, alterando configurações"
  - "compilações de lançamento, alternando para compilação de depuração"
  - "Projetos Visual Basic, compilações de depuração e lançamento"
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: 45
caps.handback.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como definir configura&#231;&#245;es de depura&#231;&#227;o e vers&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Projetos do Visual Studio tem versão separada e configurações para o seu programa de depuração.  Como os nomes sugerem, você cria a versão de depuração para depuração e a versão de lançamento para a distribuição da versão final.  
  
 A configuração de depuração do seu programa é compilada com informações de depuração simbólica e sem otimização.  A otimização complica a depuração, porque a relação entre o código fonte e as instruções geradas é mais complexa.  
  
 A configuração de versão do seu programa não contém nenhuma informação de depuração simbólica e é totalmente otimizada.  Informações de depuração podem ser geradas em Arquivos PDB, dependendo das opções do compilador que são usadas.  Criar arquivos PDB pode ser muito útil se você posteriormente precisa depurar a versão de lançamento.  
  
 Para obter mais informações sobre configurações de compilação, consulte[Noções sobre configurações de compilação](../ide/understanding-build-configurations.md).  
  
 Você pode alterar a configuração de compilação de**criar**menu, na barra de ferramentas ou nas páginas de propriedades do projeto.  Páginas de propriedades do projeto são específicos do idioma.  O procedimento a seguir mostra como alterar a configuração de compilação no menu e barra de ferramentas.  Para obter mais informações sobre como alterar a configuração de compilação em projetos em diferentes idiomas, consulte a seção de tópicos relacionados abaixo.  
  
### Para alterar a configuração de compilação  
  
1.  No menu Build: clique**criar \/ Configuration Manager**em seguida, selecione**Depurar**ou**versão**.  
  
2.  Na barra de ferramentas, escolha**Depurar**ou**versão**do**configurações da solução**caixa de listagem.  
  
     ![toolbar build configuration](~/debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Essa barra de ferramentas não está disponível nas edições Express.  É possível usar os itens de menu **Solução de Compilação F6** e de **Iniciar Depuração F5** para escolher a configuração.  
  
## Consulte também  
 [Configurações de depuração e preparação](../debugger/debugger-settings-and-preparation.md)   
 [Definições do projeto para uma configuração de depuração do C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Definições do projeto para configurações de depuração do C\#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Definições do projeto para uma configuração de depuração do Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Como criar e editar configurações de teste](../ide/how-to-create-and-edit-configurations.md)   
 [Configurações Debug e Release projeto](http://msdn.microsoft.com/pt-br/0440b300-0614-4511-901a-105b771b236e)