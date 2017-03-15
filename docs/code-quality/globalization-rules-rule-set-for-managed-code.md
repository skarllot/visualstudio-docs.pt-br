---
title: "Conjunto de regras de globaliza&#231;&#227;o para c&#243;digo gerenciado | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Conjunto de regras de globaliza&#231;&#227;o para c&#243;digo gerenciado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode usar a regra das regras de globalização do Microsoft definida para enfatizar os problemas que possam impedir que os dados em seu aplicativo sejam exibidos corretamente em idiomas diferentes, em localidades, e em culturas.  Você deve incluir esta regra definida como se seu aplicativo for encontrado, globalizados, ou ambos.  
  
|Regra|Descrição|  
|-----------|---------------|  
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|Especifique MessageBoxOptions|  
|[CA1301](../Topic/CA1301:%20Avoid%20duplicate%20accelerators.md)|Evite aceleradores duplicados|  
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Não tornam as cadeias de caracteres específicas da localidade de hardcode|  
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Não transmita literais como parâmetros localizados|  
|[CA1304](../Topic/CA1304:%20Specify%20CultureInfo.md)|Especificar CultureInfo|  
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|Especifique IFormatProvider|  
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Definir a localidade para tipos de dados|  
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|Especifique StringComparison|  
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normalização cadeias de caracteres para letras maiúsculas|  
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Use StringComparison ordinal|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Especifique que o marshaling para argumentos de cadeia de caracteres de P\/Invoke|