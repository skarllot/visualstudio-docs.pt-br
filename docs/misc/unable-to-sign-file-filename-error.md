---
title: "N&#227;o &#233; poss&#237;vel assinar o arquivo &#39;&lt; nomedoarquivo &gt;&#39;: &lt; erro &gt; | Microsoft Docs"
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
  - "bc31028"
  - "vbc31028"
helpviewer_keywords: 
  - "BC31028"
ms.assetid: 2cb22e75-5ee2-4e07-afc0-680a0bd543d4
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o &#233; poss&#237;vel assinar o arquivo &#39;&lt; nomedoarquivo &gt;&#39;: &lt; erro &gt;
Ocorreu um erro ao tentar entrar no arquivo especificado. Esse erro pode ter ocorrido por vários motivos:  
  
-   Permissões insuficientes.  
  
-   Faltando arquivos do sistema necessários para a assinatura Authenticode.  
  
-   Uma referência a um certificado não existente ou arquivo de chave privada.  
  
-   Grafia incorreta de um nome de arquivo ou URL.  
  
 **ID do erro:** BC31028  
  
### Para corrigir este erro  
  
1.  Insira o certificado correto e nomes de arquivo de chave privada.  
  
2.  Se você estiver usando a assinatura Authenticode, verifique se os arquivos Signcode.exe. exe e javasign, estão presentes, e o atributo somente leitura não está definido.  
  
3.  Verifique se você tem `Write` permissão para o arquivo.  
  
## Consulte também  
 [File Signing Tool \(Signcode.exe\)](http://msdn.microsoft.com/pt-br/2d299154-34ea-41ba-ad12-17075bb7e1db)   
 [Deployment and Authenticode Signing](http://msdn.microsoft.com/pt-br/ecc3f059-da2e-445b-9b87-5b2978e2f8b2)