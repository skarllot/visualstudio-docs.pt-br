---
title: "Elemento &lt;Signature&gt; (implanta&#231;&#227;o do ClickOnce) | Microsoft Docs"
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
  - "Elemento <Signature> (manifesto da implantação do ClickOnce)"
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;Signature&gt; (implanta&#231;&#227;o do ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contém as informações necessárias para assinar digitalmente este manifesto de implantação.  
  
## Sintaxe  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## Comentários  
 Assinar um manifesto de implantação usando uma assinatura do envelope é opcional, mas recomendado.  Para obter mais informações sobre assinatura XML arquivos Consulte a World Wide Web Consortium recomendação, "Assinatura de XML sintaxe e processamento," descrito em [http:\/\/www.w3.org\/TR\/xmldsig\-core\/](http://www.w3.org/TR/xmldsig-core/).  
  
 Se você quiser assinar seu manifesto, hashes devem ser fornecidos para todos os arquivos.  Um manifesto com arquivos que não estão em hash não pode ser assinado porque os usuários não é possível verificar o conteúdo dos arquivos sem hash.  
  
## Exemplo  
 O exemplo de código a seguir ilustra uma `Signature` elemento em um manifesto de implantação usado em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação.  
  
```  
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
  <SignedInfo>  
    <CanonicalizationMethod Algorithm=  
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />  
    <SignatureMethod Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
    <Reference URI="">  
      <Transforms>  
        <Transform Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
      </Transforms>  
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <DigestValue>d2z5AE...</DigestValue>  
    </Reference>  
  </SignedInfo>  
  <SignatureValue>  
4PHj6SaopoLp...  
  </SignatureValue>  
  <KeyInfo>  
    <X509Data>  
      <X509Certificate>  
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...  
      </X509Certificate>  
    </X509Data>  
  </KeyInfo>  
</Signature>  
```  
  
## Consulte também  
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)