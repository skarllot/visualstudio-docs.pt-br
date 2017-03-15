---
title: "Avisos de uso | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.usagerules"
helpviewer_keywords: 
  - "avisos de uso"
  - "avisos da análise de código gerenciado, avisos de uso"
  - "avisos de uso"
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Avisos de uso
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os avisos de uso dão suporte ao uso apropriado do.NET Framework.  
  
## Nesta seção  
  
|Regra|Descrição|  
|-----------|---------------|  
|[CA1801: revisar parâmetros não usados](../Topic/CA1801:%20Review%20unused%20parameters.md)|Uma assinatura de método inclui um parâmetro que não é usado no corpo do método.|  
|[CA1806: não ignore resultados do método](../code-quality/ca1806-do-not-ignore-method-results.md)|Um novo objeto é criado mas nunca usado; ou um método que cria e retorna uma nova cadeia de caracteres é chamado e a nova cadeia de caracteres nunca seja usada; um método ou COM ou de P\/Invoke retorna um HRESULT ou um código de erro que nunca sejam usados.|  
|[CA1816: chamar GC.SuppressFinalize corretamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Um método que é uma implementação Dispose não chama GC.SuppressFinalize; um método ou que não é uma implementação Dispose chama GC.SuppressFinalize; chama um método ou GC.SuppressFinalize e passa algo diferente do \(i no Visual Basic\).|  
|[CA2200: relançar para preservar detalhes da pilha](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Uma exceção é lançada novamente e a exceção é especificado explicitamente na instrução do lançamento.  Se uma exceção é lançada novamente especificando a exceção na instrução do lançamento, a lista das chamadas de método entre o método original que lançou a exceção e o método atual será perdida.|  
|[CA2201: não acionar tipos de exceção reservados](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Isso gerencie o erro original difícil detectar e depurar.|  
|[CA2202: não descartar objetos várias vezes](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Uma implementação do método contém os caminhos de código que poderiam causar várias chamadas para System.IDisposable.Dispose ou a um equivalente de disposição \(como um método de Close\(\) em alguns tipos\) no mesmo objeto.|  
|[CA2204: os literais do recurso devem ter a ortografia correta](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Uma cadeia de caracteres literal em um corpo do método contém uma ou mais palavras que não são reconhecidos pela biblioteca de SPELLING CHECKER da Microsoft.|  
|[CA2205: usar equivalentes gerenciados da API do Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Um método de invocação de plataforma é definido e um método com a funcionalidade equivalente existe na biblioteca de classes do.NET Framework.|  
|[CA2207: inicializar campos estáticos de tipo de valor embutido](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Um tipo de valor declara um construtor estático explícito.  Para corrigir uma violação desta regra, inicializar todos os dados estáticos quando é declarada e remover o construtor estático.|  
|[CA2208: instanciar exceções de argumento corretamente](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|For feita uma chamada para o construtor \(sem parâmetros\) padrão de um tipo de exceção que esteja ou deriva de ArgumentException, ou um argumento incorreto de cadeia de caracteres é passado a um construtor com parâmetros de um tipo de exceção que esteja ou deriva de ArgumentException.|  
|[CA2211: os campos não constantes não devem estar visíveis](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Os campos estáticos que não são constantes ou somente leitura não é seguro para threads.  O acesso a esse campo deve ser cuidadosamente controlado exige e técnicas de programação avançado para sincronizar o acesso ao objeto da classe.|  
|[CA2212: não marcar componentes atendidos com WebMethod](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Um método em um tipo que herde de System.EnterpriseServices.ServicedComponent é marcado com System.Web.Services.WebMethodAttribute.  Como WebMethodAttribute e um método de ServicedComponent têm conflitantes o comportamento e os requisitos para o contexto e a transação fluem, o comportamento do método estarão incorretas em alguns cenários.|  
|[CA2213: os campos descartáveis devem ser descartados](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Um tipo que implementa System.IDisposable declara os campos que são de tipos que também implementam IDisposable.  O método dispose do campo não é chamado pelo método dispose do tipo declarando.|  
|[CA2214: não chamar métodos substituíveis em construtores](../Topic/CA2214:%20Do%20not%20call%20overridable%20methods%20in%20constructors.md)|Quando um construtor chama um método virtual, é possível que o construtor para a instância do que invoca o método não foi executada.|  
|[CA2215: os métodos de descarte devem chamar o descarte da classe base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Se um tipo é herdada de um tipo descartável, deve chamar o método dispose do tipo de base de seu próprio método dispose.|  
|[CA2216: os tipos descartáveis devem declarar o finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Um tipo que implementa System.IDisposable, e tem campos que sugerem o uso de recursos não gerenciado, o não implementa um finalizador conforme descrito por Object.Finalize.|  
|[CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Uma enumeração externamente visível é marcada com FlagsAttribute, e tem um ou mais valores que não são potências de dois ou uma combinação dos outros valores definidos na enumeração.|  
|[CA2218: substituir GetHashCode em igualdades de substituição](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|GetHashCode retorna um valor, com base na instância atual, que é adequada para algoritmos de hash e estruturas de dados como uma tabela de hash.  Dois objetos que têm o mesmo tipo e são iguais devem retornar o mesmo código hash.|  
|[CA2219: não acione exceções em cláusulas de exceção](../Topic/CA2219:%20Do%20not%20raise%20exceptions%20in%20exception%20clauses.md)|Quando uma exceção é gerada em finalmente ou na cláusula de falha, a nova exceção oculta a exceção ativa.  Quando uma exceção é gerada em uma cláusula de filtro, o tempo de execução de captura silenciosamente a exceção.  Isso gerencie o erro original difícil detectar e depurar.|  
|[CA2220: os finalizadores devem chamar o finalizador da classe base](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|O acabamento deveriam ser propagadas pela hierarquia de herança.  Para garantir isso, os tipos devem chamar sua classe base é encerrado o método em seus próprios finalizam o método.|  
|[CA2221: os finalizadores devem ser protegidos](../code-quality/ca2221-finalizers-should-be-protected.md)|Finalizers deve usar o modificador de acesso de família.|  
|[CA2222: não diminuir a visibilidade de membro herdada](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Você não deve alterar o modificador de acesso para membros herdados.  Alterar um membro herdado para particular não impede que os chamadores acessem a implementação da classe base do método.|  
|[CA2223: os membros devem ser diferentes além do tipo de retorno](../Topic/CA2223:%20Members%20should%20differ%20by%20more%20than%20return%20type.md)|Embora Common Language Runtime permitir o uso de tipos de retorno diferenciar membros de outra forma idênticos, este recurso não está em CLS, nem é um recurso comum das linguagens de programação .NET.|  
|[CA2224: substituir igualdades em igualdades de operador de sobrecarga](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Um tipo público implementa o operador de igualdade, mas não substitui Object.Equals.|  
|[CA2225: as sobrecargas do operador têm alternativas nomeadas](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)|Uma sobrecarga do operador foi detectada, e o método backup denominado esperado não foi encontrado.  O membro de backup denominado fornece acesso à mesma funcionalidade que o operador, e é fornecido para os desenvolvedores de programação nos idiomas que não dão suporte a operadores sobrecarregados.|  
|[CA2226: os operadores devem ter sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Um tipo implementa o operador de igualdade ou de desigualdade, e não implementa o operador oposto.|  
|[CA2227: as propriedades de coleção devem ser somente leitura](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Uma propriedade gravável da coleção permite que um usuário substitui a coleção o com uma coleção diferente.  Uma propriedade somente leitura para a coleção de ser substituído mas ainda permite que membros individuais são definidos.|  
|[CA2228: não remeter formatos de recurso não lançados](../Topic/CA2228:%20Do%20not%20ship%20unreleased%20resource%20formats.md)|Os arquivos de recursos que foram compilados usando versões de pré\-lançamento do .NET Framework podem não ser úteis por versões com suporte do.NET Framework.|  
|[CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)|Para corrigir uma violação desta regra, implemente o construtor de serialização.  Para uma classe selada, faça o construtor particular; se não, remova protegida.|  
|[CA2230: usar parâmetros para argumentos variáveis](../code-quality/ca2230-use-params-for-variable-arguments.md)|Um público ou um tipo protegido contêm um público ou protegido um método que usa a convenção de chamada de VarArgs em vez da palavra\-chave de params.|  
|[CA2231: sobrecarregar igualdades de operador em ValueType.Equals substituídos](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Um tipo de valor substitui Object.Equals mas não implementa o operador de igualdade.|  
|[CA2232: marcar pontos de entrada dos Windows Forms com STAThread](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|STAThreadAttribute indica que o modelo de threading COM para o aplicativo é um STA. de thread único.  Esta deverá de atributo estiver presente no ponto de entrada de qualquer aplicativo que usa o Windows Forms; se for omitida, os componentes do windows podem não funcionar corretamente.|  
|[CA2233: as operações não devem estourar](../code-quality/ca2233-operations-should-not-overflow.md)|Operações aritméticas não devem ser executadas sem primeiro validar os operandos, para garantir que o resultado da operação não está fora do intervalo de valores possíveis para os tipos de dados envolvidos.|  
|[CA2234: passar objetos System.Uri em vez de cadeias de caracteres](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)|For feita uma chamada para um método que possui um parâmetro de cadeia de caracteres cujo nome contém “uri”, “URI”, “urn”, “URN”, “URL”, ou “URL”.  O tipo declarando do método contém uma sobrecarga correspondente do método que possui um parâmetro de System.Uri.|  
|[CA2235: marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Um campo da instância de um tipo que não seja serializável é declarado em um tipo que é serializable.|  
|[CA2236: chamar métodos de classe base em tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Para corrigir uma violação desta regra, chame o método ou do construtor de serialização de GetObjectData do tipo de base do método correspondentes derivado do tipo ou o construtor.|  
|[CA2237: marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Para ser reconhecido por Common Language Runtime como serializável, os tipos devem ser marcados com o atributo de SerializableAttribute mesmo se o tipo usa uma rotina de serialização personalizada com a implementação da interface de ISerializable.|  
|[CA2238: implementar métodos de serialização corretamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Um método que manipula um evento de serialização não possui a assinatura, o tipo de retorno ou a visibilidade corretos.|  
|[CA2239: fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Um tipo tem um campo que é marcado com o atributo de System.Runtime.Serialization.OptionalFieldAttribute, e o tipo não fornece métodos de manipulação de eventos de desserialização.|  
|[CA2240: implementar ISerializable corretamente](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)|Para corrigir uma violação desta regra, execute o método de GetObjectData visível e substituível, e verifique se todos os campos de instância serão incluídos no processo de serialização marcados ou explicitamente com o atributo de NonSerializedAttribute.|  
|[CA2241: fornecer argumentos corretos para métodos de formatação](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|O argumento de formato passado a System.String.Format não contém um item de formato que corresponde a cada argumento do objeto, ou vice\-versa.|  
|[CA2242: teste para NaN corretamente](../code-quality/ca2242-test-for-nan-correctly.md)|Essa expressão testa um valor em Single.Nan ou Double.Nan.  Use Single.IsNan \(único\) ou Double.IsNan \(duplo\) para testar o valor.|  
|[CA2243: os literais da cadeia de caracteres de atributo devem ser analisados corretamente](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|O parâmetro literal de cadeia de caracteres de um atributo não analisa corretamente para uma URL, um GUID, ou uma versão.|