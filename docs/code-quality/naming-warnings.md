---
title: "Avisos de nomenclatura | Microsoft Docs"
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
  - "vs.codeanalysis.namingrules"
helpviewer_keywords: 
  - "avisos da análise de código gerenciado, avisos de nomenclatura"
  - "avisos de nomenclatura"
  - "avisos de nomenclatura"
ms.assetid: f97223ce-1d39-4134-81c9-fff2c75d979b
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Avisos de nomenclatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nomeando avisos dar suporte à conformidade com as convenções de nomenclatura das diretrizes de design de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] .  
  
## Nesta seção  
  
|Regra|Descrição|  
|-----------|---------------|  
|[CA1700: não nomeie valores de enum como 'Reservados'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Esta regra pressupõe que um membro da enumeração que tenha um nome que contém “reservado” não é usado atualmente mas é um espaço reservado a ser renomeado ou removido em uma versão futura.  Renomear ou remover um membro é uma alteração.|  
|[CA1713: os eventos não devem ter um prefixo anterior ou posterior](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|O nome de início de um evento com “antes de” ou “depois de”.  Para nomear eventos relacionados que são gerados em uma sequência específica, use o tempo atual ou passado para indicar a posição relativa na sequência de ações.|  
|[CA1714: os enums de sinalizadores devem ter nomes plurais](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Uma enumeração pública tem o atributo de System.FlagsAttribute e seu nome não termina com “s”.  Tipos que é marcado com FlagsAttribute tem nomes que são plural porque o atributo indica que mais de um valor pode ser especificado.|  
|[CA1704: os identificadores do recurso devem ter a ortografia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|O nome de um identificador externamente visível contém uma ou mais palavras que não são reconhecidos pela biblioteca de SPELLING CHECKER da Microsoft.|  
|[CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Os identificadores de namespaces, tipos, membros, e parâmetros não podem diferir somente por casos como os idiomas que visam Common Language Runtime não é necessário fazer diferenciação de maiúsculas e minúsculas.|  
|[CA1715: os identificadores devem ter o prefixo correto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|O nome de uma interface visível não externamente me começa com um capital “”.  O nome de um parâmetro de tipo genérico em um tipo ou um método externamente visível não começa com um capital “T”.|  
|[CA1720: os identificadores não devem conter nomes de tipo](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|O nome de um parâmetro em um membro externamente visível contém um nome de tipo de dados, ou nome de um membro externamente visível contém um nome específico do idioma do tipo de dados.|  
|[CA1722: os identificadores não devem ter prefixo incorreto](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Por convenção, somente determinados elementos de programação têm nomes que começam com um prefixo específico.|  
|[CA1711: os identificadores não devem ter sufixo incorreto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Por convenção, somente os nomes dos tipos que estendem determinados tipos de base ou que implementam determinadas interfaces, ou tipos derivados desses tipos, deve terminar com sufixos específicos reservados.  Outros nomes de tipo não devem usar esses sufixos reservadas.|  
|[CA1717: apenas enums FlagsAttribute devem ter nomes plurais](../Topic/CA1717:%20Only%20FlagsAttribute%20enums%20should%20have%20plural%20names.md)|As convenções de nomenclatura ditam que um nome plural de uma enumeração indica que mais de um valor de enumeração pode ser especificado ao mesmo tempo.|  
|[CA1725: os nomes de parâmetro devem corresponder à declaração base](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|A nomeação consistente dos parâmetros em uma hierarquia de substituição aumentar a usabilidade das substituições do método.  Um nome de parâmetro de um método derivada que difere do nome na declaração de base pode causar confusão quanto se o método for uma substituição do método de base ou de uma nova sobrecarga do método.|  
|[CA1719: os nomes de parâmetro não devem corresponder aos nomes de membro](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Um nome de parâmetro deve comunicar o significado de um parâmetro, nome do membro deve comunicar o significado de um membro.  Seria um design raro onde esses são os mesmos.  Nomeando um parâmetro da mesma forma como o nome do membro é unintuitive e faz a biblioteca difícil usar.|  
|[CA1701: as palavras compostas da cadeia de caracteres do recurso devem ter maiúsculas e minúsculas corretas](../Topic/CA1701:%20Resource%20string%20compound%20words%20should%20be%20cased%20correctly.md)|Cada palavra da cadeia de caracteres de recurso são divididas em tokens que são baseados em maiúsculas e minúsculas.  Cada combinação contíguo de dois token é verificada pela biblioteca de SPELLING CHECKER da Microsoft.  Se reconhecidas, as palavras gerenciem uma violação da regra.|  
|[CA1703: as cadeias de caracteres do recurso devem ter a ortografia correta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|Uma cadeia de caracteres de recurso contém uma ou mais palavras que não são reconhecidos pela biblioteca de SPELLING CHECKER da Microsoft.|  
|[CA1724: os nomes de tipo não devem corresponder a namespaces](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|Os nomes de tipo não devem corresponder aos nomes de namespaces que são definidas na biblioteca de classes de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] .  A violação desta regra pode reduzir a usabilidade de biblioteca.|  
|[CA1707: os identificadores não devem conter sublinhados](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Por convenção, os nomes de identificadores não contêm o caractere de sublinhado \(\_\).  Esta regra verifica namespaces, tipos, membros, e parâmetros.|  
|[CA1721: os nomes de propriedade não devem corresponder a métodos get](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|O nome de um público ou inicia protegidos do membro com “e” correspondem a obtenção de outra forma o nome de um público ou de uma propriedade protegida. “Obter” métodos e as propriedades devem ter nomes que distinguem claramente a função.|  
|[CA1716: os identificadores não devem corresponder a palavras\-chave](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Um nome do namespace ou um nome de tipo correspondem a uma palavra\-chave reservada em uma linguagem de programação.  Os identificadores de namespaces e tipos não devem corresponder às palavras\-chave que são definidos pelos idiomas que visam Common Language Runtime.|  
|[CA1726: usar termos preferenciais](../code-quality/ca1726-use-preferred-terms.md)|O nome de um identificador externamente visível inclui um termo para que uma alternativa, termo preferido existe.  Como alternativa, o nome inclui o termo “sinalizador” ou “sinalizadores”.|  
|[CA1709: os identificadores do recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Por convenção, os nomes de parâmetros usam as caixas de camelo, e o namespace, digite e, os nomes de membro usam o uso de maiúsculas e minúsculas de Pascal.|  
|[CA1702: palavras compostas devem ter maiúsculas e minúsculas corretas](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|O nome de um identificador contiver várias palavras e, pelo menos uma das palavras parece ser uma palavra compostas que não sejam encaixotadas corretamente.|  
|[CA1712: não use valores enum como prefixo com o nome do tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|Os nomes dos membros da enumeração não são prefixados com o nome do tipo como as informações de tipo deve ser fornecida por ferramentas de desenvolvimento.|  
|[CA1710: os identificadores devem ter o sufixo correto](../Topic/CA1710:%20Identifiers%20should%20have%20correct%20suffix.md)|Por convenção, os nomes dos tipos que estendem determinados tipos de base ou que implementam determinadas interfaces, ou tipos derivados desses tipos, têm um sufixo associado ao tipo de base ou a interface.|