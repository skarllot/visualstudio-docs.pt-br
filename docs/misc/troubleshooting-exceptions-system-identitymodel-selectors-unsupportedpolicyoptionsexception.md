---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.IdentityModel.Selectors.UnsupportedPolicyOptionsException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Exceção System.IdentityModel.Selectors.UnsupportedPolicyOptionsException"
  - "Exceção UnsupportedPolicyOptionsException"
ms.assetid: 1151127d-81a1-4d87-8462-924ab9d1ee01
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.IdentityModel.Selectors.UnsupportedPolicyOptionsException
Um <xref:System.IdentityModel.Selectors.UnsupportedPolicyOptionsException> exceção indica que uma política foi fornecida para o sistema que inclui opções que não são suportadas. Restrições que podem causar essas falhas incluem o seguinte:  
  
 Um destinatário solicitou um token do serviço de token de segurança local especificando http:\/\/schemas.xmlsoap.org\/ws\/2005\/05\/identity\/issuer\/self como o emissor do token. No entanto, um dos requisitos especificados na política não há suporte, o serviço de token de segurança local do CardSpace. Para obter mais informações, consulte [uma referência técnica para o perfil de cartão de informações v 1.0](http://go.microsoft.com/fwlink/?LinkId=102401). Exemplos de opções sem suporte incluem o seguinte:  
  
-   Uma declaração solicitada pelo destinatário não está na lista de declarações com suporte especificadas no [suporte para tipos de declaração](http://go.microsoft.com/fwlink/?LinkId=102402) seção de "Uma referência técnica para o perfil do cartão de informações v 1.0".  
  
-   O tipo de token é algo diferente de SAML 1.0 ou 1.1.  
  
-   Para sites não SSL, uma chave não é simétrica.  
  
-   O KeyWrapAlgorithm é diferente do algoritmo padrão.  
  
-   Um elemento sem suporte é especificado na política. Os elementos que têm suporte são os seguintes:  
  
    -   EncryptionAlgorithm  
  
    -   CanonicalizationAlgorithm  
  
    -   SignWith  
  
    -   TokenType  
  
    -   ClaimsElement  
  
    -   KeyType  
  
    -   Tamanho da chave  
  
    -   EncryptWith  
  
    -   RequestType  
  
    -   SecondaryParameters  
  
    -   KeyWrapAlgorithm  
  
-   WST: RequestType não é do tipo de problema.  
  
-   Para tipos de chave assimétricos, um tamanho de chave não é 2048.  
  
## Consulte também  
 <xref:System.IdentityModel.Selectors.UnsupportedPolicyOptionsException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)