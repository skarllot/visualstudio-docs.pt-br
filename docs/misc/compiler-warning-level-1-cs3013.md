---
title: "Compilador CS3013 de aviso (n&#237;vel 1) | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3013"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3013"
ms.assetid: 00b3bbe1-f2a0-465c-be0e-1af700c5753d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS3013 de aviso (n&#237;vel 1)
Módulos adicionados devem ser marcados com o atributo CLSCompliant para corresponder ao assembly  
  
 Um módulo que foi compilado com o [\/target: Module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) opção de compilador foi adicionada para uma compilação com [\/addmodule](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). No entanto, conformidade do módulo com o Common Language Specification \(CLS\) não concorda com o estado CLS da compilação atual.  
  
 Compatibilidade com CLS é indicada com o atributo de módulo. Por exemplo, `[module:CLSCompliant(true)]` indica que o módulo é compatível com, CLS e `[module:CLSCompliant(false)]` indica que o módulo não é compatível com CLS. O padrão é `[module:CLSCompliant(false)]`. Para obter mais informações sobre a CLS, consulte [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).