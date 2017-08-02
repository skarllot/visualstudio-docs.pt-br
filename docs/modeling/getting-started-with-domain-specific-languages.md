---
title: "Guia de Introdução com linguagens específicas do domínio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 024392a2-2c04-404f-a27b-7273553c3b60
caps.latest.revision: 16
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
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 8bd2f054db2c69a99218af05ca8d12465731ebca
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-domain-specific-languages"></a>Introdução às linguagens específicas do domínio
Este tópico explica os conceitos básicos de definindo e usando uma linguagem específica do domínio (DSL) criada com o SDK de modelagem para Visual Studio.  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
 Se você for novo no DSLs, recomendamos que você examine o **laboratório de ferramentas DSL**, que pode ser encontrado no site: [visualização e o SDK de modelagem](http://go.microsoft.com/fwlink/?LinkID=186128)  
  
## <a name="what-can-you-do-with-a-domain-specific-language"></a>O que você pode fazer com uma linguagem específica do domínio?  
 Uma linguagem específica do domínio é uma notação, geralmente gráfica, que é projetada para ser usado para uma finalidade específica. Por outro lado, as linguagens como UML são para fins gerais. Em uma DSL, você pode definir os tipos de elemento de modelo e seus relacionamentos e como são apresentados na tela.  
  
 Quando você tiver criado uma DSL, você pode distribuí-lo como parte de um pacote de extensão de integração do Visual Studio (VSIX). Os usuários trabalham com DSL no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
 ![Diagrama de árvore genealógica, caixa de ferramentas e o explorer](~/docs/modeling/media/familyt_instance.png "FamilyT_Instance")  
  
 A notação é apenas parte de uma DSL. Junto com a notação, o pacote VSIX inclui ferramentas que os usuários podem aplicar para ajudá-los a editar e gerar material de seus modelos.  
  
 Um dos principais aplicativos de DSLs é gerar o código do programa, arquivos de configuração e outros artefatos. Especialmente em grandes projetos e linhas de produtos, onde serão criados diversas variantes de um produto, a gerar muitos aspectos variável de DSLs pode fornecer um grande aumento na confiabilidade e muito rápida resposta às alterações de requisitos.  
  
 O restante desta visão geral é um passo a passo que apresenta as operações básicas de criação e uso de uma linguagem específica do domínio no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para definir uma DSL, é necessário ter instalados os seguintes componentes:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|SDK de modelagem para Visual Studio||  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
## <a name="creating-a-dsl-solution"></a>Criando uma solução DSL  
 Para criar uma nova linguagem específica do domínio, você cria um novo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução usando o modelo de projeto de linguagem específica do domínio.  
  
#### <a name="to-create-a-dsl-solution"></a>Para criar uma solução DSL  
  
1.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
2.  Em **tipos de projeto**, expanda o **Other Project Types** nó e clique em **extensibilidade**.  
  
3.  Clique em **Designer de linguagem específica do domínio**.  
  
     ![Criar caixa de diálogo DSL](~/docs/modeling/media/create_dsldialog.png "Create_DSLDialog")  
  
4.  No **nome** , digite **FamilyTree**. Clique em **OK**.  
  
     O **Assistente de linguagem específica do domínio** abre e exibe uma lista de soluções do modelo DSL.  
  
     Clique em cada modelo para ver uma descrição  
  
     Os modelos são úteis pontos de partida. Cada um deles fornece uma DSL, que você pode editar para atender às suas necessidades de trabalho concluído. Normalmente, você escolheria o modelo mais próximo de você deseja criar.  
  
5.  Para este passo a passo, escolha o **linguagem mínima** modelo.  
  
6.  Insira uma extensão de nome de arquivo para sua DSL na página do assistente apropriada. Essa é a extensão que será usada pelos arquivos que contêm as instâncias de sua DSL.  
  
    -   Escolha uma extensão que não está associada com qualquer aplicativo em seu computador ou em qualquer computador onde você deseja instalar a DSL. Por exemplo, **docx** e **htm** seria inaceitável arquivo extensões de nome.  
  
    -   O assistente o avisará se a extensão inserida está sendo usada como uma DSL. Considere usar uma extensão de nome de arquivo diferente. Também é possível redefinir a instância Experimental do SDK do Visual Studio para limpar os designers experimentais antigos. Clique em **iniciar**, clique em **todos os programas**, **SDK do Microsoft Visual Studio 2010**, **ferramentas**e então **redefinir a instância do Microsoft Visual Studio 2010 Experimental**.  
  
7.  Inspecione as outras páginas e, em seguida, clique em **concluir**.  
  
     É gerada uma solução que contém dois projetos. Eles são chamados Dsl e DslPackage. Um arquivo de diagrama é aberto que é nomeado Dsldefinition.  
  
    > [!NOTE]
    >  A maioria do código que você pode ver nas pastas em dois projetos é gerada a partir de Dsldefinition. Por esse motivo, a maioria das modificações DSL são feitas neste arquivo.  
  
 A interface do usuário agora se assemelha à imagem a seguir.  
  
 ![designer de DSL](~/docs/modeling/media/dsl_designer.png "dsl_designer")  
  
 Essa solução define uma linguagem específica de domínio. Para obter mais informações, consulte [visão geral da Interface do usuário específica do domínio idioma ferramentas](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).  
  
## <a name="the-important-parts-of-the-dsl-solution"></a>As partes importantes da solução DSL  
 Observe os seguintes aspectos da nova solução.  
  
-   **Dsl\DslDefinition.DSL** esse é o arquivo que você vê quando você cria uma solução DSL. Quase todo o código na solução é gerado a partir desse arquivo, e a maioria das alterações feitas em uma definição de DSL é feita aqui. Para obter mais informações, consulte Trabalhando com o [trabalhando com o diagrama de definição de DSL](../modeling/working-with-the-dsl-definition-diagram.md).  
  
-   **Projeto DSL** este projeto contém o código que define a linguagem específica do domínio.  
  
-   **Projeto DslPackage** este projeto contém o código que permite que as instâncias da DSL para ser aberto e editado no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
##  <a name="a-namedebugginga-running-the-dsl"></a><a name="Debugging"></a>Executando a DSL  
 Você pode executar a solução DSL assim que você criou. Posteriormente, você pode modificar a definição de DSL gradualmente, o executar a solução novamente após cada alteração.  
  
#### <a name="to-experiment-with-the-dsl"></a>Para experimentar a DSL  
  
1.  Clique em **transformar todos os modelos** na barra de ferramentas Solution Explorer. Isso gera novamente a maioria do código-fonte do Dsldefinition.  
  
    > [!NOTE]
    >  Sempre que alterar Dsldefinition, você deve clicar em **transformar todos os modelos** antes de recriar a solução. Você pode automatizar esta etapa. Para obter mais informações, consulte [como automatizar transformar todos os modelos](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a).  
  
2.  Pressione F5, ou o **depurar** menu, clique em **iniciar depuração**.  
  
     A DSL compilações e é instalado na instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Uma instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é iniciado. A instância experimental usa as configurações de uma subárvore separada do registro, onde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensões são registradas para fins de depuração. Instâncias normais do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] não tem acesso às extensões registrado nele.  
  
