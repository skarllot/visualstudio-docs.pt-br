---
title: "Personalizando a serialização de XML e armazenamento de arquivo | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
ms.assetid: 76c53ef1-e3b9-45da-b425-1bddb3c01395
caps.latest.revision: 17
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 2c737f86064f87093844ccbacb645bb6460caf4f
ms.lasthandoff: 02/22/2017

---
# <a name="customizing-file-storage-and-xml-serialization"></a>Personalizando o armazenamento de arquivos e a serialização XML
Quando o usuário salva uma instância ou *modelo*, de uma linguagem específica do domínio (DSL) em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], um arquivo XML é criado ou atualizado. O arquivo poderá ser recarregado para recriar o modelo no repositório.  
  
 Você pode personalizar o esquema de serialização, ajustando as configurações em **o comportamento de serialização Xml** no Gerenciador de DSL. Há um nó em **o comportamento de serialização Xml** para cada classe de domínio, propriedade e relação. As relações são localizadas em suas classes de origem. Também há nós que correspondem a forma, conector e classes de diagrama.  
  
 Você também pode escrever código de programa para uma personalização mais avançada.  
  
> [!NOTE]
>  Se você deseja salvar o modelo em um formato específico, mas não é necessário recarregá-lo do formulário, considere o uso de modelos de texto para gerar a saída do modelo, em vez de um esquema de serialização personalizada. Para obter mais informações, consulte [código de geração de uma linguagem específica do domínio](../modeling/generating-code-from-a-domain-specific-language.md).  
  
## <a name="model-and-diagram-files"></a>Arquivos de modelo e diagrama  
 Geralmente, cada modelo é salvo em dois arquivos:  
  
-   O arquivo de modelo tem um nome como **Model1.mydsl**. Ele armazena os elementos de modelo e relações e suas propriedades. A extensão de arquivo, como **.mydsl** é determinado pelo **FileExtension** propriedade o **Editor** nó na definição de DSL.  
  
-   O arquivo de diagrama tem um nome como **Model1.mydsl.diagram**. Ele armazena as formas, conectores e suas posições, cores, espessuras de linha e outros detalhes da aparência do diagrama. Se o usuário exclui um **.diagram** arquivo, as informações essenciais no modelo não são perdidas. Apenas o layout do diagrama é perdido. Quando o arquivo de modelo é aberto, um padrão definido de formas e conectores serão criados.  
  
#### <a name="to-change-the-file-extension-of-a-dsl"></a>Para alterar a extensão de arquivo de uma DSL  
  
1.  Abra a definição de DSL. No Gerenciador de DSL, clique no nó do Editor.  
  
2.  Na janela Propriedades, edite o **FileExtension** propriedade. Não inclua o inicial "." da extensão do nome do arquivo.  
  
3.  No Solution Explorer, altere o nome dos arquivos de modelo de dois itens em **DslPackage\ProjectItemTemplates**. Esses arquivos têm nomes que seguem este formato:  
  
     `myDsl.diagram`  
  
     `myDsl.myDsl`  
  
## <a name="the-default-serialization-scheme"></a>O esquema de serialização padrão  
 Para criar um exemplo deste tópico, a seguinte definição de DSL foi usada.  
  
 ![Diagrama de definição de DSL - modelo de árvore genealógica](~/docs/modeling/media/familyt_person.png "FamilyT_Person")  
  
 Essa DSL foi usado para criar um modelo que tem a seguinte aparência na tela.  
  
 ![Diagrama de árvore genealógica, caixa de ferramentas e o explorer](~/docs/modeling/media/familyt_instance.png "FamilyT_Instance")  
  
 Esse modelo foi salvo e aberto novamente no editor de texto XML:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<familyTreeModel xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="f817b728-e920-458e-bb99-98edc469d78f" xmlns="http://schemas.microsoft.com/dsltools/FamilyTree">  
  <people>  
    <person name="Henry VIII" birthYear="1491" deathYear="1547" age="519">  
      <children>  
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />  
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Mary" />  
      </children>  
    </person>  
    <person name="Elizabeth I" birthYear="1533" deathYear="1603" age="477" />  
    <person name="Mary" birthYear="1515" deathYear="1558" age="495" />  
  </people>  
