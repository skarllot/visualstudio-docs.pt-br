---
title: "O tipo de projeto n&#227;o d&#225; suporte para esta instala&#231;&#227;o | Microsoft Docs"
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
  - "vs.projectflavornotavailable"
ms.assetid: 50e92aff-3ce9-4600-94af-4a16e9dffc90
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# O tipo de projeto n&#227;o d&#225; suporte para esta instala&#231;&#227;o
Este erro ocorre quando você tenta abrir um tipo de projeto que requer um software development kit \(SDK\) que não é instalado com Visual Studio.  Por exemplo, esse erro ocorre se você abre o Visual Studio em um computador que não tenha SDK do Visual Studio instalado e não tente abrir um arquivo de projeto para o SDK, como um projeto de VSIX. \(Para obter mais informações sobre SDK do Visual Studio, consulte [Estendendo o Visual Studio](http://go.microsoft.com/fwlink/?LinkID=64968).\)  
  
## Solução alternativa  
 Você deve verificar que você tenha instalado SDK correto para o tipo de projeto que você está tentando abrir.  
  
#### Para verificar se você já tem SDK instalado  
  
1.  Na barra de menu, escolha **Arquivo**, **Novo**, **Projeto**.  
  
2.  Na caixa de diálogo **Novo Projeto** , expanda o nó de **Instalado** , expanda o nó de **Modelos** , escolha o nó de **Outros tipos de projetos** .  
  
3.  Revise os tipos de projeto disponíveis para determinar se o projeto que você está tentando abrir está disponível.  
  
 Se você não conseguir localizar o tipo de projeto que você está tentando abrir, você não tem SDK associado instalado.  Você deve localizar e instalar SDK associado para abrir o tipo de projeto.  
  
## Consulte também  
 [O que há de novo no Visual Studio 2015](../ide/what-s-new-in-visual-studio-2015.md)   
 [Portando, migrando e atualizando projetos do Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)