3.  Na instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], abra o arquivo de modelo chamado **teste** de **Solution Explorer**.  
  
     \- ou -  
  
     Clique com botão direito no projeto de depuração, aponte para **adicionar**e, em seguida, clique em **Item**. No **Adicionar Item** caixa de diálogo, selecione o tipo de arquivo de sua DSL.  
  
     O arquivo de modelo abre como um diagrama em branco.  
  
     A caixa de ferramentas abre e exibe ferramentas apropriadas para o tipo de diagrama.  
  
4.  Use as ferramentas para criar formas e conectores no diagrama.  
  
    1.  Para criar formas, arraste na ferramenta de forma de exemplo para o diagrama.  
  
    2.  Para conectar duas formas, clique na ferramenta Conector de exemplo, clique na primeira forma e, em seguida, clique na segunda forma.  
  
5.  Clique nos rótulos de formas para alterá-los.  
  
 Sua avaliação [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] será parecida com o exemplo a seguir:  
  
 ![](~/docs/modeling/media/dsl_min.png "DSL_min")  
  
### <a name="the-content-of-a-model"></a>O conteúdo de um modelo  
 O conteúdo de um arquivo que é uma instância de uma DSL é chamado um *modelo*. O modelo contém *modelo**elementos* e *links* entre os elementos. A definição de DSL Especifica quais tipos de elementos de modelo e links podem existir no modelo. Por exemplo, em uma DSL criada usando o modelo de linguagem mínima, há um tipo de elemento de modelo e um tipo de link.  
  
 A definição de DSL pode especificar como o modelo é exibido em um diagrama. Você pode escolher entre uma variedade de estilos de formas e conectores. Você pode especificar que algumas formas aparecem dentro de outras formas.  
  
 Você pode exibir um modelo como uma árvore de **Explorer** exibir enquanto você estiver editando um modelo. Como adicionar formas no diagrama, os elementos de modelo também aparecem no explorer. O explorer pode ser usado mesmo se não houver nenhum diagrama.  
  
 Se você não conseguir ver o Explorer na instância de depuração de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], no **exibição** menu, aponte para **outras janelas**e, em seguida, clique em * \<seu idioma >* **Explorer**.  
  