</familyTreeModel>  
  
```  
  
 Observe os seguintes pontos sobre o modelo serializado:  
  
-   Cada nó XML tem um nome que é o mesmo que um nome de classe de domínio, exceto que a primeira letra é minúscula. Por exemplo, `familyTreeModel` e `person`.  
  
-   Propriedades do domínio, como nome e BirthYear são serializadas como atributos em nós do XML. Novamente, o caractere inicial do nome da propriedade é convertido em minúsculas.  
  
-   Cada relação é serializada como um nó XML aninhado dentro da extremidade de origem da relação. O nó tem o mesmo nome que a propriedade da função de origem, mas com um caractere inicial minúscula.  
  
     Por exemplo, na definição de DSL, uma função chamada **pessoas** tem origem no **FamilyTree** classe.  No XML, é representado pelo nó chamado `people` aninhadas dentro de `familyTreeModel` nó.  
  
-   Na extremidade de destino de cada relação de incorporação é serializada como um nó aninhado sob a relação. Por exemplo, o `people` nó contém vários `person` nós.  
  
-   Na extremidade de destino de cada relação de referência é serializada como uma *moniker*, que codifica uma referência ao elemento de destino.  
  
     Por exemplo, em um `person` nó, pode haver um `children` relação. Esse nó contém identificadores de origem, como:  
  
    ```  
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />  
    ```  
  
## <a name="understanding-monikers"></a>Noções básicas sobre identificadores  
 Identificadores são usados para representar referências cruzadas entre diferentes partes dos arquivos de modelo e o diagrama. Eles também são usados no `.diagram` arquivo para referir-se a nós no arquivo do modelo. Há duas formas de moniker:  
  
-   *Identificadores de ID* citar o GUID do elemento de destino. Por exemplo:  
  
    ```  
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />  
  
    ```  
  
-   *Qualificado monikers chave* identificar o elemento de destino, o valor de uma propriedade de domínio designado, chamado de chave do moniker. O moniker do elemento de destino é prefixado pelo moniker do seu elemento pai na árvore de relações inseridas.  
  
     Os exemplos a seguir são executados de uma DSL no qual existe é uma classe de domínio chamada álbum, que tem uma relação de incorporação para um domínio nomeada música da classe:  
  
    ```  
    <albumMoniker title="/My Favorites/Jazz after Teatime" />  
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />  
  
    ```  
  
     Qualificado monikers chave serão usados se a classe de destino tem uma propriedade de domínio para o qual a opção **é a chave do Moniker** é definido como `true` na **o comportamento de serialização Xml**. No exemplo, essa opção é definida para propriedades de domínio denominadas "Título" nas classes de domínio "Álbum" e "Música".  
  
 Qualificado identificadores de chave são mais fáceis de ler do que os identificadores de ID. Se você pretende que o XML de seus arquivos de modelo a ser lido por pessoas, considere o uso de monikers chave qualificados. No entanto, é possível que o usuário definir mais de um elemento com a mesma chave do moniker. Chaves duplicadas pode causar o recarregamento do arquivo não corretamente. Portanto, se você definir uma classe de domínio que é referenciada usando identificadores de chave qualificados, você deve considerar maneiras de impedir que o usuário salvar um arquivo que tem identificadores duplicados.  
  
#### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Para definir uma classe de domínio para ser referenciado por identificadores de ID  
  
1.  Verifique se **é a chave do Moniker** é `false` para cada propriedade de domínio na classe e suas classes base.  
  
    1.  No Gerenciador de DSL, expanda **dados de Behavior\Class de serialização de Xml\\***\<a classe de domínio >***\Element dados**.  
  
    2.  Verifique **é a chave do Moniker** é `false` para cada propriedade de domínio.  
  
    3.  Se a classe de domínio tiver uma classe base, repita o procedimento dessa classe.  
  
2.  Definir **serializar Id**  =  `true` para a classe de domínio.  
  
     Essa propriedade pode ser encontrada em **o comportamento de serialização Xml**.  
  
#### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Para definir uma classe de domínio para fazer referência a identificadores de chave qualificados  
  
-   Definir **chave do Moniker é** para uma propriedade de domínio de uma classe de domínio existente. O tipo da propriedade deve ser `string`.  
  
    1.  No Gerenciador de DSL, expanda **dados de Behavior\Class de serialização de Xml\\***\<a classe de domínio >***\Element dados**e, em seguida, selecione a propriedade de domínio.  
  
    2.  Na janela Propriedades, defina **é a chave do Moniker** para `true`.  
  
-   \- ou -  
  
     Criar um novo domínio classe usando o **classe de domínio nomeado** ferramenta.  
  
     Essa ferramenta cria uma nova classe que tem uma propriedade de domínio denominada nome. O **é o nome do elemento** e **é a chave do Moniker** propriedades dessa propriedade de domínio são inicializadas em `true`.  
  
-   \- ou -  
  
     Crie uma relação de herança de classe de domínio para outra classe que tem uma propriedade de chave do moniker.  
  
### <a name="avoiding-duplicate-monikers"></a>Evitando Monikers duplicados  
 Se você usar identificadores qualificados de chave, é possível que dois elementos no modelo de um usuário pode ter o mesmo valor na propriedade de chave. Por exemplo, se sua DSL tem uma classe Person que tem um nome de propriedade, o usuário pode definir os nomes de dois elementos sejam os mesmos. Embora o modelo pode ser salvo em arquivo, ele seria não recarregar corretamente.  
  
 Há vários métodos que ajudam a evitar essa situação:  
  
-   Definir **é o nome do elemento**  =  `true` para a propriedade de chave do domínio. Selecione a propriedade de domínio no diagrama de definição de DSL e, em seguida, defina o valor na janela Propriedades.  
  
     Quando o usuário cria uma nova instância da classe, esse valor faz com que a propriedade de domínio a ser atribuído automaticamente um valor diferente. O comportamento padrão adiciona um número ao final do nome da classe. Isso não impede que o usuário alterar o nome de uma duplicata, mas ajuda no caso de quando o usuário não define o valor antes de salvar o modelo.  
  
-   Habilite a validação para a DSL. No Gerenciador de DSL, selecione Editor \ validação e defina o **usa... ** propriedades `true`.  
  
     Há um método de validação gerados automaticamente que verifica ambiguidades. O método está sendo o `Load` categoria de validação. Isso garante que o usuário será avisado que talvez não seja possível abrir o arquivo novamente.  
  
     Para obter mais informações, consulte [validação em uma linguagem específica do domínio](../modeling/validation-in-a-domain-specific-language.md).  
  
### <a name="moniker-paths-and-qualifiers"></a>Qualificadores e caminhos de moniker  
 Um moniker chave qualificado termina com a chave do moniker e é prefixado com o moniker do seu pai na árvore de incorporação. Por exemplo, se o identificador de origem de um álbum é:  
  
```  
<albumMoniker title="/My Favorites/Jazz after Teatime" />  
  
