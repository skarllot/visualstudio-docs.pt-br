---
title: "CA1711: os identificadores n&#227;o devem ter sufixo incorreto | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1711"
  - "IdentifiersShouldNotHaveIncorrectSuffix"
helpviewer_keywords: 
  - "CA1711"
  - "IdentifiersShouldNotHaveIncorrectSuffix"
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1711: os identificadores n&#227;o devem ter sufixo incorreto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|  
|CheckId|CA1711|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um identificador tem um sufixo incorreto.  
  
## Descrição da Regra  
 Por convenção, somente os nomes dos tipos que estendem determinados tipos de base ou que implementam determinadas interfaces, ou tipos derivados desses tipos, deve terminar com sufixos específicos reservados.  Outros nomes de tipo não devem usar esses sufixos reservadas.  
  
 A tabela a seguir lista os sufixos reservadas e os tipos de base e interfaces com associados.  
  
|Sufixo|Tipo de base\/interface|  
|------------|-----------------------------|  
|Atributo|<xref:System.Attribute?displayProperty=fullName>|  
|Coleção|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|  
|Dicionário|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|  
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|  
|EventHandler|Um representante do manipulador de eventos|  
|Exceção|<xref:System.Exception?displayProperty=fullName>|  
|Permissão|<xref:System.Security.IPermission?displayProperty=fullName>|  
|Fila|<xref:System.Collections.Queue?displayProperty=fullName>|  
|Pilha|<xref:System.Collections.Stack?displayProperty=fullName>|  
|Fluxo|<xref:System.IO.Stream?displayProperty=fullName>|  
  
 Além disso, os seguintes sufixos se **não** é usado:  
  
-   Delegate  
  
-   Enum  
  
-   Executa \- use “core” em vez  
  
-   O sufixo ex ou semelhante para distingui\-lo de uma versão anterior do mesmo tipo  
  
 Convenções de nomenclatura dão uma aparência comum para bibliotecas que tem como foco o common language runtime.  Isto reduz a curva de aprendizado que é necessária para novas bibliotecas de software, e aumenta confiança dos clientes de que a biblioteca foi desenvolvida por alguém que com experiência programar código gerenciado.  
  
## Como Corrigir Violações  
 Remova o sufixo do nome do tipo.  
  
## Quando Suprimir Alertas  
 Não suprima um aviso desta regra a menos que o sufixo tem um significado inequívoco no domínio de aplicativo.  
  
## Regras Relacionadas  
 [CA1710: os identificadores devem ter o sufixo correto](../Topic/CA1710:%20Identifiers%20should%20have%20correct%20suffix.md)  
  
## Consulte também  
 [Atributos](../Topic/Attributes1.md)   
 [Delegados e eventos](http://msdn.microsoft.com/pt-br/d98fd58b-fa4f-4598-8378-addf4355a115)