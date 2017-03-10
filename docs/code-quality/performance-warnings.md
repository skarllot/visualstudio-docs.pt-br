---
title: "Avisos de desempenho | Microsoft Docs"
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
  - "vs.codeanalysis.performancerules"
helpviewer_keywords: 
  - "avisos de desempenho"
  - "avisos de desempenho"
  - "desempenho, avisos"
  - "avisos da análise de código gerenciado, avisos de desempenho"
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Avisos de desempenho
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os avisos de desempenho dão suporte a bibliotecas de alto desempenho e aplicativos.  
  
## Nesta seção  
  
|Regra|Descrição|  
|-----------|---------------|  
|[CA1800: não converter desnecessariamente](../code-quality/ca1800-do-not-cast-unnecessarily.md)|As conversões duplicados diminui o desempenho, principalmente quando as conversões são executadas em instruções compactas da iteração.|  
|[CA1801: revisar parâmetros não usados](../Topic/CA1801:%20Review%20unused%20parameters.md)|Uma assinatura de método inclui um parâmetro que não é usado no corpo do método.|  
|[CA1802: usar literais quando apropriado](../code-quality/ca1802-use-literals-where-appropriate.md)|Um campo é declarado estático e somente leitura \(compartilhado e readonly em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\), e iniciado com um valor que é computável em tempo de compilação.  Como o valor atribuído ao campo de destino é computável em tempo de compilação, altere a declaração a um campo de const \(const em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) de modo que o valor é computado em tempo de compilação em vez de em tempo de execução.|  
|[CA1804: remover locais não usados](../code-quality/ca1804-remove-unused-locals.md)|As variáveis locais não usado e as atribuições desnecessários aumenta o tamanho de um desempenho do assembly e a diminuição.|  
|[CA1806: não ignore resultados do método](../code-quality/ca1806-do-not-ignore-method-results.md)|Um novo objeto é criado mas nunca usado, ou um método que cria e retorna uma nova cadeia de caracteres sejam chamados e a nova cadeia de caracteres é usada, nunca ou um método do Component Object Model \(COM\) ou de P\/Invoke retornam um HRESULT ou um código de erro que nunca sejam usados.|  
|[CA1809: evitar locais excessivos](../code-quality/ca1809-avoid-excessive-locals.md)|Uma otimização comuns de desempenho é armazenar um valor em um registro de processador em vez de memória, que é chamado “enregistering o valor”.  Para aumentar a possibilidade de que todas as variáveis locais enregistered, limite o número de variáveis locais a 64.|  
|[CA1810: inicializar campos estáticos de tipo de referência embutido](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Quando um tipo declara um construtor estático explícito, o compilador de \(JIT\) just\-in\-time adiciona uma verificação a cada construtor de método estático e da instância do tipo para garantir que o construtor estático esteve chamado anteriormente.  As verificações estáticos de construtor podem diminuir o desempenho.|  
|[CA1811: evitar código privado não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)|Um membro particular ou interno de nível de assembly \(\) não tem chamadores no assembly, não é invocado por Common Language Runtime, e não é invocado por um representante.|  
|[CA1812: evitar classes internas sem instâncias](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)|Uma instância de um tipo de nível de assembly não é criada pelo código no assembly.|  
|[CA1813: evitar atributos não lacrados](../code-quality/ca1813-avoid-unsealed-attributes.md)|A biblioteca de classes de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] fornece métodos para recuperar atributos personalizados.  Por padrão, esses métodos da hierarquia de herança do atributo.  Selar o atributo elimina a pesquisa pela hierarquia de herança e pode melhorar o desempenho.|  
|[CA1814: preferir matrizes denteadas em relação às multidimensionais](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Uma matriz denteada é uma matriz cujos elementos sejam matrizes.  As matrizes que compõem os elementos podem ter os tamanhos diferentes, o que pode resultar em menos espaço desperdiçado para alguns conjuntos de dados.|  
|[CA1815: substituir igualdades e igualdades de operador em tipos de valor](../Topic/CA1815:%20Override%20equals%20and%20operator%20equals%20on%20value%20types.md)|Para tipos de valor, a implementação herdada de igual usa a biblioteca de reflexão e compara o conteúdo de todos os campos.  Reflexão é computacionalmente cara, e comparar cada campo por igualdade pode ser desnecessário.  Se você espera que os usuários comparar ou classificar instâncias, ou se usar instâncias como a tabela de hash chaves, seu tipo de valor deve implementar iguais.|  
|[CA1816: chamar GC.SuppressFinalize corretamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Um método que é uma implementação Dispose não chama GC.SuppressFinalize, ou um método que não é uma implementação Dispose chama GC.SuppressFinalize, ou chamadas GC.SuppressFinalize de um método e passa algo diferente do \(i em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).|  
|[CA1819: as propriedades não devem retornar matrizes](../code-quality/ca1819-properties-should-not-return-arrays.md)|As matrizes retornadas por propriedades para gravação não são protegidas, mesmo se a propriedade é somente leitura.  Para manter a matriz inalterável, a propriedade deve retornar uma cópia da matriz.  Normalmente, os usuários não adversas integrarem as implicações de desempenho de chamar essas propriedades.|  
|[CA1820: teste para cadeias de caracteres vazias usando o comprimento da cadeia de caracteres](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Comparar cadeias de caracteres usando a propriedade de String.Length ou o método de String.IsNullOrEmpty é significativamente mais rápida do que usando iguais.|  
|[CA1821: remover finalizadores vazios](../code-quality/ca1821-remove-empty-finalizers.md)|Sempre que possível, para evitar finalizers devido à sobrecarga adicional de desempenho que é envolvida no tempo de vida do objeto de rastreamento.  Um finalizador vazia incorre a sobrecarga adicionada sem nenhum benefício.|  
|[CA1822: marcar membros como estáticos](../Topic/CA1822:%20Mark%20members%20as%20static.md)|Os membros que não acessam dados da instância ou métodos da instância de chamada podem ser marcados como estático \(compartilhada em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  Depois que você marca os métodos como estático, o compilador emitirá sites nonvirtual da chamada para esses membros.  Isso pode proporcionar um ganho mensurável de desempenho para o código de acentos.|  
|[CA1823: evitar campos privados não usados](../code-quality/ca1823-avoid-unused-private-fields.md)|Os campos particulares foram detectados que não parece ser acessados no assembly.|  
|[CA1824: marcar assemblies com NeutralResourcesLanguageAttribute](../Topic/CA1824:%20Mark%20assemblies%20with%20NeutralResourcesLanguageAttribute.md)|O atributo de NeutralResourcesLanguage informa o ResourceManager de idioma que foi usada para exibir os recursos de uma cultura neutra para um assembly.  Isso melhora o desempenho da pesquisa para o primeiro recursos que você carrega e reduzir seu conjunto de trabalho.|