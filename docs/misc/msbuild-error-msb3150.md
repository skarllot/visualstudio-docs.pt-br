---
title: "Erro MSB3150 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.NoStringsForCulture"
helpviewer_keywords: 
  - "MSB3150"
ms.assetid: 90d86aef-f4df-4070-8ecc-173eb40668aa
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3150 (MSBuild)
**MSB3150: Não há recursos de cadeia de caracteres disponíveis para compilar bootstrapper com cultura '{0}'.**  
  
 Esse erro ocorre quando o Setup. XML foi encontrado, mas não continha o nó de cadeias de caracteres. O arquivo XML provavelmente foi corrompido.  
  
### Para corrigir este erro  
  
-   Vá para **Painel de controle**, selecione **Adicionar ou remover programas**, reparar o Visual Studio SDK e copie os arquivos para o diretório apropriado \(\< caminho de instalação do SDK \> \\bootstrapper\\engine\\ \< culture \> \\setup.xml\).