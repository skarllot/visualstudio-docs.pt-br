---
title: "Erro MSB3180 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.DuplicateComDefinition"
helpviewer_keywords: 
  - "MSB3180"
ms.assetid: 98d8cb76-6176-4121-82ee-8a297d9deebc
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3180 (MSBuild)
**Msb3180 \(\): O componente COM '\< assembly \>' é definido em ambos os '\< arquivo \>' e '\< arquivo \>', clsid\/tlbid \= "' \< assembly \>'".**  
  
 Esse erro é gerado pela geração de manifesto aplicativo processo quando referências COM duplicados \(para bibliotecas de classes ou tipo\) são encontradas no arquivo faz referência ou no dependente manifestos.  
  
 Por exemplo, você poderá receber esse erro se você adicionou uma referência a um objeto COM um manifesto externo e uma referência ao mesmo objeto COM um manifesto interno.  
  
### Para corrigir este erro  
  
-   Remova uma das referências duplicadas COM.  
  
## Consulte também  
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)