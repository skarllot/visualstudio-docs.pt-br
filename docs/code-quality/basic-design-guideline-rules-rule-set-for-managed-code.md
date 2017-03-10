---
title: "Conjunto de regras de diretriz do design b&#225;sico para c&#243;digo gerenciado | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Conjunto de regras de diretriz do design b&#225;sico para c&#243;digo gerenciado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode usar a regra das regras de diretrizes de design básico do Microsoft definida para enfatizar facilitar seu código entender e usar.  Você deve incluir esta regra definida como se o seu projeto inclui o código de biblioteca ou se você deseja impor práticas recomendadas para o código que é fácil de manter.  
  
 As regras de diretrizes de design básico inclui todas as regras em conjunto mínimo da regra das regras do Microsoft Recommeded.  Para obter uma lista das regras mínimas, consulte [Conjunto de regras recomendadas gerenciado para código gerenciado](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md).  
  
 A tabela a seguir descreve todas as regras no conjunto de regras das regras de diretrizes de design básico da Microsoft.  
  
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
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|Não declarar membros estáticos em tipos genéricos|  
|[CA1002](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)|Não expõe listas genéricas|  
|[CA1003](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)|Use instâncias genéricas do manipulador de eventos|  
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|Os métodos genéricos devem fornecer o parâmetro de tipo|  
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Evite parâmetros em excesso em tipos genéricos|  
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|Aninhar não genérico em assinaturas de membro|  
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|Use produtos genéricas onde apropriado|  
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Os enum devem ter o valor zero|  
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|As coleções devem implementar a interface genérica|  
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Considere passar tipos de base como parâmetros|  
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|Os tipos de sumário não devem ter construtores|  
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Carga do operador que equivale ao sobrecarregamento adicionam e subtraia\-o|  
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|Assemblies de marca a CLSCompliantAttribute|  
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|Assemblies de marca a ComVisibleAttribute|  
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Atributos de marca a AttributeUsageAttribute|  
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Defina acessadores para argumentos de atributo|  
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Os indicadores não devem ser multidimensionais|  
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|Use as propriedades onde apropriado|  
|[CA1025](../Topic/CA1025:%20Replace%20repetitive%20arguments%20with%20params%20array.md)|Substitua os argumentos e repetitivos com a matriz de param|  
|[CA1026](../Topic/CA1026:%20Default%20parameters%20should%20not%20be%20used.md)|Os parâmetros padrão não devem ser usados|  
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Enum de marca a FlagsAttribute|  
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|O armazenamento de enum deve ser Int32|  
|[CA1030](../Topic/CA1030:%20Use%20events%20where%20appropriate.md)|Use eventos quando apropriado|  
|[CA1031](../Topic/CA1031:%20Do%20not%20catch%20general%20exception%20types.md)|Não capturar tipos de exceções gerais|  
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Implementar construtores padrão de exceção|  
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|Os tipos aninhados não devem ser visíveis|  
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|As implementações de ICollection digitaram altamente membros|  
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|Métodos de substituição em tipos comparáveis|  
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Os enumeradores devem estar fortemente tipado|  
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|Listas são digitadas altamente|  
|[CA1041](../Topic/CA1041:%20Provide%20ObsoleteAttribute%20message.md)|Fornecer a mensagem de ObsoleteAttribute|  
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Use a integral ou cadeia de caracteres do argumento para indicadores|  
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|As propriedades não devem ser somente gravação|  
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|Não iguais carga do operador em tipos de referência|  
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Não declarar membros protegidos em tipos selados|  
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Não declarar membros virtuais em tipos selados|  
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|Declare namespaces em|  
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|Não declarar campos visíveis da instância|  
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Os tipos estáticos de suporte devem ser selados|  
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|Os tipos estáticos de suporte não devem ter construtores|  
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Os parâmetros de URI não devem ser cadeias de caracteres|  
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Os valores de retorno de URI não devem ser cadeias de caracteres|  
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|As propriedades do URI não devem ser cadeias de caracteres|  
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|As sobrecargas do URI de cadeia de caracteres chamam sobrecargas de System.Uri|  
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|Os tipos não devem estender determinados tipos de base|  
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|Os membros não deve expor determinados tipos concretos|  
|[CA1064](../Topic/CA1064:%20Exceptions%20should%20be%20public.md)|As exceções devem ser públicas|  
|[CA1500](../Topic/CA1500:%20Variable%20names%20should%20not%20match%20field%20names.md)|Nomes de variáveis não devem corresponder aos nomes de campo|  
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|Evite a complexidade excessiva|  
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Os identificadores devem ser diferentes por mais de casos|  
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Os identificadores não devem corresponder a palavra\-chave|  
|[CA1801](../Topic/CA1801:%20Review%20unused%20parameters.md)|Parâmetros não usada de revisão|  
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|Remova os locais não usado|  
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|Evite locais em excesso|  
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Inicializar os campos estáticos do tipo de referência embutida|  
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|Evite código privado uncalled|  
|[CA1812](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)|Evite ajustar uninstantiated classes internas|  
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|Evite ajustar unsealed atributos|  
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Prefer entalhou matrizes sobre multidimensional|  
|[CA1815](../Topic/CA1815:%20Override%20equals%20and%20operator%20equals%20on%20value%20types.md)|Igual a substituição e iguais do operador em tipos de valor|  
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|As propriedades não devem retornar matrizes|  
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Teste para cadeias de caracteres vazias usando o comprimento da cadeia de caracteres|  
|[CA1822](../Topic/CA1822:%20Mark%20members%20as%20static.md)|Membros da marca como estático|  
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|Evite campos particulares não usado|  
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Não digite tipos de exceção permitidos|  
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Use equivalentes gerenciados da API do Win32|  
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Criar uma instância do argumento exceções corretamente|  
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Os campos de não constante não devem ser visíveis|  
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Não marque enum com FlagsAttribute|  
|[CA2219](../Topic/CA2219:%20Do%20not%20raise%20exceptions%20in%20exception%20clauses.md)|Não digite as exceções em cláusulas de exceção|  
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Finalizers deve ser protegido|  
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Não diminuir a visibilidade herdada do membro|  
|[CA2223](../Topic/CA2223:%20Members%20should%20differ%20by%20more%20than%20return%20type.md)|Os membros precisarem ser diferentes por mais do que o tipo de retorno|  
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Iguais de substituição em sobrecarregar iguais do operador|  
|[CA2225](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)|As sobrecargas do operador denominado substituições|  
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Os operadores devem ter sobrecargas simétricas|  
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|As propriedades da coleção devem ser somente leitura|  
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Param use para argumentos variáveis|  
|[CA2234](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)|Objetos de passagem System.Uri em vez de cadeias de caracteres|  
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Fornecer métodos de desserialização para campos opcionais|