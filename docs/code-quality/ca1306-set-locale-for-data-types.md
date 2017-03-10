---
title: "CA1306: definir localidade para tipos de dados | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1306"
  - "SetLocaleForDataTypes"
helpviewer_keywords: 
  - "CA1306"
  - "SetLocaleForDataTypes"
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1306: definir localidade para tipos de dados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SetLocaleForDataTypes|  
|CheckId|CA1306|  
|Categoria|Microsoft.Globalization|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um método ou um construtor criou uma ou mais instâncias de <xref:System.Data.DataTable?displayProperty=fullName> ou de <xref:System.Data.DataSet?displayProperty=fullName> e não têm definido explicitamente a propriedade de localidade \(<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> ou <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>\).  
  
## Descrição da Regra  
 A localidade determina os elementos com específicos de apresentação de dados, como a formatação usado para valores numéricos, símbolos de moeda, e ordem de classificação.  Quando você cria <xref:System.Data.DataTable> ou <xref:System.Data.DataSet>, você deve definir a localidade explicitamente.  Por padrão, a localidade para esses tipos é a cultura atual.  Para os dados que são armazenados em um base de dados ou em um arquivo e compartilhados global, a localidade normalmente deve ser definida como a cultura invariável \(<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>\).  Quando os dados são compartilhados por meio de culturas, usa a localidade padrão pode fazer com que o conteúdo de <xref:System.Data.DataTable> ou de <xref:System.Data.DataSet> a ser dispostos incorretamente ou interpretado.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, defina explicitamente a localidade para <xref:System.Data.DataTable> ou <xref:System.Data.DataSet>.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra quando a biblioteca ou o aplicativo são para um público local limitada, os dados não é compartilhado, ou os gera a configuração padrão do comportamento desejado em todos os cenários com suporte.  
  
## Exemplo  
 O exemplo a seguir cria duas instâncias de <xref:System.Data.DataTable> .  
  
 [!code-cs[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]  
  
## Consulte também  
 <xref:System.Data.DataTable?displayProperty=fullName>   
 <xref:System.Data.DataSet?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>