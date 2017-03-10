---
title: "Use a op&#231;&#227;o de linha de comando &#39;&lt; op&#231;&#227;o &gt;&#39; ou configura&#231;&#245;es de projeto apropriadas em vez de &#39;&lt; parameter &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc41008"
  - "vbc41008"
helpviewer_keywords: 
  - "BC41008"
ms.assetid: 1c5d6d7a-b767-4dae-aa61-d7fa81d5aad1
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Use a op&#231;&#227;o de linha de comando &#39;&lt; op&#231;&#227;o &gt;&#39; ou configura&#231;&#245;es de projeto apropriadas em vez de &#39;&lt; parameter &gt;&#39;
A melhor maneira de especificar um arquivo que contém uma chave pública para um assembly, um contêiner de chave pública para um assembly, ou um assembly parcialmente assinado é usar o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Opções do compilador. Não recomendamos o uso do <xref:System.Reflection.AssemblyKeyFileAttribute>, <xref:System.Reflection.AssemblyKeyNameAttribute>, ou <xref:System.Reflection.AssemblyDelaySignAttribute> atributos em seu código.  
  
 **ID do erro:** BC41008  
  
### Para corrigir este erro  
  
1.  Use o [\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile), [\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer), ou [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Opções de compilador em vez do <xref:System.Reflection.AssemblyKeyFileAttribute>, <xref:System.Reflection.AssemblyKeyNameAttribute>, ou <xref:System.Reflection.AssemblyDelaySignAttribute> atributos em seu código.  
  
## Consulte também  
 [Como criar assemblies amigáveis assinados](../Topic/How%20to:%20Create%20Signed%20Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [Compilador de linha de comando do Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile)   
 [\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer)   
 [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign)