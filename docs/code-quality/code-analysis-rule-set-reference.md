---
title: "Refer&#234;ncia do conjunto de regras da an&#225;lise de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "conjuntos de regras de análise de código"
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: 43
caps.handback.revision: 43
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Refer&#234;ncia do conjunto de regras da an&#225;lise de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando você configura a análise de código para o código gerenciado projetos em [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], em [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], ou em [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]que você verá uma lista *de conjuntos de regra*interno.  Você pode usar um dos conjuntos standar de regra, ou você pode personalizar uma regra definida para atender aos requisitos do seu projeto.  
  
## Conjuntos de regra disponíveis  
 A tabela a seguir lista os conjuntos de regra padrão:  
  
|||  
|-|-|  
|[Todo o conjunto de regras](../code-quality/all-rules-rule-set.md)|Esse conjunto de regras contém todas as regras.  Executar esse conjunto de regras pode resultar em um grande número de avisos que estão sendo relatado.  Use esta regra definida para obter uma imagem abrangente de todos os problemas em seu código.  Isso pode ajudá\-lo a decidir quais conjuntos mais focalizados de regra são as mais apropriadas para executar para seus projetos.|  
|[Conjunto de regras de correção básico para código gerenciado](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|Essas regras referem\-se aos erros lógicos e os erros comuns feitas no uso de APIs da estrutura.  Inclua esta regra definida para expandir na lista de avisos relatados por regras recomendadas mínimo.|  
|[Conjunto de regras de diretriz do design básico para código gerenciado](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|Essas regras se concentram em impor práticas recomendadas fazer seu código fáceis de entender e usar.  Inclua esta regra definida como se o seu projeto inclui o código de biblioteca ou se você deseja impor práticas recomendadas para o código facilmente sustentável.|  
|[Conjunto de regras de correção estendido para código gerenciado](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|Essas regras se expandem nas regras básicas de exatidão para maximizar os erros de uso da lógica e da estrutura que são relatados.  Dar ênfase adicional é colocada em cenários específicos como aplicativos de interoperabilidade desconectados e do COM.  Considere incluir esta regra definida se um desses cenários se aplica ao seu projeto ou para localizar problemas adicionais no projeto.|  
|[Conjunto de regras de diretrizes do design estendido para código gerenciado](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|Essas regras se expandem nas regras de diretrizes de design básico para maximizar os problemas de usabilidade e de manutenibilidade que são relatados.  Dar ênfase adicional é colocada na nomeação diretrizes.  Considere incluir esta regra definida como se o seu projeto inclui o código de biblioteca ou se você deseja impor os padrões mais altos para escrever o código sustentável.|  
|[Conjunto de regras de globalização para código gerenciado](../code-quality/globalization-rules-rule-set-for-managed-code.md)|Essas regras se concentram nos problemas que impedem que os dados em seu aplicativo são exibidos corretamente quando usados em idiomas diferentes, em localidades, e em culturas.  Inclua esta regra definida se seu aplicativo for encontrado ou globalizados.|  
|[Conjunto de regras mínimas gerenciado para código gerenciado](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|Essas regras se concentram nos problemas mais importantes em seu código para que a análise de código é a mais precisa.  Essas regras são pequenas em número e devem ser executado apenas em edições limitadas do Visual Studio.  Use MinimumRecommendedRules.ruleset com outras edições do Visual Studio.|  
|[Conjunto de regras recomendadas gerenciado para código gerenciado](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|Essas regras se concentram nos problemas mais importantes no código, inclusive buracos na segurança em potencial, falhas de aplicativo, e outros erros importantes de lógica e de design.  Você deve incluir esta regra definida em qualquer regra personalizada e cria para seus projetos.|  
|[Conjunto de regras mínimas misto](../code-quality/mixed-minimum-rules-rule-set.md)|Essas regras se concentram nos problemas mais importantes em seus C\+\+ projeto que dão suporte a Common Language Runtime, incluindo buracos na segurança em potencial e o aplicativo falhará.  Você deve incluir esta regra definida em qualquer regra personalizada e cria C\+\+ para seus projetos que dão suporte a Common Language Runtime.|  
|[Conjunto de regras recomendadas misto](../code-quality/mixed-recommended-rules-rule-set.md)|Essas regras no foco na maioria dos problemas comuns e críticas em seus C\+\+ projeto que dão suporte a Common Language Runtime, incluindo buracos na segurança em potencial, o aplicativo falhará, e outros erros importantes de lógica e de design.  Você deve incluir esta regra definida em qualquer regra personalizada e cria C\+\+ para seus projetos que dão suporte a Common Language Runtime.  Este ruleset é criado para ser configurado com a edição do Visual Studio Professional ou superior.|  
|[Conjunto de regras mínimas nativo](../code-quality/native-minimum-rules-rule-set.md)|Essas regras se concentram nos problemas mais importantes em seu código nativo, incluindo buracos na segurança em potencial e o aplicativo falhará.  Você deve incluir esta regra definida em qualquer regra personalizada e cria para seus projetos nativos.|  
|[Conjunto de regras recomendadas nativo](../code-quality/native-recommended-rules-rule-set.md)|Essas regras o foco no mais importante e os problemas comuns em seu código nativo, incluindo buracos na segurança e potenciais o aplicativo falhará.  Você deve incluir esta regra definida em qualquer regra personalizada e cria para seus projetos nativos.  Este ruleset é criado para funcionar com edição do Visual Studio Professional ou superior.|  
|[Conjunto de regras de segurança para código gerenciado](../code-quality/security-rules-rule-set-for-managed-code.md)|Esse conjunto de regras contém todas as regras de segurança do Microsoft.  Inclua esta regra definida para maximizar o número de problemas potenciais de segurança que são relatadas.|