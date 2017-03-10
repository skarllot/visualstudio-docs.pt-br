---
title: "CA1415: declarar P/Invokes corretamente | Microsoft Docs"
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
  - "CA1415"
  - "DeclarePInvokesCorrectly"
helpviewer_keywords: 
  - "CA1415"
  - "DeclarePInvokesCorrectly"
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1415: declarar P/Invokes corretamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclarePInvokesCorrectly|  
|CheckId|CA1415|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Sem\-quebras \- se o P\/Invoke que declara o parâmetro não pode ser consultado fora do assembly.  Interromper \- se o P\/Invoke que declara o parâmetro pode ser consultado fora do assembly.|  
  
## Causa  
 Um método de invocação de plataforma for declarado incorretamente.  
  
## Descrição da Regra  
 Um método de invocação de plataforma acessa o código não gerenciado e é definido com a palavra\-chave de `Declare` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou em <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>.  Atualmente, esta regra procura as declarações de método de invocação de plataforma que visem as funções do Win32 que têm um ponteiro para um parâmetro SOBREPOR da estrutura e o parâmetro gerenciado correspondente não é um ponteiro para uma estrutura de <xref:System.Threading.NativeOverlapped?displayProperty=fullName> .  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, declarar corretamente o método de invocação de plataforma.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra os métodos de invocação de plataforma que violam a regra e satisfazem a regra.  
  
 [!CODE [FxCop.Interoperability.DeclarePInvokes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes#1)]  
  
## Consulte também  
 [Interoperação com código não gerenciado](../Topic/Interoperating%20with%20Unmanaged%20Code.md)