---
title: "CA1058: os tipos n&#227;o devem estender determinados tipos base | Microsoft Docs"
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
  - "TypesShouldNotExtendCertainBaseTypes"
  - "CA1058"
helpviewer_keywords: 
  - "CA1058"
  - "TypesShouldNotExtendCertainBaseTypes"
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1058: os tipos n&#227;o devem estender determinados tipos base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesShouldNotExtendCertainBaseTypes|  
|CheckId|CA1058|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo externamente visível estende determinados tipos de base.  Atualmente, esta regra relata os tipos que deriva dos seguintes tipos:  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.Xml.XmlDocument?displayProperty=fullName>  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.Queue?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Stack?displayProperty=fullName>  
  
## Descrição da Regra  
 Para a versão 1 de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] , recomendou\-se derivar novas exceções de <xref:System.ApplicationException>.  A recomendação foi alterado e as novas exceções deve derivar de <xref:System.Exception?displayProperty=fullName> ou de uma das subclasses no namespace de <xref:System> .  
  
 Não crie uma subclasse de <xref:System.Xml.XmlDocument> se você quiser criar uma exibição XML de um modelo ou de uma fonte de dados do objeto subjacente.  
  
### Coleções não genéricas  
 Use e\/ou estender coleções genéricas sempre que possível.  Não estender coleções não genéricas em seu código, a menos que você o enviar previamente.  
  
 **Exemplos do uso incorreto**  
  
```c#  
public class MyCollection : CollectionBase  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollectionBase  
{  
}  
```  
  
 **Exemplos do uso correto**  
  
```c#  
public class MyCollection : Collection<T>  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollection<T>  
{  
}  
```  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, derivar o tipo de um tipo de base diferente ou uma coleção genérica.  
  
## Quando Suprimir Alertas  
 Não suprima um aviso desta regra para violações sobre <xref:System.ApplicationException>.  É seguro suprimir um aviso desta regra para violações sobre <xref:System.Xml.XmlDocument>.  É seguro suprimir um aviso sobre uma coleção não genérico se o código foi liberado anteriormente.