---
title: "Elemento &lt;assemblyIdentity&gt; (implanta&#231;&#227;o do ClickOnce) | Microsoft Docs"
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
  - "urn:schemas-microsoft-com:asm.v2#assemblyIdentity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Elemento <assemblyIdentity> (manifesto da implantação do ClickOnce)"
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;assemblyIdentity&gt; (implanta&#231;&#227;o do ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica o assembly principal da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  
  
## Sintaxe  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## Elementos e atributos  
 O `assemblyIdentity` elemento é obrigatório.  Ele contém nenhum elemento filho e tem os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`name`|Obrigatório.  Identifica o nome legível da implantação para fins informativos.<br /><br /> Se `name` contém caracteres especiais, como aspas simples ou duplas, o aplicativo pode falhar ativar.|  
|`version`|Obrigatório.  Especifica o número de versão do assembly, no seguinte formato:  `major.minor.build.revision`.<br /><br /> Esse valor deve ser incrementado em um manifesto atualizado para acionar uma atualização do aplicativo.|  
|`publicKeyToken`|Obrigatório.  Especifica uma seqüência hexadecimal de 16 caracteres que representa os últimos 8 bytes do valor de hash SHA\-1 da chave pública sob as quais o manifesto de implantação é assinado.  A chave pública que é usada para assinar deve ser 2048 bits ou superior.<br /><br /> Embora a assinar um assembly é recomendada mas opcional, esse atributo é necessário.  Se um assembly for assinado, você deve copiar um valor de um assembly auto\-assinado ou use um valor "fictício" de todos os zeros.|  
|`processorArchitecture`|Obrigatório.  Especifica o processador.  Os valores válidos são `msil` para os processadores, `x86` para Windows de 32 bits, `IA64` para Windows de 64 bits, e `Itanium` para os processadores de 64 bits Intel Itanium.|  
|`type`|Obrigatório.  Para compatibilidade com a tecnologia do Windows side\-by\-side installation.  O único valor permitido é  `win32`.|  
  
## Comentários  
  
## Exemplo  
 O exemplo de código a seguir ilustra um `assemblyIdentity` elemento em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto de implantação.  Este exemplo de código é parte de um exemplo maior fornecido para a [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md) tópico.  
  
```  
<!-- Identify the deployment. -->  
<assemblyIdentity   
  name="My Application Deployment.app"  
  version="1.0.0.0"  
  publicKeyToken="43cb1e8e7a352766"  
  language="neutral"  
  processorArchitecture="x86"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## Consulte também  
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Elemento \<assemblyIdentity\>](../deployment/assemblyidentity-element-clickonce-application.md)