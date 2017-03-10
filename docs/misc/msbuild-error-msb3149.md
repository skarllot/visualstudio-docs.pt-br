---
title: "Erro MSB3149 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.NoResources"
helpviewer_keywords: 
  - "MSB3149"
ms.assetid: 63857405-d420-457d-9ba7-80e1a2a9dcb7
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3149 (MSBuild)
**MSB3149: Não há recursos disponíveis para compilar bootstrapper.**  
  
 Esse erro ocorre quando nenhum arquivo de recurso do inicializador \(Setup\) não pôde ser encontrado que corresponde a qualquer cultura.  
  
### Para corrigir este erro  
  
-   Vá para **Painel de controle**, selecione **Adicionar ou remover programas**, reparar o Visual Studio SDK e copie os arquivos para o diretório apropriado \(\< caminho de instalação do SDK \> \\bootstrapper\\engine\\ \< culture \> \\setup.xml\).  
  
## Consulte também  
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)