### <a name="the-api-of-your-dsl"></a>A API de sua DSL  
 A DSL gera uma API que permite ler e atualizar os modelos que são instâncias da DSL. Um aplicativo da API é gerar arquivos de texto de um modelo. Para obter mais informações, consulte [geração de código de tempo de Design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 Na solução de depuração, abra os arquivos de modelo com a extensão. "TT". Estes exemplos demonstram como você pode gerar texto de modelos e permitem que você teste a API da DSL. Um dos exemplos é escrito em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], os outros em [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
 Em cada modelo de arquivo é o arquivo que ele gera. Expanda o arquivo de modelo no Gerenciador de soluções e abra o arquivo gerado.  
  
 O arquivo de modelo contém um breve segmento de código que lista todos os elementos no modelo.  
  
 O arquivo gerado contém o resultado.  
  
 Quando você altera um arquivo de modelo, você verá as alterações correspondentes nos arquivos gerados após regenerar os arquivos.  
  
##### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>Para recriar os arquivos de texto depois de alterar o arquivo de modelo  
  
1.  Na instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], salve o arquivo de modelo.  
  
2.  Certifique-se de que o parâmetro de nome de arquivo em cada arquivo. TT refere-se ao arquivo de modelo que você está usando para testes. Salve o arquivo. tt.  
  
3.  Clique em **transformar todos os modelos** na barra de ferramentas de **Solution Explorer**.  
  
     \- ou -  
  
     Clique com botão direito os modelos que você deseja gerar novamente e, em seguida, clique em **executar ferramenta personalizada**.  
  
 Você pode adicionar qualquer número de arquivos de modelo de texto a um projeto. Cada modelo gera um arquivo de resultados.  
  
> [!NOTE]
>  Quando você altera a definição de DSL, o código de modelo de texto de exemplo não funcionará, a menos que você atualizá-lo.  
  
 Para obter mais informações, consulte [código de geração de uma linguagem específica do domínio](../modeling/generating-code-from-a-domain-specific-language.md) e [escrevendo código para personalizar uma linguagem específica do domínio](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
## <a name="customizing-the-dsl"></a>Personalizando a DSL  
 Quando você quiser modificar a definição de DSL, feche a instância experimental e atualizar a definição no principal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instância.  
  
> [!NOTE]
>  Depois de modificar a definição de DSL, você poderá perder informações nos modelos de teste que você criou usando versões anteriores.  Por exemplo, a solução de depuração contém um arquivo chamado Sample, que contém algumas formas e conectores. Depois que você começa a desenvolver sua definição de DSL, eles não estarão visíveis e elas serão perdidas quando você salvar o arquivo.  
  
 Você pode fazer uma grande variedade de extensões de DSL. Os exemplos a seguir lhe dará uma impressão das possibilidades.  
  
 Após cada alteração, salve a definição de DSL, clique em **transformar todos os modelos** na **Solution Explorer**e pressione **F5** para experimentar a DSL alterada.  
  
### <a name="rename-the-types-and-tools"></a>Renomeie os tipos e as ferramentas  
 Renomeie a classes de domínio existentes e relações. Por exemplo, a partir de uma definição de Dsl criados usando o modelo de linguagem mínima, você pode executar as seguintes operações de renomeação, para tornar a DSL representam árvores de família.  
  
##### <a name="to-rename-domain-classes-relationships-and-tools"></a>Para renomear classes de domínio, relações e ferramentas  
  
1.  No diagrama DslDefinition, renomeie **ExampleModel** para **FamilyTreeModel**, **ExampleElement** para **pessoa**, **destinos** para **pais**, e **fontes** para **filhos**. Você pode clicar em cada rótulo para alterá-la.  
  
     ![Diagrama de definição de DSL - modelo de árvore genealógica](~/docs/modeling/media/familyt_person.png "FamilyT_Person")  
  
2.  Renomeie as ferramentas de elemento e o conector.  
  
    1.  Abra a janela Gerenciador de DSL, clicando na guia no Gerenciador de soluções. Se você não vir, no **exibição** menu, aponte para **outras janelas** e, em seguida, clique em **Gerenciador de DSL**. Gerenciador de DSL só é visível quando o diagrama de definição de DSL é a janela ativa.  
  
    2.  Abra a janela Propriedades e posicione-o para que você possa ver Gerenciador de DSL e propriedades ao mesmo tempo.  
  
    3.  No Gerenciador de DSL, expanda **Editor**, **guias da caixa de ferramentas**, * \<DSL >*e então **ferramentas**.  
  
    4.  Clique em **ExampleElement**. Este é o item de caixa de ferramentas que é usado para criar elementos.  
  
    5.  Na janela Propriedades, altere o **nome** propriedade **pessoa**.  
  
         Observe que o **legenda** propriedade também será alterado.  
  
    6.  Da mesma forma, altere o nome do **ExampleConnector** ferramenta para **ParentLink**. Alterar o **legenda** propriedade para que ele não seja uma cópia da propriedade Name. Por exemplo, digite **Link pai**.  
  
3.  Recrie a DSL.  
  
    1.  Salve o arquivo de definição de DSL.  
  
    2.  Clique em **transformar todos os modelos** na barra de ferramentas do Gerenciador de soluções  
  
    3.  Pressione F5. Aguarde até que a instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é exibida.  
  
4.  A solução de depuração na instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], abra um arquivo de modelo de teste. Arraste elementos para ele na caixa de ferramentas. Observe que as legendas de ferramenta e os nomes de tipo no Gerenciador de DSL foram alterados.  
  
5.  Salve o arquivo de modelo.  
  
6.  Abrir um arquivo. TT e substituir ocorrências dos nomes de tipo e propriedade antigas com os novos nomes.  
  
7.  Certifique-se de que o nome do arquivo especificado no arquivo. TT especifica seu modelo de teste.  
  
8.  Salve o arquivo. tt. Abra o arquivo gerado para ver o resultado da execução do código no arquivo. tt. Verifique se ele está correto.  
  
### <a name="add-domain-properties-to-classes"></a>Adicionar propriedades de domínio para Classes  
 Adicione propriedades a uma classe de domínio, por exemplo, para representar os anos de nascimento e morte de uma pessoa.  
  
 Para tornar as novas propriedades visíveis no diagrama, você deve adicionar *decoradores* à forma que exibe o elemento de modelo. Você também deve mapear as propriedades para os decoradores.  
  
##### <a name="to-add-properties-and-display-them"></a>Para adicionar propriedades e exibi-los  
  
1.  Adicione as propriedades.  
  
    1.  No diagrama de definição de DSL, clique com botão direito do **pessoa** classe de domínio, aponte para **adicionar**e, em seguida, clique em **propriedade Domain**.  
  
    2.  Digite uma lista de novos nomes de propriedade, como **nascimento** e **morte**. Pressione **Enter** após cada um deles.  
  
2.  Adicione decoradores que exibirão as propriedades da forma.  
  
    1.  Siga a linha cinza que estende a classe de domínio da pessoa para o outro lado do diagrama. Isso é um mapa de elemento do diagrama. Vincula a classe de domínio para uma classe shape.  
  
    2.  Essa classe de forma de atalho, aponte para **adicionar**e, em seguida, clique em **decorador de texto**.  
  
    3.  Adicione dois decoradores com nomes como **BirthDecorator** e **DeathDecorator**.  
  
    4.  Selecione cada decorador novo e na janela Propriedades, defina o **posição** campo. Isso determina onde o valor da propriedade de domínio será exibido na forma. Por exemplo, defina **InnerBottomLeft** e **InnerBottomRight**.  
  
         ![Definição da forma do compartimento](~/docs/modeling/media/familyt_compartment.png "FamilyT_Compartment")  
  
3.  Mapear os decoradores para as propriedades.  
  
    1.  Abra a janela de detalhes de DSL. Geralmente, é uma guia ao lado da janela de saída. Se você não vir, no **exibição** , aponte para **outras janelas**e, em seguida, clique em **detalhes de DSL**.  
  
    2.  No diagrama de definição de DSL, clique na linha que conecta o **pessoa** classe de domínio para a classe shape.  
  
    3.  Em **detalhes de DSL**diante do **mapas do decorador** guia, clique na caixa de seleção em um decorador não mapeado. Em **Exibir propriedade**, selecione a propriedade de domínio ao qual você deseja que ela está mapeada. Por exemplo, mapear **BirthDecorator** para **nascimento**.  
  
4.  Salvar a DSL, clique em transformar todos os modelos e pressione F5.  
  
5.  Em um diagrama de modelo de exemplo, verifique se que agora você pode clicar as posições que você escolheu e digite valores para eles. Além disso, quando você seleciona um **pessoa** forma, a janela Propriedades exibe as propriedades de novo nascimento e morte.  
  
6.  Em um arquivo. TT, você pode adicionar código que obtém as propriedades de cada pessoa.  
  
 ![Diagrama de árvore genealógica, caixa de ferramentas e o explorer](~/docs/modeling/media/familyt_instance.png "FamilyT_Instance")  
  
### <a name="define-new-classes"></a>Definir novas Classes  
 Você pode adicionar classes de domínio e relações em um modelo. Por exemplo, você poderia criar uma nova classe para representar cidades e uma nova relação para representar que uma pessoa viver em uma cidade.  
  
 Para tornar os diferentes tipos distintos em um diagrama de modelo, você pode mapear as classes de domínio para tipos diferentes de forma ou formas com cores e geometria diferente.  
  
##### <a name="to-add-and-display-a-new-domain-class"></a>Para adicionar e exibir uma nova classe de domínio  
  
