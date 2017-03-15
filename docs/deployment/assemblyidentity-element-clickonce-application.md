---
title: "Elemento &lt;assemblyIdentity&gt;(aplicativo ClickOnce) | Microsoft Docs"
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
  - "Elemento <assemblyIdentity> (manifesto do aplicativo ClickOnce)"
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;assemblyIdentity&gt;(aplicativo ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica o aplicativo implantado em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação.  
  
## Sintaxe  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## Elementos e atributos  
 O `assemblyIdentity` elemento é obrigatório.  Ele contém nenhum elemento filho e tem os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Name`|Obrigatório.  Identifica o nome do aplicativo.<br /><br /> Se `Name` contém caracteres especiais, como aspas simples ou duplas, o aplicativo pode falhar ativar.|  
|`Version`|Obrigatório.  Especifica o número de versão do aplicativo no seguinte formato:  `major.minor.build.revision`|  
|`publicKeyToken`|Opcional.  Especifica uma seqüência hexadecimal de 16 caracteres que representa os últimos 8 bytes da `SHA-1` o valor da chave pública na qual o aplicativo ou assembly é assinado de hash.  A chave pública que é usada para assinar o catálogo deve ser 2048 bits ou superior.<br /><br /> Embora a assinar um assembly é recomendada mas opcional, esse atributo é necessário.  Se um assembly for assinado, você deve copiar um valor de um assembly auto\-assinado ou use um valor "fictício" de todos os zeros.|  
|`processorArchitecture`|Obrigatório.  Especifica o processador.  Os valores válidos são `msil` para os processadores, `x86` para Windows de 32 bits, `IA64` para Windows de 64 bits, e `Itanium` para os processadores de 64 bits Intel Itanium.|  
|`language`|Obrigatório.  Identifica os códigos de idioma de duas partes \(por exemplo,  `En-US`\) do assembly.  Esse elemento se encontra o `asmv2` espaço para nome.  Se não for especificado, o padrão é  `neutra`.|  
  
## Exemplos  
  
### Descrição  
 O exemplo de código a seguir ilustra um `assemblyIdentity` elemento em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto de aplicativo.  Este exemplo de código é parte de um exemplo maior fornecido no  [O manifesto de aplicativo de ClickOnce](../deployment/clickonce-application-manifest.md).  
  
### Código  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## Consulte também  
 [Manifesto de aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Elemento \<assemblyIdentity\>](../deployment/assemblyidentity-element-clickonce-deployment.md)