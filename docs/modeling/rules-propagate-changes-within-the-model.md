---
title: "Regras propagam alterações dentro do modelo | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
ms.assetid: 1690a38a-c8f5-4bc6-aab9-015771ec6647
caps.latest.revision: 30
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e503405dbd2cfc5dfa39ad9f03ec67cbfe31abae
ms.lasthandoff: 02/22/2017

---
# <a name="rules-propagate-changes-within-the-model"></a>Regras propagam alterações dentro do modelo
Você pode criar uma regra do repositório para propagar uma alteração de um elemento para outro na visualização e o SDK de modelagem (VMSDK). Quando ocorre uma alteração a qualquer elemento no repositório de regras são programadas para ser executado, geralmente quando a transação externa for confirmada. Existem diferentes tipos de regras para diferentes tipos de eventos, como adicionar um elemento ou excluí-lo. Você pode anexar regras a tipos específicos de elementos, formas ou diagramas. Muitos recursos internos são definidos pelas regras: por exemplo, regras de garantem que um diagrama é atualizado quando o modelo for alterado. Você pode personalizar sua linguagem específica do domínio, adicionando suas próprias regras.  
  
 Repositório de regras são particularmente úteis para propagar alterações dentro do armazenamento – ou seja, é alterado para elementos de modelo, relações, formas ou conectores e seu domínio propriedades. As regras não são executados quando o usuário invoca os comandos de desfazer ou refazer. Em vez disso, o Gerenciador de transações garante que o repositório de conteúdo é restaurado para o estado correto. Se você deseja propagar alterações aos recursos fora do repositório, use armazenar eventos. Para obter mais informações, consulte [manipuladores de propagar alterações fora do modelo de evento](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
 Por exemplo, suponha que você deseja especificar que, sempre que o usuário (ou seu código) cria um novo elemento de tipo ExampleDomainClass, um elemento adicional de outro tipo é criado em outra parte do modelo. Você poderia escrever um AddRule e associá-lo a ExampleDomainClass. Você deve escrever o código na regra para criar o elemento adicional.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
  
namespace ExampleNamespace  
{  
 // Attribute associates the rule with a domain class:  
 [RuleOn(typeof(ExampleDomainClass), FireTime=TimeToFire.TopLevelCommit)]  
 // The rule is a class derived from one of the abstract rules:  
 class MyAddRule : AddRule  
 {  
  // Override the abstract method:  
  public override void ElementAdded(ElementAddedEventArgs e)  
  {  
    base.ElementAdded(e);  
    ExampleDomainClass element = e.ModelElement;  
    Store store = element.Store;  
    // Ignore this call if we're currently loading a model:  
    if (store.TransactionManager.CurrentTransaction.IsSerializing)   
       return;  
  
    // Code here propagates change as required – for example:  
      AnotherDomainClass echo = new AnotherDomainClass(element.Partition);  
      echo.Name = element.Name;  
      echo.Parent = element.Parent;    
    }  
  }  
 // The rule must be registered:  
 public partial class ExampleDomainModel  
 {  
   protected override Type[] GetCustomDomainModelTypes()  
   {  
     List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
     types.Add(typeof(MyAddRule));  
     // If you add more rules, list them here.   
     return types.ToArray();  
   }  
 }  
}  
  
```  
  
> [!NOTE]
>  O código de uma regra deve alterar o estado somente de elementos dentro do armazenamento; ou seja, a regra deve alterar apenas elementos de modelo, relações, formas, conectores, diagramas ou suas propriedades. Se você deseja propagar alterações aos recursos fora do repositório, defina armazenar eventos. Para obter mais informações, consulte [manipuladores de propagar alterações fora do modelo de evento](../modeling/event-handlers-propagate-changes-outside-the-model.md)  
  
### <a name="to-define-a-rule"></a>Para definir uma regra  
  
1.  Definir a regra como uma classe prefixado com o `RuleOn` atributo. O atributo associa a regra com uma de suas classes de domínio, relações ou elementos de diagrama. A regra será aplicada a cada instância desta classe, que pode ser abstrato.  
  
2.  Registrar a regra adicionando-o para o conjunto retornado por `GetCustomDomainModelTypes()` em sua classe de modelo de domínio.  
  
3.  Derive a classe de regra de uma das classes de regras de abstrata e escreva o código do método de execução.  
  
 As seções a seguir descrevem essas etapas mais detalhadamente.  
  
### <a name="to-define-a-rule-on-a-domain-class"></a>Para definir uma regra em uma classe de domínio  
  
-   Em um arquivo de código personalizado, defina uma classe e um prefixo com o <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute>atributo:</xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute>  
  
    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value – but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  
  
    ```  
  
-   O tipo de entidade no primeiro parâmetro pode ser uma classe de domínio, relação de domínio, forma, conector ou diagrama. Normalmente, você aplica regras a relações e classes de domínio.  
  
     O `FireTime` geralmente é `TopLevelCommit`. Isso garante que a regra é executada somente depois que todas as alterações principais da transação foram feitas. As alternativas são embutidas, que executa a regra logo após a alteração; e LocalCommit, que executa a regra ao final da transação atual (que pode não ser mais externo). Você também pode definir a prioridade de uma regra para afetar seus pedidos na fila, mas esse é um método confiável de atingir o resultado que necessário.  
  
-   Você pode especificar uma classe abstrata, como o tipo de entidade.  
  
-   A regra se aplica a todas as instâncias da classe de entidade.  
  
-   O valor padrão para `FireTime` é TimeToFire.TopLevelCommit. Isso faz com que a regra a ser executado quando a transação externa for confirmada. Uma alternativa é TimeToFire.Inline. Isso faz com que a regra seja executada logo após o evento de disparo.  
  
### <a name="to-register-the-rule"></a>Para registrar a regra  
  
-   Adicione a classe de regra à lista de tipos retornados pela `GetCustomDomainModelTypes` em seu modelo de domínio:  
  
    ```  
    public partial class ExampleDomainModel  
     {  
       protected override Type[] GetCustomDomainModelTypes()  
       {  
         List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
         types.Add(typeof(MyAddRule));  
         // If you add more rules, list them here.   
         return types.ToArray();  
       }  
     }  
  
    ```  
  
-   Se você não tiver certeza do nome da sua classe de modelo de domínio, examinar o arquivo **Dsl\GeneratedCode\DomainModel.cs**  
  
-   Escreva esse código em um arquivo de código personalizado em seu projeto DSL.  
  
### <a name="to-write-the-code-of-the-rule"></a>Escrever o código da regra  
  
-   Derive a classe de regra de uma das seguintes classes base:  
  
    |Classe base|Disparador|  
    |----------------|-------------|  
    |<xref:Microsoft.VisualStudio.Modeling.AddRule></xref:Microsoft.VisualStudio.Modeling.AddRule>|Um elemento, um link ou uma forma é adicionada.<br /><br /> Use isso para detectar novas relações, além de novos elementos.|  
    |<xref:Microsoft.VisualStudio.Modeling.ChangeRule></xref:Microsoft.VisualStudio.Modeling.ChangeRule>|Um valor de propriedade de domínio é alterado. O argumento do método fornece os valores antigo e novo.<br /><br /> Para formas, essa regra é acionada quando interna `AbsoluteBounds` alterações de propriedade, se a forma é movida.<br /><br /> Em muitos casos, é mais conveniente substituir `OnValueChanged` ou `OnValueChanging` no manipulador de propriedade. Esses métodos são chamados imediatamente antes e após a alteração. Por outro lado, a regra é executada normalmente no final da transação. Para obter mais informações, consulte [manipuladores de alteração de valor de propriedade de domínio](../modeling/domain-property-value-change-handlers.md). **Observação:** essa regra não é disparada quando um link é criado ou excluído. Em vez disso, escrever um `AddRule` e um `DeleteRule` para a relação de domínio.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeletingRule></xref:Microsoft.VisualStudio.Modeling.DeletingRule>|Acionado quando um elemento ou link está prestes a ser excluído. A propriedade ModelElement.IsDeleting é verdadeira até o final da transação.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeleteRule></xref:Microsoft.VisualStudio.Modeling.DeleteRule>|Executado quando um elemento ou um link foi excluído. A regra é executada depois que todas as regras foram executadas, incluindo DeletingRules. ModelElement.IsDeleting for false, e ModelElement.IsDeleted for true. Para permitir uma recuperação subsequente, o elemento não é realmente removido da memória, mas ele é removido do Store.ElementDirectory.|  
    |<xref:Microsoft.VisualStudio.Modeling.MoveRule></xref:Microsoft.VisualStudio.Modeling.MoveRule>|Um elemento é movido da partição de um repositório para outro.<br /><br /> (Observe que isso não está relacionado à posição de uma forma gráfica).|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule></xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>|Essa regra se aplica somente às relações de domínio. Se você atribuir explicitamente um elemento de modelo para qualquer uma das extremidades de um link é disparado.|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule></xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule>|Acionado quando a ordem dos links para ou de um elemento é alterada usando os métodos MoveBefore ou MoveToIndex em um link.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule></xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>|Executado quando uma transação é criada.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule></xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>|Executado quando a transação é confirmada.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule></xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>|Executado quando a transação é revertida.|  
  
-   Cada classe tem um método que você substituir. Tipo de `override` em sua classe para descobri-lo. O parâmetro desse método identifica o elemento que está sendo alterado.  
  
 Observe os seguintes pontos sobre regras:  
  
1.  O conjunto de alterações em uma transação pode disparar muitas regras. Geralmente, as regras são executadas quando a transação externa for confirmada. Eles são executados em uma ordem não especificada.  
  
2.  Uma regra é sempre executada dentro de uma transação. Portanto, você não precisa criar uma nova transação para fazer alterações.  
  
3.  As regras não são executadas quando uma transação é revertida, ou quando as operações de desfazer ou refazer são executadas. Essas operações Redefinir todo o conteúdo do repositório para seu estado anterior. Portanto, se sua regra altera o estado de qualquer arquivo fora do repositório, ele talvez não lembre synchronism com o armazenamento de conteúdo. Para atualizar o estado fora do repositório, é melhor usar eventos. Para obter mais informações, consulte [manipuladores de propagar alterações fora do modelo de evento](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
4.  Algumas regras são executadas quando um modelo é carregado do arquivo. Para determinar se carregar ou salvar está em andamento, use `store.TransactionManager.CurrentTransaction.IsSerializing`.  
  
5.  Se o código da sua regra cria mais gatilhos de regra, eles serão adicionados ao final da lista de acionamento e serão executados antes que a transação seja concluída. DeletedRules são executados depois que todas as outras regras. Uma regra pode executar várias vezes em uma transação, uma vez para cada alteração.  
  
6.  Para passar informações para e de regras, você pode armazenar informações de `TransactionContext`. Isso é apenas um dicionário que é mantido durante a transação. Ele é descartado quando a transação termina. Os argumentos do evento em cada regra fornecem acesso a ele. Lembre-se de que as regras não são executadas em uma ordem previsível.  
  
7.  Use as regras depois de considerar outras alternativas. Por exemplo, se você quiser atualizar uma propriedade quando um valor é alterado, considere usar uma propriedade calculada. Se você quiser restringir o tamanho ou o local de uma forma, use um `BoundsRule`. Se você quiser responder a uma alteração no valor de uma propriedade, adicione um `OnValueChanged` manipulador para a propriedade. Para obter mais informações, consulte [propagando alterações e responder a](../modeling/responding-to-and-propagating-changes.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir atualiza uma propriedade quando uma relação de domínio é instanciada para vincular dois elementos. A regra será acionada não apenas quando o usuário cria um link em um diagrama, mas também se o código do programa cria um link.  
  
 Para testar este exemplo, criar uma DSL usando o modelo de solução de fluxo de tarefa e insira o código a seguir em um arquivo no projeto Dsl. Criar e executar a solução e abra o arquivo de amostra no projeto de depuração. Desenhe um Link de comentário entre uma forma de comentário e um elemento de fluxo. Altera o texto do comentário ao relatório do elemento mais recente que você conectou para.  
  
 Na prática, você geralmente escreveria um DeleteRule para cada AddRule.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.VisualStudio.Modeling;  
  
namespace Company.TaskRuleExample  
{  
  
  [RuleOn(typeof(CommentReferencesSubjects))]  
  public class RoleRule : AddRule  
  {  
  
    public override void ElementAdded(ElementAddedEventArgs e)  
    {  
      base.ElementAdded(e);  
      CommentReferencesSubjects link = e.ModelElement as CommentReferencesSubjects;  
      Comment comment = link.Comment;  
      FlowElement subject = link.Subject;  
      Transaction current = link.Store.TransactionManager.CurrentTransaction;  
      // Don't want to run when we're just loading from file:  
      if (current.IsSerializing) return;  
      comment.Text = "Flow has " + subject.FlowTo.Count + " outgoing connections";  
    }  
  
  }  
  
  public partial class TaskRuleExampleDomainModel  
  {  
    protected override Type[] GetCustomDomainModelTypes()  
    {  
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
      types.Add(typeof(RoleRule));  
      return types.ToArray();  
    }  
  }  
  
}  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [Manipuladores de eventos propagam alterações fora do modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [BoundsRules restringem o local e o tamanho de uma forma](../modeling/boundsrules-constrain-shape-location-and-size.md)
