---
title: "CA5350: N&#227;o Use algoritmos criptogr&#225;ficos fracos | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA5350: N&#227;o Use algoritmos criptogr&#225;ficos fracos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseWeakCryptographicAlgorithms|  
|CheckId|CA5350|  
|Categoria|Microsoft.Cryptography|  
|Alteração significativa|Não separável|  
  
> [!NOTE]
>  Esse aviso última atualização de novembro de 2015.  
  
## Causa  
 Algoritmos de criptografia, como <xref:System.Security.Cryptography.TripleDES> e algoritmos de hash como <xref:System.Security.Cryptography.SHA1> e <xref:System.Security.Cryptography.RIPEMD160> são considerados fracos.  
  
 Esses algoritmos criptográficos não fornece tanta garantia de segurança como equivalentes mais modernos. Algoritmos de hash criptográfico <xref:System.Security.Cryptography.SHA1> e <xref:System.Security.Cryptography.RIPEMD160> fornecem menos resistência de colisão de algoritmos de hash mais modernos. O algoritmo de criptografia <xref:System.Security.Cryptography.TripleDES> fornece menos bits de segurança que algoritmos de criptografia mais modernos.  
  
## Descrição da regra  
 Algoritmos de criptografia fraca e funções de hash são usadas atualmente por uma série de motivos, mas eles não devem ser usados para garantir a confidencialidade dos dados que eles protegem.  
  
 A regra dispara quando encontra 3DES, SHA1 ou RIPEMD160 algoritmos no código e gera um aviso ao usuário.  
  
## Como corrigir violações  
 Use opções criptograficamente mais fortes:  
  
-   Para criptografia TripleDES, use <xref:System.Security.Cryptography.Aes> criptografia.  
  
-   Para funções de hash SHA1 ou RIPEMD160, use os do [SHA\-2](https://msdn.microsoft.com/en-us/library/windows/desktop/aa382459.aspx) família \(por exemplo, <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>\).  
  
## Quando suprimir avisos  
 Suprima um aviso nessa regra quando o nível de proteção necessário para os dados não requer uma garantia de segurança.  
  
## Exemplo de código pseudo  
 No momento da redação deste artigo, o exemplo de pseudocódigo a seguir ilustra o padrão detectado por essa regra.  
  
### Violação de hash SHA\-1  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA1.Create();  
  
```  
  
### Solução  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA256.Create();  
  
```  
  
### RIPEMD160 Violação de hash  
  
```  
using System.Security.Cryptography; ... var hashAlg = RIPEMD160Managed.Create();  
  
```  
  
### Solução  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA256.Create();  
  
```  
  
### Violação de criptografia TripleDES  
  
```  
using System.Security.Cryptography; ... using (TripleDES encAlg = TripleDES.Create()) { ... }  
```  
  
### Solução  
  
```  
using System.Security.Cryptography; ... using (AesManaged encAlg = new AesManaged()) { ... }  
```