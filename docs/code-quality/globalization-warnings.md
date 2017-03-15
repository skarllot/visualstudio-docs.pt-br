---
title: "Avisos de globaliza&#231;&#227;o | Microsoft Docs"
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
  - "vs.codeanalysis.globalizationrules"
helpviewer_keywords: 
  - "globalização [Visual Studio], avisos"
  - "avisos de globalização"
  - "avisos da análise de código gerenciado, avisos de globalização"
  - "avisos, globalização"
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Avisos de globaliza&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os avisos de globalização dão suporte a bibliotecas mundo\- prontas e aplicativos.  
  
## Nesta seção  
  
|Regra|Descrição|  
|-----------|---------------|  
|[CA1300: especificar MessageBoxOptions](../code-quality/ca1300-specify-messageboxoptions.md)|Para exibir corretamente uma caixa de mensagem para as culturas que usam uma ordem da direita para a esquerda de leitura, os membros de RightAlign e de RtlReading de enumeração de MessageBoxOptions deve ser passado ao método de apresentação.|  
|[CA1301: evitar aceleradores duplicados](../Topic/CA1301:%20Avoid%20duplicate%20accelerators.md)|Uma tecla de acesso, também conhecida como, um acelerador de teclado permite o acesso a um controle usando a tecla ALT.  Quando vários controles de acesso tenham chaves duplicadas, o comportamento da tecla de acesso não é bem definido.|  
|[CA1302: não codificar cadeias de caracteres específicas da localidade](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|A enumeração de System.Environment.SpecialFolder contém membros que fazem referência às pastas do sistema especiais.  Os locais dessas pastas podem ter valores diferentes em sistemas operacionais diferentes; o usuário pode alterar os locais; e os locais são encontrados.  O método de Environment.GetFolderPath retorna os locais que estão associados com a enumeração de Environment.SpecialFolder, localizada e apropria\-os para o computador atualmente em execução.|  
|[CA1303: não passar literais como parâmetros localizados](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Um método externamente visível envia uma cadeia literal como um parâmetro a um construtor o método ou na biblioteca de classes de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] , e essa cadeia de caracteres deve ser localizável.|  
|[CA1304: especificar CultureInfo](../Topic/CA1304:%20Specify%20CultureInfo.md)|Um método ou um construtor chamam um membro que tem uma sobrecarga que aceita um parâmetro de System.Globalization.CultureInfo, e o método ou o construtor não chama a sobrecarga que usa o parâmetro de CultureInfo.  Quando um objeto de CultureInfo ou de System.IFormatProvider não for fornecido, o valor padrão que é fornecido pelo membro sobrecarregado não pode ter o efeito desejado em todas as localidades.|  
|[CA1305: especificar IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)|Um método ou um construtor chamam um ou mais membros que têm as sobrecargas que aceitam um parâmetro de System.IFormatProvider, e o método ou o construtor não chama a sobrecarga que usa o parâmetro de IFormatProvider.  Quando um objeto de System.Globalization.CultureInfo ou de IFormatProvider não for fornecido, o valor padrão que é fornecido pelo membro sobrecarregado não pode ter o efeito desejado em todas as localidades.|  
|[CA1306: definir localidade para tipos de dados](../code-quality/ca1306-set-locale-for-data-types.md)|A localidade determina os elementos com específicos de apresentação de dados, como a formatação que é usado para valores numéricos, símbolos de moeda, e ordem de classificação.  Quando você cria um DataTable ou um conjunto de dados, você deve definir explicitamente a localidade.|  
|[CA1307: especificar StringComparison](../code-quality/ca1307-specify-stringcomparison.md)|Uma operação de comparação de cadeia de caracteres usa uma sobrecarga do método que não definir um parâmetro de StringComparison.|  
|[CA1308: normalizar cadeias de caracteres para maiúsculas](../code-quality/ca1308-normalize-strings-to-uppercase.md)|As cadeias de caracteres devem ser normalizadas em maiúsculas.  Um pequeno grupo de caracteres não pode fazer uma viagem de ida e volta quando são convertidos em minúsculas.|  
|[CA1309: usar StringComparison ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Uma operação de comparação de cadeia de caracteres que é nonlinguistic não define o parâmetro de StringComparison o ordinal ou ao OrdinalIgnoreCase.  Definindo explicitamente o parâmetro a StringComparison.Ordinal ou a StringComparison.OrdinalIgnoreCase, seu código geralmente ganha a velocidade, fica mais correto, e se torna mais confiável.|  
|[CA2101: especificar marshaling para argumentos da cadeia de caracteres P\/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Um membro da invocação de plataforma permitir chamadores parcialmente confiáveis, tem um parâmetro de cadeia de caracteres, e não faz explicitamente para realizar marshaling a cadeia de caracteres.  Isso pode causar uma vulnerabilidade de segurança potencial.|