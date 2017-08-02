---
title: "Personalizando a criação de elemento e o movimento | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
ms.assetid: cbd28f15-dfd7-46bd-ab79-5430e3ed83c8
caps.latest.revision: 36
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8237c8df126fa09613b03d35c599af851522efb8
ms.lasthandoff: 02/22/2017

---
# <a name="customizing-element-creation-and-movement"></a>Personalizando a criação e o movimento de elementos
Você pode permitir que um elemento a ser arrastado para outra, da caixa de ferramentas ou em uma operação de colar ou a operação de movimentação. Você pode ter movidos elementos vinculados aos elementos de destino, usando os relacionamentos que você especificar.  
  
 Uma diretiva element merge (EMD) Especifica o que acontece quando um elemento de modelo *mesclada* em outro elemento de modelo. Isso acontece quando:  
  
-   O usuário arrasta da toolbox para o diagrama ou uma forma.  
  
-   O usuário cria um elemento usando um menu Adicionar no explorer ou uma forma do compartimento.  
  
-   O usuário move um item de uma raia para outra.  
  
-   O usuário cola um elemento.  
  
-   O código de programa chama a diretiva element merge.  
  
 Embora as operações de criação podem parecer diferente do que as operações de cópia, eles realmente funcionam da mesma maneira. Quando um elemento é adicionado, por exemplo da caixa de ferramentas, um protótipo dele é replicado. O protótipo é mesclado no modelo da mesma maneira como os elementos que foram copiados de uma outra parte do modelo.  
  
 A responsabilidade de uma EMD é decidir como um objeto ou grupo de objetos deve ser mesclado em um local específico no modelo. Em particular, ele decide quais relações devem ser instanciadas para vincular o grupo mesclado no modelo. Você também pode personalizá-lo para definir propriedades e criar objetos adicionais.  
  
 ![EMD_Merge DSL](~/docs/modeling/media/dsl-emd_merge.png "DSL-EMD_Merge")  
A função de uma diretiva Element Merge  
  
 Uma EMD é gerada automaticamente quando você define uma relação de incorporação. Esse padrão EMD cria uma instância da relação quando os usuários adicionam novas instâncias filho ao pai. Você pode modificar essas EMDs padrão, por exemplo, adicionando código personalizado.  
  
 Você também pode adicionar seus próprios EMDs na definição de DSL, para permitir aos usuários arrastar ou colar diferentes combinações de classes mescladas e de recebimento.  
  
## <a name="defining-an-element-merge-directive"></a>Definindo uma diretiva Element Merge  
 Você pode adicionar diretivas de mesclagem de elementos para classes de domínio, relações de domínio, formas, conectores e diagramas. Você pode adicionar ou encontrá-los no Gerenciador de DSL sob a classe receptora do domínio. A classe de recebimento é a classe de domínio do elemento que já está no modelo e, em que o elemento novo ou copiado será mesclado.  
  
 ![DSL EMD_Details](~/docs/modeling/media/dsl-emd_details.png "EMD_Details DSL")  
  
 O **classe indexação** é a classe de domínio de elementos que podem ser mescladas em membros da classe receptora. Instâncias das subclasses da classe indexação também serão mescladas por este EMD, a menos que você defina **aplica-se à subclasses** como False.  
  
 Há dois tipos de diretiva de mesclagem:  
  
-   A **processo de mesclagem** diretiva especifica as relações pelo qual o novo elemento deve ser vinculado à árvore.  
  
-   A **Forward mesclar** diretiva redireciona o novo elemento para outro elemento de recebimento, normalmente um pai.  
  
 Você pode adicionar código personalizado para diretivas de mesclagem:  
  
-   Definir **aceitação personalizada usa** para adicionar seu próprio código para determinar se uma determinada instância do elemento de indexação deve ser mesclada no elemento de destino. Quando o usuário arrasta da caixa de ferramentas, o ponteiro "inválido" mostra se seu código não permite a mesclagem.  
  
     Por exemplo, você poderia permitir a mesclagem apenas quando o elemento de recebimento estiver em um estado específico.  
  
-   Definir **mesclagem personalizada usa** adicionar fornecem o próprio código para definir as alterações feitas no modelo quando a mesclagem for executada.  
  
     Por exemplo, você pode definir propriedades no elemento mesclado usando dados de seu novo local no modelo.  
  
> [!NOTE]
>  Se você escrever código personalizado de mesclagem, ele afeta somente mesclagens que são executadas usando esse EMD. Se houver outros EMDs que mesclagem o mesmo tipo de objeto, ou se houver outros códigos personalizados que cria esses objetos sem usar o EMD, em seguida, eles não serão afetados pelo seu código personalizado de mesclagem.  
>   
>  Se você desejar certificar-se de que um novo elemento ou nova relação sempre é processada por seu código personalizado, considere a definição de um `AddRule` na relação de incorporação e um `DeleteRule` na classe de domínio do elemento. Para obter mais informações, consulte [propagar alterações dentro do modelo de regras](../modeling/rules-propagate-changes-within-the-model.md).  
  
## <a name="example-defining-an-emd-without-custom-code"></a>Exemplo: Definindo uma EMD sem código personalizado  
 O exemplo a seguir permite aos usuários criar um elemento e um conector ao mesmo tempo, arrastando da toolbox para uma forma existente. O exemplo adiciona uma EMD à definição de DSL. Antes dessa modificação, os usuários poderão arrastar ferramentas no diagrama, mas não em formas existentes.  
  
 Os usuários também podem colar elementos em outros elementos.  
  
#### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Para permitir aos usuários criar um elemento e um conector ao mesmo tempo  
  
1.  Criar uma nova DSL usando o **linguagem mínima** modelo de solução.  
  
     Quando você executar essa DSL, ela permite criar formas e conectores entre as formas. Você não pode arrastar um novo **ExampleElement** forma Toolbox para uma forma existente.  
  
2.  Para permitir que os usuários mesclar elementos em `ExampleElement` formas, crie um novo EMD na `ExampleElement` classe de domínio:  
  
    1.  Em **Gerenciador de DSL**, expanda **Classes de domínio**. Clique com botão direito `ExampleElement` e, em seguida, clique em **adicionar nova diretiva Element Merge**.  
  
    2.  Verifique se o **detalhes de DSL** janela é aberta, para que você pode ver os detalhes do novo EMD. (Menu: **exibição**, **outras janelas**, **detalhes de DSL**.)  
  
3.  Definir o **indexação classe** na janela de detalhes de DSL, para definir a classe de elementos pode ser mesclado com `ExampleElement` objetos.  
  
     Neste exemplo, selecione `ExampleElements`, de modo que o usuário pode arrastar novos elementos para elementos existentes.  
  
     Observe que a classe de indexação se torna o nome de EMD no Gerenciador de DSL.  
  
4.  Em **direta do processo criando links**, adicionar dois caminhos:  
  
    1.  Um caminho vincula o novo elemento para o modelo pai. A expressão de caminho que você precisa inserir navega de elemento existente, backup por meio da relação de incorporação para o modelo pai. Por fim, ele especifica a função no novo link para o qual o novo elemento será atribuído. O caminho é o seguinte:  
  
         `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`  
  
    2.  Outro caminho vincula o novo elemento para o elemento existente. A expressão de caminho Especifica a relação de referência e a função à qual o novo elemento será atribuído. Esse caminho é o seguinte:  
  
         `ExampleElementReferencesTargets.Sources`  
  
     Você pode usar a ferramenta de navegação do caminho para criar cada caminho:  
  
    1.  Em **direta do processo criando links nos caminhos**, clique em ** \<Adicionar caminho >**.  
  
    2.  Clique na seta suspensa à direita do item de lista. Uma exibição de árvore é exibida.  
  
    3.  Expanda os nós na árvore para formar o caminho que você deseja especificar.  
  
5.  Teste o DSL:  
  
    1.  Pressione F5 para recompilar e executar a solução.  
  
         Recriando levará mais tempo porque o código gerado será atualizado a partir de modelos de texto de acordo com a nova definição de DSL.  
  
    2.  Quando a instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] foi iniciado, abra um arquivo de modelo de DSL. Crie alguns elementos de exemplo.  
  
    3.  Arraste a partir de **elemento de exemplo** ferramenta em uma forma existente.  
  
         Uma nova forma aparece e é vinculado à forma existente com um conector.  
  
    4.  Copie uma forma existente. Selecione outra forma e cole.  
  
         Uma cópia da primeira forma é criada.  Ele tem um novo nome e ele está vinculado a segunda forma com um conector.  
  
 Observe os seguintes pontos neste procedimento:  
  
-   Criando diretivas de mescla de elemento, você pode permitir que qualquer classe de elemento para aceitar qualquer um dos outros. O EMD é criado na classe do receptor do domínio, e a classe de domínio aceito é especificada no **classe Index** campo.  
  