1.  Adicionar uma classe de domínio e torná-lo um filho da raiz do modelo.  
  
    1.  No diagrama de definição de DSL, clique o **relação de incorporação** ferramenta, clique na classe raiz **FamilyTreeModel**e clique em uma parte vazia do diagrama.  
  
         Uma nova classe de domínio será exibida, que está conectado ao FamilyTreeModel com uma relação de incorporação.  
  
         Defina seu nome, por exemplo **Cidade**.  
  
        > [!NOTE]
        >  Cada classe de domínio, exceto a raiz do modelo deve ser o destino de pelo menos uma relação de incorporação ou ela deve herdar de uma classe que é o destino de uma inserção. Por esse motivo, é conveniente com frequência criar uma classe de domínio usando a ferramenta de relação de incorporação.  
  
    2.  Adicionar uma propriedade de domínio para a nova classe, por exemplo **nome**.  
  
2.  Adicione uma relação de referência entre pessoa e cidade.  
  
    1.  Clique o **relação de referência** ferramenta, clique em pessoa e, em seguida, clique em cidade.  
  
         ![Fragmento da definição de DSL: raiz da árvore genealógica](~/docs/modeling/media/familyt_root.png "FamilyT_Root")  
  
        > [!NOTE]
        >  Relações de referência representam referências cruzadas de uma parte da árvore modelo para outro.  
  
3.  Adicione uma forma para representar as cidades em diagramas de modelo.  
  
    1.  Arraste uma **forma geométrica** da caixa de ferramentas para o diagrama e renomeá-lo, por exemplo **TownShape**.  
  
    2.  Na janela Propriedades, defina os campos de aparência da nova forma, como cor de preenchimento e Geometry.  
  
    3.  Adicione um decorador para exibir o nome da cidade e renomeá-lo NameDecorator. Defina sua propriedade de posição.  
  
4.  A classe de domínio de cidade são mapeados para o TownShape.  
  
    1.  Clique o **mapa de elemento do diagrama** ferramenta, clique em classe de domínio cidade e a classe de forma TownShape.  
  
    2.  No **mapas do decorador** guia o **detalhes de DSL** janela com o conector de mapa selecionado, verifique NameDecorator e defina **Exibir propriedade** ao nome.  
  
5.  Crie um conector para exibir a relação entre a pessoa e cidades.  
  
    1.  Arraste um conector da caixa de ferramentas para o diagrama. Renomeie-o e defina suas propriedades de aparência.  
  
    2.  Use o **mapa de elemento do diagrama** ferramenta para vincular o novo conector à relação entre pessoa e cidade.  
  
         ![Definição de árvore genealógica com mapa de forma adicionada](~/docs/modeling/media/familyt_shapemap.png "FamilyT_ShapeMap")  
  
6.  Crie uma ferramenta de elemento para fazer uma cidade de novo.  
  
    1.  Em **Gerenciador de DSL**, expanda **Editor** , em seguida, **guias da caixa de ferramentas**.  
  
    2.  Clique com botão direito * \<DSL >* e, em seguida, clique em **adicionar nova ferramenta de elemento**.  
  
    3.  Definir o **nome** propriedade da nova ferramenta e definir seu **classe** propriedade adiante.  
  
    4.  Definir o **ícone caixa de ferramentas** propriedade. Click **[...] ** e além do **nome de arquivo** , selecione um arquivo de ícone.  
  
7.  Crie uma ferramenta de conector para criar um link entre cidades e pessoas.  
  
    1.  Clique com botão direito * \<DSL >* e, em seguida, clique em **adicionar nova ferramenta de conector**.  
  
    2.  Defina a propriedade de nome da nova ferramenta.  
  
    3.  No **ConnectionBuilder** propriedade, selecione o construtor que contém o nome da relação pessoa-cidade.  
  
    4.  Definir o **ícone caixa de ferramentas**.  
  
8.  Salvar a definição de DSL, clique em **transformar todos os modelos**e então pressione **F5**.  
  
9. Na instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], abra um arquivo de modelo de teste. Use as novas ferramentas para criar links entre cidades e pessoas e cidades. Observe que você só pode criar links entre os tipos corretos de elemento.  
  
