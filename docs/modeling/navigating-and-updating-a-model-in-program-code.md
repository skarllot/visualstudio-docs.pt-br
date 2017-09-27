---
title: "Navegar e atualizar um modelo no código de programa | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
ms.assetid: 1427ae91-be8a-4ce7-85df-00038faa2cbb
caps.latest.revision: 26
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 40f3a1d56019a8bcab4a11ffaf3aa7d37b02d262
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="navigating-and-updating-a-model-in-program-code"></a>Navegando e atualizando um modelo no código do programa
Você pode escrever código para criar e excluir elementos de modelo, defina suas propriedades e criar e excluir links entre os elementos. Todas as alterações devem ser feitas em uma transação. Se os elementos são exibidos em um diagrama, o diagrama será "corrigido para cima" automaticamente no final da transação.  
  
## <a name="in-this-topic"></a>Neste tópico  
 [Uma definição de DSL de exemplo](#example)  
  
 [Navegando o modelo](#navigation)  
  
 [Acessando informações da classe](#metadata)  
  
 [Executar as alterações dentro de uma transação](#transaction)  
  
 [Criar elementos de modelo](#elements)  
  
 [Criação de Links de relação](#links)  
  
 [Excluindo elementos](#deleteelements)  
  
 [Excluir Links de relação](#deletelinks)  
  
 [Reordenar os Links de uma relação](#reorder)  
  
 [Bloqueios](#locks)  
  
 [Copiar e colar](#copy)  
  
 [Navegar e diagramas de atualização](#diagrams)  
  
 [Navegando entre elementos e formas](#views)  
  
 [Propriedades de formas e conectores](#shapeProperties)  
  
 [DocView e DocData](#docdata)  
  
##  <a name="example"></a>Uma definição de DSL de exemplo  
 Esta é a parte principal do DslDefinition.dsl para os exemplos neste tópico:  
  
 ![Diagrama de definição de DSL &#45; modelo de árvore de família](../modeling/media/familyt_person.png "FamilyT_Person")  
  
 Esse modelo é uma instância desse DSL:  
  
 ![Modelo de árvore da família Tudor](../modeling/media/tudor_familytreemodel.png "Tudor_FamilyTreeModel")  
  
### <a name="references-and-namespaces"></a>Referências e Namespaces  
 Para executar o código neste tópico, você deve fazer referência a:  
  
 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`  
  
 Seu código usará esse namespace:  
  
 `using Microsoft.VisualStudio.Modeling;`  
  
 Além disso, se você estiver escrevendo o código em um projeto diferente no qual seu DSL é definido, você deve importar o assembly que é compilado pelo projeto Dsl.  
  
##  <a name="navigation"></a>Navegando o modelo  
  
### <a name="properties"></a>Propriedades  
 Propriedades de domínio que você define na definição de DSL tornam-se propriedades que você pode acessar no código do programa:  
  
 `Person henry = ...;`  
  
 `if (henry.BirthDate < 1500) ...`  
  
 `if (henry.Name.EndsWith("VIII")) ...`  
  
 Se você quiser definir uma propriedade, você deve fazer isso dentro de um [transação](#transaction):  
  
 `henry.Name = "Henry VIII";`  
  
 Se estiver na definição de DSL, uma propriedade **tipo** é **calculado**, você não pode defini-lo. Para obter mais informações, consulte [calculado e as propriedades de armazenamento personalizado](../modeling/calculated-and-custom-storage-properties.md).  
  
### <a name="relationships"></a>Relações  
 Relações de domínio que você define na definição de DSL se tornam pares de propriedades, uma classe em cada extremidade da relação. Os nomes das propriedades aparecem no diagrama DslDefinition como rótulos em funções em cada lado da relação. Dependendo da multiplicidade da função, o tipo da propriedade é a classe na outra extremidade da relação, ou uma coleção de classe.  
  
 `foreach (Person child in henry.Children) { ... }`  
  
 `FamilyTreeModel ftree = henry.FamilyTreeModel;`  
  
 As propriedades nas extremidades opostas de uma relação são sempre recíproco. Quando um link é criado ou excluído, as propriedades de função em ambos os elementos são atualizadas. A expressão a seguir (que usa as extensões de `System.Linq`) é sempre true para a relação de ParentsHaveChildren no exemplo:  
  
 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`  
  
 `&& p.Parents.All(parent => parent.Children.Contains(p));`  
  
 **ElementLinks**. Uma relação também é representada por um elemento de modelo chamado um *link*, que é uma instância do tipo de relação de domínio. Um link sempre tem elemento de uma origem e o elemento de um destino. O elemento de origem e o elemento de destino podem ser o mesmo.  
  
 Você pode acessar um link e suas propriedades:  
  
 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`  
  
 `// This is now true:`  
  
 `link == null || link.Parent == henry && link.Child == edward`  
  
 Por padrão, não mais de uma instância de uma relação é permitida para vincular qualquer par de elementos de modelo. Mas se na definição de DSL, o `Allow Duplicates` sinalizador é verdadeiro para a relação, em seguida, pode haver mais de um link e você deve usar `GetLinks`:  
  
 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`  
  
 Também há outros métodos para acessar links. Por exemplo:  
  
 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`  
  
 **Funções ocultas.** Se na definição de DSL, **é gerado de propriedade** é **false** para uma função específica, em seguida, nenhuma propriedade é gerada que corresponde a essa função. No entanto, você ainda pode acessar os links e percorrer os links usando os métodos da relação:  
  
 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`  
  
 O exemplo usado com mais frequência é o <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relação, o que vincula a um elemento de modelo para a forma que o exibe em um diagrama:  
  
 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`  
  
### <a name="the-element-directory"></a>O diretório do elemento  
 Você pode acessar todos os elementos no repositório usando o diretório do elemento:  
  
 `store.ElementDirectory.AllElements`  
  
 Também há métodos de localização de elementos, como o seguinte:  
  
 `store.ElementDirectory.FindElements(Person.DomainClassId);`  
  
 `store.ElementDirectory.GetElement(elementId);`  
  
##  <a name="metadata"></a>Acessando informações da classe  
 Você pode obter informações sobre as classes, relações e outros aspectos da definição de DSL. Por exemplo:  
  
 `DomainClassInfo personClass = henry.GetDomainClass();`  
  
 `DomainPropertyInfo birthProperty =`  
  
 `personClass.FindDomainProperty("BirthDate")`  
  
 `DomainRelationshipInfo relationship =`  
  
 `link.GetDomainRelationship();`  
  
 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`  
  
 As classes de ancestral de elementos de modelo são da seguinte maneira:  
  
-   ModelElement - todos os elementos e relações são encerrar outras  
  
-   ElementLink - todas as relações são ElementLinks  
  
##  <a name="transaction"></a>Executar as alterações dentro de uma transação  
 Sempre que o código de programa altera nada no repositório, ele deve fazer isso dentro de uma transação. Isso se aplica a todos os elementos de modelo, relações, formas, diagramas e suas propriedades. Para obter mais informações, consulte <xref:Microsoft.VisualStudio.Modeling.Transaction>.  
  
 É o método mais conveniente de gerenciar uma transação com um `using` instrução incluída em um `try...catch` instrução:  
  
```  
Store store; ...  
try  
{  
  using (Transaction transaction =  
    store.TransactionManager.BeginTransaction("update model"))  
    // Outermost transaction must always have a name.  
  {  
    // Make several changes in Store:  
    Person p = new Person(store);  
    p.FamilyTreeModel = familyTree;  
    p.Name = "Edward VI";  
    // end of changes to Store  
  
    transaction.Commit(); // Don't forget this!  
  } // transaction disposed here  
}  
catch (Exception ex)  
{  
  // If an exception occurs, the Store will be   
  // rolled back to its previous state.  
}  
```  
  
 Você pode tornar qualquer número de alterações dentro de uma transação. Você pode abrir novas transações dentro de uma transação ativa.  
  
 Para tornar as alterações permanentes, você deve `Commit` a transação antes de ser descartado. Se ocorrer uma exceção que não é capturado dentro da transação, o repositório será redefinido para seu estado antes das alterações.  
  
##  <a name="elements"></a>Criar elementos de modelo  
 Este exemplo adiciona um elemento a um modelo existente:  
  
```  
FamilyTreeModel familyTree = ...; // The root of the model.         
using (Transaction t =  
    familyTree.Store.TransactionManager  
    .BeginTransaction("update model"))  
{  
  // Create a new model element   
  // in the same partition as the model root:  
  Person edward = new Person(familyTree.Partition);  
  // Set its embedding relationship:  
  edward.FamilyTreeModel = familyTree;  
          // same as: familyTree.People.Add(edward);  
  // Set its properties:  
  edward.Name = "Edward VII";  
  t.Commit(); // Don't forget this!  
}  
```  
  
 Este exemplo ilustra esses pontos essenciais sobre como criar um elemento:  
  
-   Crie o novo elemento em uma partição específica do repositório. Para elementos de modelo e relações, mas não formas, isso geralmente é a partição padrão.  
  
-   Tornar o destino de uma relação de incorporação. Em DslDefinition deste exemplo, cada pessoa deve ser o destino da relação FamilyTreeHasPeople incorporada. Para fazer isso, podemos pode definir a propriedade de função FamilyTreeModel do objeto Person ou adicionar a pessoa para a propriedade da função de pessoas do objeto FamilyTreeModel.  
  
-   Definir as propriedades de um novo elemento, especialmente a propriedade para o qual `IsName` é verdadeiro para o DslDefinition. Esse sinalizador marca a propriedade que serve para identificar o elemento exclusivamente dentro de seu proprietário. Nesse caso, a propriedade de nome tem esse sinalizador.  
  
-   A definição de DSL dessa DSL deve ter sido carregada no repositório. Se você estiver escrevendo uma extensão, como um comando de menu, isso geralmente será já true. Em outros casos, você pode explicitamente carregar o modelo para o armazenamento, ou usar <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus> para carregá-lo. Para obter mais informações, consulte [como: abrir um modelo de arquivo no código do programa](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
 Quando você cria um elemento dessa maneira, uma forma é criada automaticamente (se o DSL tem um diagrama). Ele aparece em um local atribuído automaticamente, com a forma padrão, cor e outros recursos. Se você quiser controlar onde e como a forma associada é exibida, consulte [criação de um elemento e sua forma](#merge).  
  
##  <a name="links"></a>Criação de Links de relação  
 Existem duas relações definidas no exemplo, a definição de DSL. Cada relação define uma *propriedade função* na classe em cada extremidade da relação.  
  
 Há três maneiras em que você pode criar uma instância de uma relação. Cada um desses três métodos tem o mesmo efeito:  
  
-   Defina a propriedade do player de função de origem. Por exemplo:  
  
    -   `familyTree.People.Add(edward);`  
  
    -   `edward.Parents.Add(henry);`  
  
-   Defina a propriedade de destino. Por exemplo:  
  
    -   `edward.familyTreeModel = familyTree;`  
  
         A multiplicidade desta função é `1..1`, portanto, podemos atribuir o valor.  
  
    -   `henry.Children.Add(edward);`  
  
         A multiplicidade desta função é `0..*`, portanto, podemos adicionar à coleção.  
  
-   Construa uma instância da relação explicitamente. Por exemplo:  
  
    -   `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`  
  
    -   `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`  
  
 O último método é útil se você deseja definir propriedades na relação em si.  
  
 Quando você cria um elemento dessa maneira, um conector no diagrama é criado automaticamente, mas ele tem uma forma padrão, cor e outros recursos. Para controlar como o conector associado é criado, consulte [criação de um elemento e sua forma](#merge).  
  
##  <a name="deleteelements"></a>Excluindo elementos  
 Excluir um elemento chamando `Delete()`:  
  
 `henry.Delete();`  
  
 Essa operação também serão excluídos:  
  
-   Links de relação de e para o elemento. Por exemplo, `edward.Parents` não terá mais `henry`.  
  
-   Elementos em funções para o qual o `PropagatesDelete` sinalizador é true. Por exemplo, de forma que exibe o elemento será excluída.  
  
 Por padrão, cada relação incorporada tem `PropagatesDelete` true na função de destino. Excluindo `henry` não exclui o `familyTree`, mas `familyTree.Delete()` excluirá todos os `Persons`. Para obter mais informações, consulte [personalizar o comportamento de exclusão](../modeling/customizing-deletion-behavior.md).  
  
 Por padrão, `PropagatesDelete` não é verdadeiro para as funções de relações de referência.  
  
 Você pode fazer com que as regras de exclusão omitir propagações específicas quando você exclui um objeto. Isso é útil se você estiver substituindo um elemento para outro. Você fornecer o GUID de uma ou mais funções para as quais não deveriam ser propagada exclusão. O GUID pode ser obtido da classe de relação:  
  
 `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`  
  
 (Esse exemplo específico deve ter nenhum efeito, porque `PropagatesDelete` é `false` para as funções do `ParentsHaveChildren` relação.)  
  
 Em alguns casos, a exclusão é impedida pela existência de um bloqueio no elemento ou em um elemento que seria excluído pelo propagação. Você pode usar `element.CanDelete()` para verificar se o elemento pode ser excluído.  
  
##  <a name="deletelinks"></a>Excluir Links de relação  
 Você pode excluir um link de relação, removendo um elemento de uma propriedade de função:  
  
 `henry.Children.Remove(edward); // or:`  
  
 `edward.Parents.Remove(henry);  // or:`  
  
 Você também pode excluir o link explicitamente:  
  
 `edwardHenryLink.Delete();`  
  
 Todos estes três métodos têm o mesmo efeito. Você somente precisa usar um deles.  
  
 Se a função tiver multiplicidade entre 0 e 1 ou 1..1, você pode configurá-lo `null`, ou para outro valor:  
  
 `edward.FamilyTreeModel = null;`ou:  
  
 `edward.FamilyTreeModel = anotherFamilyTree;`  
  
##  <a name="reorder"></a>Ordenação novamente os Links de uma relação  
 Os links de uma relação específica que são originados ou direcionado a um elemento de modelo específico têm uma sequência específica. Eles aparecem na ordem na qual eles foram adicionados. Por exemplo, essa instrução sempre produzirá os filhos na mesma ordem:  
  
 `foreach (Person child in henry.Children) ...`  
  
 Você pode alterar a ordem dos links:  
  
 `ParentsHaveChildren link = GetLink(henry,edward);`  
  
 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`  
  
 `DomainRoleInfo role =`  
  
 `link.GetDomainRelationship().DomainRoles[0];`  
  
 `link.MoveBefore(role, nextLink);`  
  
##  <a name="locks"></a>Bloqueios  
 As alterações podem ser evitadas, um bloqueio. Bloqueios podem ser definidos em elementos individuais, partições e o armazenamento. Se qualquer um desses níveis tem um bloqueio que impede que o tipo de alteração que você deseja fazer, uma exceção pode ser gerada quando você tenta a ele. Você pode descobrir se os bloqueios são definidos usando o elemento. GetLocks(), que é um método de extensão que é definido no namespace <xref:Microsoft.VisualStudio.Modeling.Immutability>.  
  
 Para obter mais informações, consulte [definindo uma política de bloqueio para criar segmentos de somente leitura](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).  
  
##  <a name="copy"></a>Copiar e colar  
 Você pode copiar elementos ou grupos de elementos em um <xref:System.Windows.Forms.IDataObject>:  
  
```  
Person person = personShape.ModelElement as Person;  
Person adopter = adopterShape.ModelElement as Person;  
IDataObject data = new DataObject();  
personShape.Diagram.ElementOperations  
      .Copy(data, person.Children.ToList<ModelElement>());  
```  
  
 Os elementos são armazenados como um grupo de elementos serializado.  
  
 É possível mesclar elementos de um IDataObject em um modelo:  
  
```  
using (Transaction t = targetDiagram.Store.  
        TransactionManager.BeginTransaction("paste"))  
{  
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);  
}  
```  
  
 `Merge ()`pode aceitar um um `PresentationElement` ou `ModelElement`. Se você atribuir um `PresentationElement`, você também pode especificar uma posição no diagrama de destino como um terceiro parâmetro.  
  
##  <a name="diagrams"></a>Navegar e diagramas de atualização  
 Em uma DSL, o elemento de modelo de domínio, que representa um conceito como pessoa ou música, é separado do elemento de forma que representa o que você vê no diagrama. O elemento de modelo de domínio armazena as propriedades importantes e as relações dos conceitos. O elemento de forma armazena o tamanho, a posição e a cor do modo de exibição do objeto no diagrama e o layout de seus componentes.  
  
### <a name="presentation-elements"></a>Elementos de apresentação  
 ![Diagrama de classe de tipos base de forma e o elemento](../modeling/media/dslshapesandelements.png "DSLshapesAndElements")  
  
 Em sua definição de DSL, cada elemento que você especificar cria uma classe derivada de uma das seguintes classes padrão.  
  
|Tipo de elemento|Classe base|  
|---------------------|----------------|  
|Classe de domínio|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|  
|Relacionamento de domínio|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|  
|Forma|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|  
|Conector|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|  
|Diagrama|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|  
  
 Normalmente, um elemento em um diagrama representa um elemento de modelo. Normalmente (mas nem sempre), um <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> representa uma instância da classe de domínio e um <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> representa uma instância de relação de domínio. O <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relação vincula uma forma de nó ou link para o elemento de modelo que ele representa.  
  
 Todas as formas de nó ou link pertence a um diagrama. Uma forma de link binário se conecta a duas formas de nó.  
  
 Formas podem ter formas filho em dois conjuntos. Uma forma de `NestedChildShapes` conjunto é limitado da caixa delimitadora de seu pai. Uma forma de `RelativeChildShapes` lista pode aparecer fora ou parcialmente fora dos limites do pai - por exemplo, um rótulo ou uma porta. Um diagrama não tem nenhum `RelativeChildShapes` e não `Parent`.  
  
###  <a name="views"></a>Navegando entre elementos e formas  
 Elementos de modelo de domínio e elementos de forma são relacionados pelo <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relação.  
  
```csharp  
// using Microsoft.VisualStudio.Modeling;  
// using Microsoft.VisualStudio.Modeling.Diagrams;  
// using System.Linq;  
Person henry = ...;  
PersonShape henryShape =   
  PresentationViewsSubject.GetPresentation(henry)  
    .FirstOrDefault() as PersonShape;  
```  
  
 A mesma relação vincula relações conectores no diagrama:  
  
```  
Descendants link = Descendants.GetLink(henry, edward);  
DescendantConnector dc =  
   PresentationViewsSubject.GetPresentation(link)  
     .FirstOrDefault() as DescendantConnector;  
// dc.FromShape == henryShape && dc.ToShape == edwardShape  
```  
  
 Essa relação também vincula a raiz do modelo para o diagrama:  
  
```  
FamilyTreeDiagram diagram =   
   PresentationViewsSubject.GetPresentation(familyTree)  
      .FirstOrDefault() as FamilyTreeDiagram;  
```  
  
 Para obter o elemento do modelo representado por uma forma, use:  
  
 `henryShape.ModelElement as Person`  
  
 `diagram.ModelElement as FamilyTreeModel`  
  
### <a name="navigating-around-the-diagram"></a>Navegar em torno do diagrama  
 Em geral não é aconselhável para navegar entre as formas e conectores no diagrama. É melhor navegar pelas relações no modelo, movendo entre as formas e conectores somente quando é necessário trabalhar na aparência do diagrama. Esses métodos link conectores para as formas em cada extremidade:  
  
 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`  
  
 `connector.FromShape, connector.ToShape`  
  
 Muitas formas são compostos; elas são compostas de uma forma pai e uma ou mais camadas de filhos. Formas que são posicionadas em relação à outra forma são consideradas seu *filhos*. Quando a forma pai é movido, os filhos são movidas com ela.  
  
 *Filhos relativos* pode aparecer fora da caixa delimitadora da forma pai. *Aninhados* filhos estritamente aparecerem dentro dos limites do pai.  
  
 Para obter o conjunto superior de formas em um diagrama, use:  
  
 `Diagram.NestedChildShapes`  
  
 As classes de ancestral de formas e conectores são:  
  
 <xref:Microsoft.VisualStudio.Modeling.ModelElement>  
  
 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>  
  
 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>  
  
 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>  
  
 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>  
  
 ------- *YourShape*  
  
 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>  
  
 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>  
  
 --------- *YourConnector*  
  
###  <a name="shapeProperties"></a>Propriedades de formas e conectores  
 Na maioria dos casos, não é necessário fazer alterações explícitas de formas. Quando você tiver alterado os elementos de modelo, as regras de "corrigir" atualizam as formas e conectores. Para obter mais informações, consulte [respondendo a e propagando alterações](../modeling/responding-to-and-propagating-changes.md).  
  
 No entanto, é útil fazer algumas alterações explícitas para formas de propriedades que são independentes dos elementos de modelo. Por exemplo, você pode alterar essas propriedades:  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A>-Determina a altura e largura da forma.  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A>-posição relativa ao diagrama ou de forma pai  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A>-o conjunto de canetas e pincéis usadas para desenhar a forma ou o conector  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A>-faz com que a forma invisível  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A>-torna a forma visível após um`Hide()`  
  
###  <a name="merge"></a>Criação de um elemento e forma  
 Quando você cria um elemento e vinculá-lo na árvore de relações de inserção, uma forma é automaticamente criada e associada a ele. Isso é feito pelas regras de "ajuste" executem no final da transação. No entanto, a forma aparecerá em um local atribuído automaticamente e sua forma, cor e outros recursos terão valores padrão. Para controlar como a forma é criada, você pode usar a função de mesclagem. Você deve primeiro adicionar os elementos que você deseja adicionar um ElementGroup e, em seguida, mesclar o grupo no diagrama.  
  
 Este método:  
  
-   Define o nome, se você tiver atribuído a uma propriedade como o nome do elemento.  
  
-   Observa a qualquer elemento de mesclagem diretivas que você especificou na definição de DSL.  
  
 Este exemplo cria uma forma na posição do mouse, quando o usuário clica duas vezes no diagrama. Na definição de DSL para este exemplo, o `FillColor` propriedade `ExampleShape` foi exposto.  
  
```  
  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
partial class MyDiagram  
{  
  public override void OnDoubleClick(DiagramPointEventArgs e)  
  {  
    base.OnDoubleClick(e);  
  
    using (Transaction t = this.Store.TransactionManager  
        .BeginTransaction("double click"))  
    {  
      ExampleElement element = new ExampleElement(this.Store);  
      ElementGroup group = new ElementGroup(element);  
  
      { // To use a shape of a default size and color, omit this block.  
        ExampleShape shape = new ExampleShape(this.Partition);  
        shape.ModelElement = element;  
        shape.AbsoluteBounds = new RectangleD(0, 0, 1.5, 1.0);  
        shape.FillColor = System.Drawing.Color.Azure;  
        group.Add(shape);  
      }  
  
      this.ElementOperations.MergeElementGroupPrototype(  
        this,  
        group.CreatePrototype(),  
        PointD.ToPointF(e.MousePosition));  
      t.Commit();  
    }  
  }  
}  
  
```  
  
 Se você fornecer mais de uma forma, defina suas posições relativas usando o `AbsoluteBounds`.  
  
 Você também pode definir a cor e outras propriedades expostas conectores usando esse método.  
  
### <a name="use-transactions"></a>Usar transações  
 Formas, conectores e diagramas são subtipos do <xref:Microsoft.VisualStudio.Modeling.ModelElement> e ao vivo no repositório. Portanto, você deve fazer alterações a eles somente dentro de uma transação. Para obter mais informações, consulte [como: usar transações para atualizar o modelo](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
##  <a name="docdata"></a>Exibição de documentos e dados de documento  
 ![Diagrama de classe dos tipos de diagrama padrão](../modeling/media/dsldiagramsanddocs.png "DSLDiagramsandDocs")  
  
## <a name="store-partitions"></a>Armazenar partições  
 Quando um modelo é carregado, o diagrama a seguir é carregado ao mesmo tempo. Normalmente, o modelo é carregado no Store.DefaultPartition, e o conteúdo de diagrama é carregado em outra partição. Geralmente, o conteúdo de cada partição é carregado e salvas em um arquivo separado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Modeling.ModelElement>   
 [Validação em uma linguagem específica do domínio](../modeling/validation-in-a-domain-specific-language.md)   
 [Gerando o código de uma linguagem específica de domínio](../modeling/generating-code-from-a-domain-specific-language.md)   
 [Como: usar transações para atualizar o modelo](../modeling/how-to-use-transactions-to-update-the-model.md)   
 [Integração de modelos usando o Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Respondendo a alterações e propagando-as](../modeling/responding-to-and-propagating-changes.md)

