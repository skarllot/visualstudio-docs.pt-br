---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Net.CookieException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Classe CookieException"
ms.assetid: 7db6b962-cc5e-4b63-be65-894a8f186b38
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Net.CookieException
Um <xref:System.Net.CookieException> exceção é lançada quando um erro é feito ao adicionar um cookie para um contêiner de cookie.  
  
## Dicas associadas  
 **Verifique se que o tamanho do cookie não excede o máximo permitido pelo contêiner de cookies.**  
 Essa exceção é lançada quando é feita uma tentativa de adicionar um <xref:System.Net.Cookie> com comprimento maior que <xref:System.Net.CookieContainer.MaxCookieSize%2A> para um <xref:System.Net.CookieContainer>. O tamanho máximo do cookie padrão é 4096 bytes.  
  
 **Ao definir a propriedade Name para um cookie, verifique se que o valor não é uma referência nula ou uma cadeia de caracteres vazia.**  
 O <xref:System.Net.Cookie.Name%2A> propriedade deve ser inicializada antes de usar uma instância do <xref:System.Net.Cookie> classe. Os seguintes caracteres são reservados e não pode ser usados para este valor de atributo: sinal de igual, ponto e vírgula, vírgula, nova linha \(\\n\), retorno de carro \(\\r\), guia \(\\t\). O caractere de cifrão \($\) não pode ser o primeiro caractere.  
  
 **Ao definir a propriedade Port para um cookie, verifique se que o valor é válido e entre aspas duplas.**  
 O <xref:System.Net.Cookie.Port%2A> atributo restringe as portas pela qual um cookie pode ser enviado. O valor padrão significa sem restrições. Definir a propriedade como uma cadeia de caracteres vazia \(""\) restringe a porta àquela usada na resposta HTTP. Caso contrário, o valor deve ser uma cadeia de caracteres entre aspas que contém valores de portas separados por vírgulas.  
  
 **Ao definir a propriedade Value de um cookie, verifique se que o valor não é nulo.**  
 Os seguintes caracteres são reservados e não pode ser usados para essa propriedade: vírgula, vírgula.  
  
## Consulte também  
 <xref:System.Net.CookieException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [How to: Write a Cookie](../Topic/How%20to:%20Write%20a%20Cookie.md)