-   Ao definir caminhos, você pode especificar quais links devem ser usadas para conectar o novo elemento ao modelo existente.  
  
     Os links que você especificar deve incluir uma relação de incorporação.  
  
-   O EMD afeta a criação da caixa de ferramentas e também operações de colagem.  
  
     Se você escrever código personalizado que cria novos elementos, você pode chamar explicitamente o EMD usando o `ElementOperations.Merge` método. Isso garante que seu código vincula novos elementos no modelo da mesma maneira como outras operações. Para obter mais informações, consulte [personalizar comportamento de cópia](../modeling/customizing-copy-behavior.md).  
  
## <a name="example-adding-custom-accept-code-to-an-emd"></a>Exemplo: Adicionar código aceitação personalizada para uma EMD  
 Adicionando código personalizado para uma EMD, você pode definir o comportamento de junção mais complexo. Esse exemplo simples impede que o usuário adicionando mais de um número fixo de elementos no diagrama. O exemplo modifica o padrão EMD que acompanha uma relação de incorporação.  
  
#### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Escrever código personalizado aceitar para restringir o que o usuário pode adicionar  
  
1.  Criar uma DSL usando o **linguagem mínima** modelo de solução. Abra o diagrama de definição de DSL.  
  
2.  No Gerenciador de DSL, expanda **Classes de domínio**, `ExampleModel`, **diretivas de mescla de elemento**. Selecione a diretiva de mesclagem do elemento denominado `ExampleElement`.  
  
     Este EMD controla como o usuário pode criar novos `ExampleElement` objetos no modelo, por exemplo, arrastando da caixa de ferramentas.  
  
3.  No **detalhes de DSL** janela, selecione **aceitação personalizada usa**.  
  
4.  Recompile a solução. Isso levará mais tempo porque o código gerado será atualizado a partir do modelo.  
  
     Um erro de compilação será relatado, semelhante a: "Company.ElementMergeSample.ExampleElement não contém uma definição para CanMergeExampleElement..."  
  
     Você deve implementar o método `CanMergeExampleElement`.  
  
