---
title: "Elemento &lt;customErrorReporting&gt; (implanta&#231;&#227;o do ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "Elemento <customErrorReporting> (manifesto da implantação do ClickOnce)"
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;customErrorReporting&gt; (implanta&#231;&#227;o do ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica um URI para mostrar quando ocorre um erro.  
  
## Sintaxe  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## Comentários  
 Esse elemento é opcional.  Sem ele, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] exibe uma caixa de diálogo de erro mostrando a pilha de exceção.  Se a `customErrorReporting` elemento está presente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] em vez disso, exibirá o URI indicado pelo `uri` parâmetro.  O URI de destino incluirá a classe de exceção externa, a classe de exceção interna e a mensagem de exceção interna como parâmetros.  
  
 Use esse elemento para adicionar funcionalidade ao seu aplicativo de relatório de erros.  Como o URI gerado inclui informações sobre o tipo de erro, o seu site da Web pode analisar que informações e a exibição, por exemplo, uma tela de solução de problemas apropriada.  
  
## Exemplo  
 O trecho a seguir mostra a `customErrorReporting` elemento, juntamente com o URI gerado, ele pode produzir.  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## Consulte também  
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)