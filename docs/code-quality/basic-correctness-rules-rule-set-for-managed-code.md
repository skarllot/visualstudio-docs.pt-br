---
title: "Conjunto de regras de corre&#231;&#227;o b&#225;sico para c&#243;digo gerenciado | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 631f0daf-1d42-4c90-a7dc-1a6a9de64c93
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Conjunto de regras de corre&#231;&#227;o b&#225;sico para c&#243;digo gerenciado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A exatidão básica regras se concentra ajustados de regra em erros lógicos e de erros comuns no uso de APIs da estrutura.  As regras básicas de exatidão incluem as regras em conjunto mínimo recomendado da regra de regras.  Para obter mais informações, consulte [Conjunto de regras recomendadas gerenciado para código gerenciado](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) você deve incluir esta regra definida para expandir na lista de avisos que o mínimo recomendado o relatório de regras.  
  
 A tabela a seguir descreve todas as regras em conjunto básico de regra das regras de correção da Microsoft.  
  
|Regra|Descrição|  
|-----------|---------------|  
|[CA1001](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)|Tipos que possui campos descartáveis deve ser descartável|  
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Declare manipuladores de eventos corretamente|  
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Marcar os assemblies com AssemblyVersionAttribute|  
|[CA1033](../Topic/CA1033:%20Interface%20methods%20should%20be%20callable%20by%20child%20types.md)|Os métodos da interface devem estar acessíveis por tipos de filho|  
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Tipos que possui recursos nativos deve ser descartável|  
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Mover P\/Invokes à classe de NativeMethods|  
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Não ocultar métodos da classe base|  
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Implemente corretamente IDisposable|  
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Não digite as exceções em locais inesperados|  
|[CA1301](../Topic/CA1301:%20Avoid%20duplicate%20accelerators.md)|Evite aceleradores duplicados|  
|[CA1400](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)|Os pontos de entrada de P\/Invoke devem existir|  
|[CA1401](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)|P\/Invokes não deve ser visível|  
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Os tipos de layout automático não deve ser visível COM|  
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Chame GetLastError imediatamente depois de P\/Invoke|  
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Os tipos de base visíveis de tipo COM o devem ser visível COM|  
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Os métodos de registro COM o devem ser correspondidos|  
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Declare P\/Invokes corretamente|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Remova os finalizers vazias|  
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Os campos do tipo de valor devem ser portáteis|  
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|As declarações de P\/Invoke devem ser portáteis|  
|[CA2002](../Topic/CA2002:%20Do%20not%20lock%20on%20objects%20with%20weak%20identity.md)|Não bloqueie em objetos de identidade fraco|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Revise consultas SQL para vulnerabilidades de segurança|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Especifique que o marshaling para argumentos de cadeia de caracteres de P\/Invoke|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Segurança declarativa revisão em tipos de valor|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Os ponteiros não devem ser visíveis|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Os tipos não seguros deve expor campos|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|A segurança do método deve ser um superconjunto do tipo|  
|[CA2116](../Topic/CA2116:%20APTCA%20methods%20should%20only%20call%20APTCA%20methods.md)|Os métodos de APTCA só devem chamar métodos de APTCA|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Os tipos de APTCA só devem estender tipos de base de APTCA|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Não expõe métodos indiretamente com as demandas de link|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|As demandas do link de substituição devem ser idênticas com base|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Cláusulas vulneráveis de quebra automática finalmente tente externa|  
|[CA2126](../Topic/CA2126:%20Type%20link%20demands%20require%20inheritance%20demands.md)|As demandas do link do tipo exigem demandas de herança|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Os tipos críticos de segurança não podem participar da equivalência do tipo|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Os construtores padrão devem ser pelo menos críticos quanto construtores padrão do tipo de base|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|O delega devem associar a transparência consistente com métodos|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Os métodos devem manter a transparência consistente ao substituir métodos de base|  
|[CA2137](../Topic/CA2137:%20Transparent%20methods%20must%20contain%20only%20verifiable%20IL.md)|Os métodos transparentes devem conter apenas o IL verificável|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Os métodos transparentes não devem chamar métodos com o atributo de SuppressUnmanagedCodeSecurity|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|O código transparente não deve referenciar itens críticos de segurança|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Os métodos transparentes não devem satisfazer LinkDemands|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Os tipos devem ser pelo menos críticos quanto os tipos de base e interfaces|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Os métodos transparentes não podem usar segurança afirmam|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Os métodos transparentes não devem chamar em código nativo|  
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Lançar novamente para preservar detalhes da pilha|  
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Não remove objetos várias vezes|  
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Inicializar os campos estáticos de tipo de valor de tabela embutida|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Não marque componentes atendidos com WebMethod|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Os campos descartáveis devem ser removidos|  
|[CA2214](../Topic/CA2214:%20Do%20not%20call%20overridable%20methods%20in%20constructors.md)|Não chame métodos overridable nos construtores|  
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Os tipos descartáveis devem declarar o finalizador|  
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Finalizers deve chamar o finalizador da classe base|  
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Construtores de serialização de ferramentas|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Operador de igual de sobrecarga em substituir ValueType.Equals|  
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Pontos de entrada do Windows Forms de marca a STAThread|  
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Marcar todos os campos não serializáveis|  
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Chamar métodos da classe base em tipos de ISerializable|  
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Marcar tipos de ISerializable com SerializableAttribute|  
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Implementar os métodos de serialização corretamente|  
|[CA2240](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)|Implementar ISerializable corretamente|  
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Forneça argumentos corretos para formatação métodos|  
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Teste para NaN corretamente|  
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Os enum devem ter o valor zero|  
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Carga do operador que equivale ao sobrecarregamento adicionam e subtraia\-o|  
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Não transmita literais como parâmetros localizados|  
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normalização cadeias de caracteres para letras maiúsculas|  
|[CA1806](../code-quality/ca1806-do-not-ignore-method-results.md)|Não ignore resultados do método|  
|[CA1816](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Chame GC.SuppressFinalize corretamente|  
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|As propriedades não devem retornar matrizes|  
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Teste para cadeias de caracteres vazias usando o comprimento da cadeia de caracteres|  
|[CA1903](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Use apenas a API da estrutura de destino|  
|[CA2004](../Topic/CA2004:%20Remove%20calls%20to%20GC.KeepAlive.md)|Remover chamadas a GC.KeepAlive|  
|[CA2006](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Use SafeHandle para encapsular recursos nativos|  
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Exceções non\-CLSCompliant de captura em manipuladores gerais|  
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Não declarar tipos mutáveis somente leitura de referência|  
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Os campos de matriz não devem ser somente leitura|  
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Afirma Seguro|  
|[CA2115](../Topic/CA2115:%20Call%20GC.KeepAlive%20when%20using%20native%20resources.md)|Chame GC.KeepAlive ao usar recursos nativos|  
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Métodos do selo que satisfazem interfaces privadas|  
|[CA2120](../Topic/CA2120:%20Secure%20serialization%20constructors.md)|Construtores de serialização seguros|  
|[CA2121](../Topic/CA2121:%20Static%20constructors%20should%20be%20private.md)|Os construtores estáticos devem ser privados|  
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|As constantes críticos de segurança devem ser transparentes|  
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Use equivalentes gerenciados da API do Win32|  
|[CA2215](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Disponha métodos deve chamar a classe base descartado|  
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Finalizers deve ser protegido|  
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Não diminuir a visibilidade herdada do membro|  
|[CA2223](../Topic/CA2223:%20Members%20should%20differ%20by%20more%20than%20return%20type.md)|Os membros precisarem ser diferentes por mais do que o tipo de retorno|  
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Iguais de substituição em sobrecarregar iguais do operador|  
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Os operadores devem ter sobrecargas simétricas|  
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|As propriedades da coleção devem ser somente leitura|  
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Fornecer métodos de desserialização para campos opcionais|