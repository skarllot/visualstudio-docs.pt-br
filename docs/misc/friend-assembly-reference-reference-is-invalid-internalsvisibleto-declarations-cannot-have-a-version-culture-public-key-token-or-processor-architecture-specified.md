---
title: "Refer&#234;ncia de assembly Friend &lt; reference &gt; &#233; inv&#225;lida. Declara&#231;&#245;es InternalsVisibleTo n&#227;o podem ter uma vers&#227;o, cultura, token de chave p&#250;blica ou arquitetura de processador especificada. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31534"
  - "vbc31534"
helpviewer_keywords: 
  - "BC31534"
ms.assetid: ae1e470e-3105-48f2-87b1-466e395a7d44
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Refer&#234;ncia de assembly Friend &lt; reference &gt; &#233; inv&#225;lida. Declara&#231;&#245;es InternalsVisibleTo n&#227;o podem ter uma vers&#227;o, cultura, token de chave p&#250;blica ou arquitetura de processador especificada.
O nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Construtor de atributo contém um `Version`, `Culture`, `PublicKeyToken`, ou `processorArchitecture` atributo.  
  
 **ID do erro:** BC31534  
  
### Para corrigir este erro  
  
1.  Remover o `Version`, `Culture`, `PublicKeyToken`, ou `processorArchitecture` atributo do nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Construtor de atributo.  
  
## Consulte também  
 <xref:System.Reflection.AssemblyName>   
 [NÃO está em compilação: Friend Assemblies \(Visual Basic\)](http://msdn.microsoft.com/pt-br/80e7a33a-ca91-450b-a00e-c5a7986e228c)