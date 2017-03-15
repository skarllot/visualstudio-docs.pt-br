---
title: "Elemento &lt;publisherIdentity&gt; (implanta&#231;&#227;o do ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Elemento publisherIdentity [manifesto da implantação ClickOnce], introdução"
  - "Elemento publisherIdentity [manifesto da implantação ClickOnce], sintaxe, elementos, e atributos"
  - "elemento necessário para manifestos assinados [ClickOnce], Elemento publisherIdentity"
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;publisherIdentity&gt; (implanta&#231;&#227;o do ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contém informações sobre o editor que assinou este manifesto de implantação.  
  
## Sintaxe  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## Elementos e atributos  
 O `publisherIdentity` elemento é necessário para manifestos assinados.  A tabela a seguir mostra os atributos que o `publisherIdentity` elemento dá suporte.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`name`|Obrigatório.  Descreve a identidade de quem publicou este aplicativo.|  
|`issuerKeyHash`|Obrigatório.  Contém o hash SHA\-1 da chave pública do emissor do certificado.|  
  
#### Parâmetros  
  
## Valor de Propriedade\/Valor Retornado  
  
## Exceções  
  
## Comentários  
  
## Requisitos  
  
## Subtítulo