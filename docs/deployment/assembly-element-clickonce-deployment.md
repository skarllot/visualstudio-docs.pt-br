---
title: "Elemento &lt;assembly&gt; (implanta&#231;&#227;o do ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#assembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Elemento <assembly> (manifesto da implantação do ClickOnce)"
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;assembly&gt; (implanta&#231;&#227;o do ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O elemento de nível superior para obter o manifesto de implantação.  
  
## Sintaxe  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## Elementos e atributos  
 O `assembly` elemento é o elemento raiz e é necessário.  O primeiro elemento contido deve ser um `assemblyIdentity` elemento.  Os elementos de manifesto devem estar nos seguintes namespaces:  `urn: schemas-microsoft-v1`,  `urn: schemas-microsoft-com:asm.v2`, e  `http://www.w3.org/2000/09/xmldsig#`.  Elementos filho do assembly também devem estar nesses namespaces, por herança ou marcação.  
  
 O `assembly` elemento tem o atributo a seguir.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`manifestVersion`|Obrigatório.  Este atributo deve ser definido como  `1.0`.|  
  
## Exemplo  
 O exemplo de código a seguir ilustra um `assembly` elemento em um manifesto de implantação para um aplicativo implantado usando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Este exemplo de código é parte de um exemplo maior fornecido para o  [O manifesto de implantação de ClickOnce](../deployment/clickonce-deployment-manifest.md) tópico.  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
```  
  
## Consulte também  
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Elemento \<assembly\>](../deployment/assembly-element-clickonce-application.md)