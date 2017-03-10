---
title: "CA1302: n&#227;o codificar cadeias de caracteres espec&#237;ficas da localidade | Microsoft Docs"
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
  - "DoNotHardcodeLocaleSpecificStrings"
  - "CA1302"
helpviewer_keywords: 
  - "DoNotHardcodeLocaleSpecificStrings"
  - "CA1302"
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1302: n&#227;o codificar cadeias de caracteres espec&#237;ficas da localidade
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotHardcodeLocaleSpecificStrings|  
|CheckId|CA1302|  
|Categoria|Microsoft.Globalization|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um método usa uma cadeia de caracteres literal que representa parte do caminho de certas pastas do sistema.  
  
## Descrição da Regra  
 A enumeração <xref:System.Environment.SpecialFolder?displayProperty=fullName> contém membros que se referem a pastas especiais do sistema.  Os locais dessas pastas podem ter valores diferentes em diferentes sistemas operacionais, o usuário pode modificar alguns dos locais, e os locais são diferentes para cada idioma.  Um exemplo de pasta especial é a pasta do sistema, que é “C:\\WINDOWS\\system32” em [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] mas é “C:\\WINNT\\system32” em [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)].  O método retorna os locais <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> que estão associados com a enumeração <xref:System.Environment.SpecialFolder>.  Os locais que são retornados por <xref:System.Environment.GetFolderPath%2A> são localizados e próprios para o computador em execução.  
  
 Esta regra cria tokens para os caminhos de pastas recuperados usando o método <xref:System.Environment.GetFolderPath%2A> em níveis distintos de diretório.  Cada cadeia de caracteres literal é comparada aos tokens.  Se uma correspondência for encontrada, assume\-se que o método está criando uma cadeia de caracteres referente ao local do sistema associado com o token.  Para a portabilidade e a localização, use o método <xref:System.Environment.GetFolderPath%2A> para recuperar os locais das pastas de sistema especiais em vez de usar cadeias de caracteres literais.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, recupere o local usando o método <xref:System.Environment.GetFolderPath%2A>.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso resultante desta regra se a cadeia de caracteres literal não é for para fazer referência a um dos locais do sistema associados com a enumeração <xref:System.Environment.SpecialFolder>.  
  
## Exemplo  
 O exemplo a seguir forma o caminho da pasta de dados comuns de aplicativo, que gera três avisos resultantes desta regra.  Em seguida, o exemplo recupera o caminho usando o método <xref:System.Environment.GetFolderPath%2A>.  
  
 [!code-cs[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]  
  
## Regras Relacionadas  
 [CA1303: não passar literais como parâmetros localizados](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)