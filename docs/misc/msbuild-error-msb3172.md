---
title: "Erro MSB3172 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.ReadInputManifestFailed"
helpviewer_keywords: 
  - "MSB3172"
ms.assetid: aa7291db-1f36-41e7-a510-90cd4daaa89d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3172 (MSBuild)
**MSB3172: Não é possível ler o manifesto '\< arquivo \>'. '\< erro \>'**  
  
 Esse erro é gerado quando o processo de compilação encontra um problema geral ao ler um arquivo de manifesto. A mensagem de erro contém o nome do arquivo seguido por informações mais detalhadas sobre o que deu errado.  
  
 Você pode ter adicionado um assembly ou um arquivo de manifesto como um arquivo de conteúdo. Você deve usar o **Adicionar referência** comando em vez de **Adicionar arquivo** para que o assembly dependente corretamente é referenciado pelo sistema do projeto. Projetos mais sofisticados normalmente marcar o. manifest na pasta bin como um arquivo de projeto, mas você deve evitar fazer isso. Torna\-se o arquivo App oculta a. manifest de arquivos e pode ser editado manualmente para cenários avançados.  
  
## Consulte também  
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)