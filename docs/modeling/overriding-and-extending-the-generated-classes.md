---
title: Substituindo e estendendo as Classes geradas | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
ms.assetid: 30baa60d-a8ea-4611-96c1-8fcc3317cf21
caps.latest.revision: 15
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 81f218f9c0d9cd5d9c6abf8f4f9f0fb78181f4f9
ms.lasthandoff: 02/22/2017

---
# <a name="overriding-and-extending-the-generated-classes"></a>Substituindo e estendendo as classes geradas
Sua definição de DSL é uma plataforma na qual você pode criar um conjunto poderoso de ferramentas com base em uma linguagem específica do domínio. Muitas extensões e adaptações podem ser feitas substituindo e estendendo as classes geradas a partir da definição de DSL. Essas classes incluem não apenas as classes de domínio que você tiver definido explicitamente no diagrama de definição de DSL, mas também outras classes que definem a caixa de ferramentas, explorer, serialização e assim por diante.  
  
## <a name="extensibility-mechanisms"></a>Mecanismos de extensibilidade  
 Vários mecanismos são fornecidos para que você possa estender o código gerado.  
  
### <a name="overriding-methods-in-a-partial-class"></a>Substituindo métodos em uma classe parcial  
 Definições de classes parciais permitem que uma classe seja definida em mais de um único local. Isso permite que você separe o código gerado do código que você escreve. Em seu código escrito manualmente, você pode substituir classes herdadas pelo código gerado.  
  
 Por exemplo, se na definição de DSL, você define uma classe de domínio chamada `Book`, você pode escrever código personalizado que adiciona métodos de substituição:  
  
 `public partial class Book`  
  
 `{`  
  
 `protected override void OnDeleting()`  
  
 `{`  
  
 `MessageBox.Show("Deleting book " + this.Title);`  
  
 `base.OnDeleting();`  
  
 `} }`  
  
> [!NOTE]
>  Para substituir os métodos em uma classe gerada, sempre escreva seu código em um arquivo separado de arquivos gerados. Normalmente, o arquivo está contido em uma pasta chamada Códigopersonalizado. Se você fizer alterações no código gerado, elas serão perdidas quando você gerar novamente o código da definição de DSL.  
  
 Para descobrir quais métodos que você pode substituir, digite **substituir** na classe, seguido por um espaço. A dica de ferramenta do IntelliSense informará quais métodos podem ser substituídos.  
  
### <a name="double-derived-classes"></a>Classes derivadas de duplo  
 A maioria dos métodos em classes geradas é herdada de um conjunto fixo de classes nos namespaces de modelagem. No entanto, alguns métodos são definidos no código gerado. Normalmente, isso significa que você não pode substituí-los; Você não pode substituir em uma classe parcial de métodos que são definidos em outra definição parcial da mesma classe.  
  
 No entanto, você pode substituir esses métodos, definindo o **gera derivado duplo** sinalizador para a classe de domínio. Este faz com que duas classes a serem gerados, sendo uma classe base abstrata da outra. Todas as definições de método e propriedade estão na classe base, e é somente o construtor na classe derivada.  
  
 Por exemplo, no exemplo Library.dsl, o `CirculationBook` classe de domínio tem a `Generates``Double Derived` definida como `true`. O código gerado para essa classe de domínio contém duas classes:  
  
-   `CirculationBookBase`, que é um resumo e que contém todos os métodos e propriedades.  
  
-   `CirculationBook`, que é derivado de `CirculationBookBase`. Está vazio, exceto para seus construtores.  
  
 Para substituir qualquer método, você cria uma definição parcial da classe derivada, como `CirculationBook`. Você pode substituir os métodos gerados e os métodos herdados da estrutura de modelagem.  
  
 Você pode usar esse método com todos os tipos de elemento, incluindo conectores, relações, formas, diagramas e elementos de modelo. Você também pode substituir os métodos de outras classes geradas. Algumas classes geradas como o ToolboxHelper sempre são derivados de duplo.  
  
### <a name="custom-constructors"></a>Construtores personalizados  
 Você não pode substituir um construtor. Mesmo em classes derivadas de duplo, o construtor deve ser na classe derivada.  
  
 Se você desejar fornecer seu próprio construtor, você pode fazer isso definindo `Has Custom Constructor` para a classe de domínio na definição de DSL. Quando você clica em **transformar todos os modelos**, o código gerado não incluirá um construtor para essa classe. Ele inclui uma chamada para o construtor ausente. Isso faz com que um relatório de erros quando você compila a solução. Clique duas vezes para ver um comentário no código gerado que explica o que você deve fornecer o relatório de erros.  
  
 Escrever uma definição de classe parcial em um arquivo que está separado dos arquivos gerados e fornecer o construtor.  
  
### <a name="flagged-extension-points"></a>Pontos de extensão sinalizadas  
 Um ponto de extensão sinalizadas é um lugar na definição de DSL, onde você pode definir uma propriedade ou uma caixa de seleção para indicar que você fornecerá um método personalizado. Construtores personalizados são um exemplo. Outros exemplos incluem configuração de `Kind` de uma propriedade de domínio calculado ou armazenamento personalizado de configuração o **personalizado é** sinalizador em um construtor de conexão.  
  
 Em cada caso, quando você define o sinalizador e gerar novamente o código, um erro de compilação fará. Clique duas vezes o erro para ver um comentário que explica o que você precisa fornecer.  
  
### <a name="rules"></a>Regras  
 O Gerenciador de transações permite que você defina regras que executam antes do final de uma transação na qual designado Ocorreu um evento, como uma alteração em uma propriedade. Regras normalmente são usadas para manter synchronism entre os diferentes elementos no repositório. Por exemplo, as regras são usadas para certificar-se de que o diagrama exibe o estado atual do modelo.  
  
 As regras são definidas em uma base por classe, para que você não precisa ter código que registra a regra para cada objeto. Para obter mais informações, consulte [propagar alterações dentro do modelo de regras](../modeling/rules-propagate-changes-within-the-model.md).  
  
### <a name="store-events"></a>Eventos de armazenamento  
 O armazenamento de modelagem fornece um mecanismo de eventos que você pode usar para escutar para tipos específicos de alterações no armazenamento, incluindo a adição e exclusão de elementos, as alterações nos valores de propriedade e assim por diante. Os manipuladores de eventos são chamados após o fechamento da transação em que as alterações foram feitas. Normalmente, esses eventos são usados para atualizar recursos fora do repositório.  
  
### <a name="net-events"></a>Eventos .NET  
 Você pode assinar alguns eventos nas formas. Por exemplo, você pode ouvir por cliques do mouse em uma forma. Você precisa escrever código que assina o evento para cada objeto. Esse código pode ser escrito em uma substituição de InitializeInstanceResources().  
  
 Alguns eventos são gerados em ShapeFields, que são usados para desenhar decoradores em uma forma. Para obter um exemplo, consulte [como: interceptar um clique em uma forma ou um decorador](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).  
  
 Geralmente esses eventos não ocorrem dentro de uma transação. Se você quiser fazer alterações no repositório, você deve criar uma transação.