10. Crie código que lista a cidade em que cada pessoa reside. Modelos de texto são um dos lugares onde você pode executar esse código. Por exemplo, você poderia modificar o arquivo Sample.tt existente na solução de depuração para que ele contém o código a seguir:  
  
    ```  
    <#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" debug="true" #>  
    <#@ output extension=".txt" #>  
    <#@ FamilyTree processor="FamilyTreeDirectiveProcessor" requires="fileName='Sample.ftree'" #>  
  
    <#  
      foreach (Person person in this.FamilyTreeModel.People)  
      {  
    #>  
        <#= person.Name #><#if (person.Town != null) {#> of <#= person.Town.Name #> <#}#>  
  
    <#  
          foreach (Person child in person.Children)  
      {  
    #>  
                <#= child.Name #>  
    <#  
      }  
      }  
    #>  
  
    ```  
  
     Quando você salva o arquivo TT, ele criará um arquivo subsidiário que contém a lista de pessoas e suas residências. Para obter mais informações, consulte [código de geração de uma linguagem específica do domínio](../modeling/generating-code-from-a-domain-specific-language.md).  
  
## <a name="validation-and-commands"></a>Validação e comandos  
 Você pode desenvolver ainda mais essa DSL adicionando restrições de validação. Essas restrições são métodos que você pode definir, certifique-se de que o modelo está no estado correto. Por exemplo, você poderia definir uma restrição para garantir que a data de nascimento de um filho é posterior de seus pais. O recurso de validação exibe um aviso se o usuário DSL tenta salvar um modelo que violam nenhuma das restrições. Para obter mais informações, consulte [validação em uma linguagem específica do domínio](../modeling/validation-in-a-domain-specific-language.md).  
  
 Você também pode definir comandos de menu que o usuário pode chamar. Comandos podem modificar o modelo. Eles também podem interagir com outros modelos no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e com recursos externos. Para obter mais informações, consulte [como: modificar um comando de Menu padrão](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
## <a name="deploying-the-dsl"></a>Implantando a DSL  
 Para permitir que outros usuários usem a linguagem específica do domínio, você distribui um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] arquivo de extensão (VSIX). Isso é criado quando você compila a solução DSL.  
  
 Localize o arquivo. VSIX na pasta bin de sua solução. Copie-o para o computador no qual você deseja instalá-lo. Nesse computador, clique duas vezes no arquivo VSIX. A DSL pode ser usada em todas as instâncias de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nesse computador.  
  
 Você pode usar o mesmo procedimento para instalar a DSL em seu próprio computador para que você não precisa usar a instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Para obter mais informações, consulte [implantar soluções de linguagem específica do domínio](../modeling/deploying-domain-specific-language-solutions.md).  
  
##  <a name="a-namereseta-removing-old-experimental-dsls"></a><a name="Reset"></a>Removendo DSLs experimentais antigos  
 Se você tiver criado as DSLs experimentais que desejar, você poderá removê-los do seu computador, redefinindo o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instância Experimental.  
  
 Isso removerá do seu computador, todas as DSLs experimentais e outros experimentais [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensões. Essas são as extensões que foram executadas no modo de depuração.  
  
 Esse procedimento não remove as DSLs ou outros [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensões que foram totalmente instaladas executando o arquivo VSIX.  
  
#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Para redefinir a instância Experimental do Visual Studio  
  
1.  Clique em **iniciar**, clique em **todos os programas**, **SDK do Microsoft Visual Studio 2010**, **ferramentas**e então **redefinir a instância do Microsoft Visual Studio 2010 Experimental**.  
  
2.  Recriar qualquer experimentais DSLs ou outros experimental [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensões que deseja usar.  
  
## <a name="see-also"></a>Consulte também  
 [Noções básicas sobre modelos, Classes e relações](../modeling/understanding-models-classes-and-relationships.md)   
 [Como definir uma linguagem específica de domínio](../modeling/how-to-define-a-domain-specific-language.md)   

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


