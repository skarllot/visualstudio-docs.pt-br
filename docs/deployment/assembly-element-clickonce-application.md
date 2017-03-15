---
title: "Elemento &lt;assembly&gt;(aplicativo ClickOnce) | Microsoft Docs"
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
  - "Elemento <assembly> (manifesto do aplicativo ClickOnce)"
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;assembly&gt;(aplicativo ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O elemento de nível superior para obter o manifesto de aplicativo.  
  
## Sintaxe  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## Elementos e atributos  
 O `assembly` elemento é o elemento raiz e é necessário.  O primeiro elemento contido deve ser um `assemblyIdentity` elemento.  Os elementos de manifesto devem estar em um dos seguintes namespaces:  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 Elementos filho do assembly também devem estar nesses namespaces, por herança ou marcação.  
  
 O `assembly` elemento tem o atributo a seguir.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`manifestVersion`|Obrigatório.  O `manifestVersion` atributo deve ser definido como  `1.0`.|  
  
## Exemplo  
 O exemplo de código a seguir ilustra um `assembly` elemento em um manifesto de aplicativo para um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  Este exemplo de código é parte de um exemplo maior fornecido no  [O manifesto de aplicativo de ClickOnce](../deployment/clickonce-application-manifest.md).  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"   
  manifestVersion="1.0"   
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
```  
  
## Consulte também  
 [Manifesto de aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Elemento \<assembly\>](../deployment/assembly-element-clickonce-deployment.md)