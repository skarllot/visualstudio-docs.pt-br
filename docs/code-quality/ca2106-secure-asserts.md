---
title: "CA2106: declara&#231;&#245;es seguras | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2106"
  - "SecureAsserts"
helpviewer_keywords: 
  - "CA2106"
  - "SecureAsserts"
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2106: declara&#231;&#245;es seguras
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecureAsserts|  
|CheckId|CA2106|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um método afirma uma permissão e nenhuma verificação de segurança é executado no chamador.  
  
## Descrição da Regra  
 Declare uma permissão de segurança sem executar qualquer verificações de segurança pode deixar uma fraqueza explorável de segurança em seu código.  Uma exames da pilha de segurança para quando uma permissão de segurança é declarada.  Se você afirma uma permissão sem executar nenhuma verificações no chamador, o chamador pode indiretamente executar o código usando suas permissões.  Afirma sem verificações de segurança são permitidos apenas quando você tiver certeza de que declare não pode ser usado em uma maneira prejudicial.  Assert é inofensivo se o código que chama é inofensivo, ou os usuários não podem passar informações para codificar arbitrária que você chama.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, adicione uma procura de segurança para o método ou em seu tipo. declarando  
  
## Quando Suprimir Alertas  
 Suprima um aviso desta regra somente depois revisão de segurança cuidadosa.  
  
## Consulte também  
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 [Diretrizes de codificação segura](../Topic/Secure%20Coding%20Guidelines.md)