```  
  
 Então, uma das músicas desse álbum poderia ser:  
  
```  
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />  
```  
  
 No entanto, se álbuns são referenciados por ID em vez disso, em seguida, os identificadores de origem será da seguinte maneira:  
  
```  
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />  
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />  
```  
  
 Observe que como um GUID é exclusivo, ele é nunca antecedido o moniker do seu pai.  
  
 Se você souber que uma propriedade de domínio específico sempre terá um valor exclusivo dentro de um modelo, você pode definir **é qualificador do Moniker** para `true` para essa propriedade. Isso fará com que ele seja usado como um qualificador, sem usar o moniker do pai. Por exemplo, se você definir ambos **é qualificador do Moniker** e **chave do Moniker é** para a propriedade domain do título da classe álbum, nome ou o identificador do modelo não é usado em identificadores de álbum e seus filhos inseridos:  
  
```  
<albumMoniker name="Jazz after Teatime" />  
<songMoniker title="/Jazz after Teatime/Hot tea" />  
  
```  
  
## <a name="customizing-the-structure-of-the-xml"></a>Personalizando a estrutura do XML  
 Para fazer as seguintes personalizações, expanda o **o comportamento de serialização Xml** nó no Gerenciador de DSL. Em uma classe de domínio, expanda o nó de dados do elemento para ver a lista de propriedades e relações que são originadas dessa classe. Selecione uma relação e ajustar suas opções na janela Propriedades.  
  
-   Definir **omitir o elemento** como true para omitir o nó de função de origem, deixando apenas a lista de elementos de destino. Você não deve definir essa opção se houver mais de uma relação entre as classes de origem e destino.  
  
    ```  
  
    <familyTreeModel ...>  
      <!-- The following node is omitted by using Omit Element: -->  
      <!-- <people> -->  
        <person name="Henry VIII" .../>  
        <person name="Elizabeth I" .../>  
      <!-- </people> -->  
    </familyTreeModel>  
  
    ```  
  
-   Definir **usar o formulário completo** para inserir os nós de destino em nós que representam as instâncias de relação. Essa opção é definida automaticamente quando você adiciona propriedades do domínio a uma relação de domínio.  
  
    ```  
  
    <familyTreeModel ...>  
      <people>  
        <!-- The following node is inserted by using Use Full Form: -->  
        <familyTreeModelHasPeople myRelationshipProperty="x1">  
          <person name="Henry VIII" .../>  
        </familyTreeModelHasPeople>  
        <familyTreeModelHasPeople myRelationshipProperty="x2">  
          <person name="Elizabeth I" .../>  
        </familyTreeModelHasPeople>  
      </people>  
    </familyTreeModel>  
  
    ```  
  
-   Definir **representação** = **elemento** ter uma propriedade de domínio salva como elemento, em vez de como um valor de atributo.  
  
    ```  
    <person name="Elizabeth I" birthYear="1533">  
      <deathYear>1603</deathYear>  
    </person>  
    ```  
  
-   Para alterar a ordem na qual os atributos e relações são serializadas, clique em um item de dados do elemento e usar o **mover para cima** ou **mover para baixo** comandos de menu.  
  
## <a name="major-customization-using-program-code"></a>Principais personalização usando um código de programa  
 Você pode substituir partes ou todos os algoritmos de serialização.  
  
 É recomendável que você estude o código em **Dsl\Generated Code\Serializer.cs** e **SerializationHelper.cs**.  
  
#### <a name="to-customize-the-serialization-of-a-particular-class"></a>Para personalizar a serialização de uma determinada classe  
  
1.  Definir **personalizado é** no nó para a classe em **o comportamento de serialização Xml**.  
  
2.  Transformar todos os modelos, criar a solução e para investigar os erros de compilação resultante. Comentários perto de cada erro explicam o que o código que você precisa fornecer.  
  
#### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Para fornecer sua própria serialização para todo o modelo  
  
1.  Substituir métodos em Dsl\GeneratedCode\SerializationHelper.cs  
  
## <a name="options-in-xml-serialization-behavior"></a>Opções de comportamento de serialização de Xml  
 No Gerenciador de DSL, o nó de comportamento de serialização de Xml contém um nó filho para cada classe de domínio, relação, forma, conector e classe de diagrama. Em cada um de nós é uma lista de propriedades e relações originadas desse elemento. Relações são representadas por si mesmos e em suas classes de origem.  
  
 A tabela a seguir resume as opções que podem ser definidas nesta seção da definição de DSL. Em cada caso, selecione um elemento no Gerenciador de DSL e defina as opções na janela Propriedades.  
  
### <a name="xml-class-data"></a>Dados de classe XML  
 Esses elementos são encontrados no Gerenciador de DSL sob **dados de Behavior\Class de serialização de Xml**.  
  
|||  
|-|-|  
|Propriedade|Descrição|  
|Com o esquema do elemento personalizado|Se for verdadeiro, indica que a classe de domínio tem um esquema de elemento personalizado|  
|É personalizada|Defina-o como **True** se quiser escrever seu próprio código de serialização e desserialização para essa classe de domínio.<br /><br /> Crie a solução e para investigar os erros para obter instruções detalhadas de descobrir.|  
|Classe de domínio|Classe de domínio ao qual se aplica a este nó de dados de classe. Somente leitura.|  
|Nome de elementos|Nome do nó XML para elementos dessa classe. O valor padrão é uma versão em letras minúsculas do nome da classe de domínio.|  
|Nome de atributo do identificador de origem|Nome do atributo usado nos elementos do moniker para conter a referência. Se estiver vazio, o nome da propriedade de chave ou id é usado.<br /><br /> Neste exemplo, é "name":`<personMoniker name="/Mike Nash"/>`|  
|Nome de elemento do identificador de origem|Nome do elemento xml usado para identificadores se referem a elementos dessa classe.<br /><br /> O valor padrão é uma versão em letra minúscula do nome da classe sufixado com "Moniker". Por exemplo, `personMoniker`.|  
|Nome de tipo de identificador de origem|Nome do tipo xsd gerado para identificadores de origem para elementos dessa classe. O XSD é em **código de Dsl\Generated\\\*XSD**|  
|Serializar Id|Se verdadeiro, o GUID de elemento é incluído no arquivo. Isso deve ser verdadeiro se não houver nenhuma propriedade está marcado como **chave do Moniker é** e a DSL define relações de referência a essa classe.|  
|Nome do tipo|Nome do tipo xml gerado no xsd da classe de domínio designado.|  
|Observações|Notas informais associadas a este elemento|  
  
### <a name="xml-property-data"></a>Dados de propriedade de XML  
 Nós de propriedade XML são encontradas em nós de classe.  
  
|||  
|-|-|  
|Propriedade|Descrição|  
|Propriedade de domínio|Propriedade à qual os dados de configuração de serialização de xml se aplica. Somente leitura.|  
|É a chave do Moniker|Se for True, a propriedade é usada como a chave para a criação de identificadores que referenciam as instâncias dessa classe de domínio.|  
|É o qualificador do Moniker|Se for True, a propriedade é usada para criar o qualificador em identificadores. Se false, e se SerializeId não é válido para essa classe de domínio, identificadores são qualificados pelo moniker do elemento pai na árvore de incorporação.|  
|Representação|Se o atributo, a propriedade é serializado como um atributo xml; Se o elemento, ela será serializada como um elemento. Se ignorar, ele não será serializado.|  
|Nome de XML|Nome usado para o elemento que representa a propriedade ou atributo xml. Por padrão, essa é uma versão em letras minúsculas do nome da propriedade de domínio.|  
|Observações|Notas informais associadas a este elemento|  
  
### <a name="xml-role-data"></a>Dados da função de XML  
 Nós de dados de função são encontrados em nós de classe de origem.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|Tem o identificador de origem|Defina como verdadeiro se você desejar fornecer seu próprio código para gerar e resolver os identificadores que atravessam essa relação.<br /><br /> Para obter instruções detalhadas, crie a solução e, em seguida, clique duas vezes em mensagens de erro.|  
|Relação de domínio|Especifica a relação para que essas opções se aplicam. Somente leitura.|  
|Omitir o elemento|Se for true, o nó XML que corresponde à função de origem é omitido do esquema.<br /><br /> Se houver mais de uma relação entre as classes de origem e de destino, este nó de função faz distinção entre os links que pertencem a duas relações. Portanto, recomendamos que você não definir essa opção nesse caso.|  
|Nome do elemento de função|Especifica o nome do elemento XML que é derivado da função de origem. O valor padrão é o nome da propriedade de função.|  
|Use a forma completa|Se true, cada elemento de destino ou o identificador de origem é colocado em um nó XML que representa a relação. Isso deve ser definido como verdadeiro se a relação tem suas próprias propriedades de domínio.|  
  
## <a name="see-also"></a>Consulte também  
 [Navegando e atualizando um modelo no código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Gerando código com base em uma linguagem específica de domínio](../modeling/generating-code-from-a-domain-specific-language.md)