5.  Criar um novo arquivo de código no **Dsl** projeto. Substitua seu conteúdo pelo seguinte código e altere o namespace para o namespace do seu projeto.  
  
    ```c#  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace Company.ElementMergeSample // EDIT.  
    {  
      partial class ExampleModel  
      {  
        /// <summary>  
        /// Called whenever an ExampleElement is to be merged into this ExampleModel.  
        /// This happens when the user pastes an ExampleElement  
        /// or drags from the toolbox.  
        /// Determines whether the merge is allowed.  
        /// </summary>  
        /// <param name="rootElement">The root element in the merging EGP.</param>  
        /// <param name="elementGroupPrototype">The EGP that the user wants to merge.</param>  
        /// <returns>True if the merge is allowed</returns>  
        private bool CanMergeExampleElement(ProtoElementBase rootElement, ElementGroupPrototype elementGroupPrototype)  
        {  
          // Allow no more than 4 elements to be added:  
          return this.Elements.Count < 4;  
        }  
      }  
    }  
  
    ```  
  
     Esse exemplo simples restringe o número de elementos que podem ser mescladas no modelo pai. Condições mais interessantes, o método pode inspecionar qualquer uma das propriedades e links do objeto receptor. Ele também pode inspecionar as propriedades dos elementos de mesclagem, que são executadas em <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>.</xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> Para obter mais informações sobre `ElementGroupPrototypes`, consulte [personalizar comportamento de cópia](../modeling/customizing-copy-behavior.md). Para obter mais informações sobre como escrever código que lê um modelo, consulte [Navegando e atualizando um modelo no código do programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
6.  Teste o DSL:  
  
    1.  Pressione F5 para recompilar a solução. Quando a instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é aberta, abra uma instância de sua DSL.  
  
    2.  Crie novos elementos de várias maneiras:  
  
        1.  Arraste do **elemento de exemplo** ferramenta para o diagrama.  
  
        2.  No **Gerenciador de modelos de exemplo**, com o botão direito no nó raiz e, em seguida, clique em **adicionar novo elemento de exemplo**.  
  
        3.  Copie e cole um elemento no diagrama.  
  
    3.  Verifique se que você não pode usar qualquer um destes procedimentos para adicionar mais de quatro elementos ao modelo. Isso ocorre porque todas elas usam a diretiva Element Merge.  
  
## <a name="example-adding-custom-merge-code-to-an-emd"></a>Exemplo: Adicionar código personalizado de mesclagem para uma EMD  
 No código de mesclagem personalizado, você pode definir o que acontece quando o usuário arrasta uma ferramenta ou cola em um elemento. Há duas maneiras de definir uma mesclagem personalizada:  
  
1.  Definir **usa personalizadas mesclar** e forneça o código necessário. O código substitui o código gerado de mesclagem. Use esta opção se você quiser redefinir completamente o que faz a mesclagem.  
  
2.  Substituir o `MergeRelate` método e, opcionalmente, o `MergeDisconnect` método. Para fazer isso, você deve definir o **gera derivado duplo** propriedade da classe de domínio. Seu código pode chamar o código de mesclagem gerado na classe base. Use esta opção se você quiser executar operações adicionais após a mesclagem foi executada.  
  
 Essas abordagens afetam apenas as mesclagens que são executadas usando esse EMD. Se você deseja afetar todas as maneiras em que o elemento mesclado pode ser criado, uma alternativa é definir um `AddRule` na relação de incorporação e um `DeleteRule` na classe de domínio mesclada. Para obter mais informações, consulte [propagar alterações dentro do modelo de regras](../modeling/rules-propagate-changes-within-the-model.md).  
  
#### <a name="to-override-mergerelate"></a>Substituir MergeRelate  
  
1.  Na definição de DSL, certifique-se de que você tenha definido o EMD ao qual você deseja adicionar o código. Se desejar, você pode adicionar caminhos e definir personalizado aceitar código conforme descrito nas seções anteriores.  
  
2.  No diagrama DslDefinition, selecione a classe receptora da mesclagem. Geralmente, é a classe na extremidade de origem de uma relação de incorporação.  
  
     Por exemplo, em uma DSL gerada a partir da solução de linguagem mínima, selecione `ExampleModel`.  
  
3.  No **propriedades** janela, defina **gera derivado duplo** para **true**.  
  
4.  Recompile a solução.  
  
5.  Inspecionar o conteúdo do **Dsl\Generated Files\DomainClasses.cs**. Procure métodos chamados `MergeRelate` e examine seu conteúdo. Isso ajudará você a escrever suas próprias versões.  
  
6.  Em um novo arquivo de código, escrever uma classe parcial para a classe de recebimento e substituir o `MergeRelate` método. Lembre-se de chamar o método base. Por exemplo:  
  
    ```c#  
    partial class ExampleModel  
    {  
      /// <summary>  
      /// Called when the user drags or pastes an ExampleElement onto the diagram.  
      /// Sets the time of day as the name.  
      /// </summary>  
      /// <param name="sourceElement">Element to be added</param>  
      /// <param name="elementGroup">Elements to be merged</param>  
      protected override void MergeRelate(ModelElement sourceElement, ElementGroup elementGroup)  
      {  
        // Connect the element according to the EMD:  
        base.MergeRelate(sourceElement, elementGroup);  
  
        // Custom actions:   
        ExampleElement mergingElement = sourceElement as ExampleElement;  
        if (mergingElement != null)  
        {  
          mergingElement.Name = DateTime.Now.ToLongTimeString();  
        }  
      }  
    }  
  
    ```  
  
#### <a name="to-write-custom-merge-code"></a>Escrever código personalizado de mesclagem  
  
1.  Em **Dsl\Generated Code\DomainClasses.cs**, inspecionar métodos chamados `MergeRelate`. Esses métodos criam links entre um novo elemento e o modelo existente.  
  
     Além disso, inspecionar métodos chamados `MergeDisconnect`. Esses métodos desvincular um elemento do modelo quando ele deve ser excluído.  
  
2.  Em **Gerenciador de DSL**, selecione ou crie a diretiva Element Merge que você deseja personalizar. No **detalhes de DSL** janela, defina **usa personalizadas mesclar**.  
  
     Quando você definir essa opção, o **processo de mesclagem** e **Forward mesclar** opções serão ignoradas. Seu código será usado.  
  
3.  Recompile a solução. Levará mais tempo porque os arquivos de código gerado serão atualizados a partir do modelo.  
  
     Mensagens de erro serão exibida. Clique duas vezes as mensagens de erro para ver as instruções no código gerado. Essas instruções pedirá que você fornecer dois métodos, `MergeRelate` *YourDomainClass* e `MergeDisconnect` *YourDomainClass*  
  
4.  Grave os métodos em uma definição de classe parcial em um arquivo separado código. Os exemplos que você inspecionou anteriormente devem sugerir que você precisa.  
  
 Código de mesclagem personalizado não afetará o código que cria objetos e relações diretamente e não afetará outros EMDs. Para certificar-se de que as alterações adicionais são implementadas, independentemente de como o elemento é criado, considere escrever um `AddRule` e um `DeleteRule` em vez disso. Para obter mais informações, consulte [propagar alterações dentro do modelo de regras](../modeling/rules-propagate-changes-within-the-model.md).  
  
## <a name="redirecting-a-merge-operation"></a>Redirecionando uma operação de mesclagem  
 Uma diretiva de mesclagem forward redireciona o destino de uma operação de mesclagem. Normalmente, o novo destino é o pai de inserção do destino inicial.  
  
 Por exemplo, uma DSL que foi criada com o modelo de diagrama de componente, portas são incorporadas em componentes. Portas são exibidas como pequenas formas na borda de uma forma de componente. O usuário cria portas arrastando a ferramenta de porta para uma forma de componente. Mas, às vezes, o usuário arrasta por engano a ferramenta de porta para uma porta existente, em vez do componente, e a operação falhará. Isso é um engano fácil quando há várias portas existentes. Para ajudar o usuário para evitar essa incômodo, você pode permitir portas ser arrastado para uma porta existente, mas a ação redirecionada para o componente pai. A operação funciona como se o elemento de destino foram o componente.  
  
 Você pode criar uma diretiva de mesclagem para frente na solução de modelo de componente. Se você compila e executar a solução original, você verá que os usuários poderão arrastar qualquer número de **porta de entrada** ou **porta de saída** elementos do **Toolbox** para um **componente** elemento. No entanto, eles não poderão arrastar uma porta para uma porta existente. Os alertas de ponteiro disponível que essa mudança não está habilitados. No entanto, você pode criar uma diretiva de mesclagem para frente para que uma porta que está, inadvertidamente, descartada em uma **porta de entrada** é encaminhado para o **componente** elemento.  
  
#### <a name="to-create-a-forward-merge-directive"></a>Para criar uma diretiva de mesclagem para frente  
  
1.  Criar um [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] solução usando o modelo do componente.  
  
2.  Exibição de **Gerenciador de DSL** abrindo Dsldefinition.  
  
3.  No **Gerenciador de DSL**, expanda **Classes de domínio**.  
  
4.  O **ComponentPort** classe abstrata de domínio é a classe base dos dois **InPort** e **OutPort**. Clique com botão direito **ComponentPort** e, em seguida, clique em **adicionar nova diretiva Element Merge**.  
  
     Um novo **diretiva Element Merge** nó aparece sob o **diretivas de mescla de elemento** nó.  
  
5.  Selecione o **diretiva Element Merge** nó e abra o **detalhes de DSL** janela.  
  
6.  Na lista de classe de indexação, selecione **ComponentPort**.  
  
7.  Selecione **encaminhar direta para uma classe de domínio diferentes**.  
  
8.  Na lista de seleção de caminho, expanda **ComponentPort**, expanda **ComponentHasPorts**e, em seguida, selecione **componente**.  
  
     O novo caminho deve ser semelhante a esta:  
  
     **ComponentHasPorts.Component/!Component**  
  
9. Salve a solução e, em seguida, transformar os modelos clicando no botão direito no **Solution Explorer** barra de ferramentas.  
  
10. Criar e executar a solução. Uma nova instância de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é exibida.  
  
11. Em **Solution Explorer**, abra Sample.mydsl. O diagrama e o **ComponentLanguage Toolbox** aparecer.  
  
12. Arraste um **porta de entrada** do **Toolbox** para outro **porta de entrada.** Em seguida, arraste uma **OutputPort** para um **InputPort** e, em seguida, a outro **OutputPort**.  
  
     Você não verá o ponteiro não está disponível e você poderá remover o novo **porta de entrada** em uma existente. Selecione o novo **porta de entrada** e arrastá-lo para outro ponto a **componente**.  
  
## <a name="see-also"></a>Consulte também  
 [Navegando e atualizando um modelo no código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Personalizando ferramentas e a caixa de ferramentas](../modeling/customizing-tools-and-the-toolbox.md)   
 [Exemplo de diagramas de circuito DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
