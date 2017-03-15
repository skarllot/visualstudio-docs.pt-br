---
title: "Elemento &lt;description&gt; (implanta&#231;&#227;o do ClickOnce) | Microsoft Docs"
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
  - "urn:schemas-microsoft-com:asm.v2#description"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Elemento <description> (manifesto da implantação do ClickOnce)"
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;description&gt; (implanta&#231;&#227;o do ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica as informações do aplicativo usadas para criar uma presença de shell e um  **Adicionar ou remover programas** item no painel de controle.  
  
## Sintaxe  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## Elementos e atributos  
 O `description` elemento é obrigatório e está sendo o `urn:schemas-microsoft-com:asm.v1` espaço para nome.  Ele contém nenhum elemento filho e tem os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`publisher`|Obrigatório.  Identifica o nome da empresa, usado para o posicionamento do ícone do Windows  **Iniciar** menu e o  **Adicionar ou remover programas** item no painel de controle, quando a implantação é configurada para instalação.|  
|`product`|Obrigatório.  Identifica o nome do produto completo.  Usado como o título para o ícone instalado no Windows  **Iniciar** menu.|  
|`suiteName`|Opcional.  Identifica uma subpasta dentro do `publisher` a pasta no Windows  **Iniciar** menu.|  
|`supportUrl`|Opcional.  Especifica uma URL de suporte que é mostrada na  **Adicionar ou remover programas** item no painel de controle.  Um atalho para esta URL também é criado para o suporte a aplicativos do Windows  **Iniciar** menu, quando a implantação é configurada para instalação.|  
  
## Comentários  
 O elemento de descrição é necessário em todas as configurações de implantação.  
  
## Exemplo  
 O exemplo de código a seguir ilustra uma `description` elemento em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto de implantação.  Este exemplo de código é parte de um exemplo maior fornecido para o  [O manifesto de implantação de ClickOnce](../deployment/clickonce-deployment-manifest.md) tópico.  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## Consulte também  
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)