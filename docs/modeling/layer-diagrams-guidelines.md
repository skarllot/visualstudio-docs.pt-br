---
title: "Diagramas de dependência: Diretrizes | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 2903bec7-a93b-46a6-aac6-994ac4f3f1a7
caps.latest.revision: 55
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
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
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 8233d0d6ce81a0869e99f5baf45b7ef7b3fc9019
ms.lasthandoff: 02/22/2017

---
# <a name="dependency-diagrams-guidelines"></a>Diagramas de dependência: diretrizes
Descrever a arquitetura do seu aplicativo em um nível alto, criando *diagramas de dependência* no Visual Studio. Certifique-se de que o código permaneça consistente com esse design, validando seu código com um diagrama de dependência. Você também pode incluir validação da camada no processo de compilação. Consulte [vídeo do Channel 9: Design e validar a arquitetura usando diagramas de dependência](http://go.microsoft.com/fwlink/?LinkID=252073).  
  
 Para ver quais versões do Visual Studio oferecer suporte a esse recurso, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="what-is-a-dependency-diagram"></a>O que é um diagrama de dependência?  
 Como um diagrama de arquitetura tradicional, um diagrama de dependência identifica os principais componentes ou unidades funcionais de design e suas interdependências. Cada nó no diagrama, chamado um *camada*, representa um grupo lógico de namespaces, projetos ou outros artefatos. Você pode desenhar as dependências que devem existir em seu design. Ao contrário de um diagrama de arquitetura tradicional, você pode verificar que as dependências reais no código-fonte está de acordo com as dependências pretendidas que você especificou. Fazendo parte de validação de uma compilação regular na [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)], você pode garantir que o código do programa continua a aderem à arquitetura do sistema por meio de alterações futuras. Consulte [diagramas de dependência: referência](../modeling/layer-diagrams-reference.md).  
  
##  <a name="a-nameupdatea-how-to-design-or-update-your-app-with-dependency-diagrams"></a><a name="Update"></a>Como criar ou atualizar seu aplicativo com diagramas de dependência  
 As etapas a seguir fornecem uma visão geral de como usar diagramas de dependência dentro do processo de desenvolvimento. As seções posteriores deste tópico descrevem mais detalhes sobre cada etapa. Se você estiver desenvolvendo um novo design, omita as etapas que se referem ao código existente.  
  
> [!NOTE]
>  Essas etapas aparecem na ordem aproximada. Você provavelmente desejará se sobrepor as tarefas, reordená-las de acordo com sua própria situação e visitá-las no início de cada iteração em seu projeto.  
  
1.  [Criar um diagrama de dependência](#Create) para o aplicativo inteiro ou para uma camada dentro dele.  
  
2.  [Definir camadas para representar componentes ou áreas funcionais principais](#CreateLayers) do seu aplicativo. Nomeie essas camadas de acordo com sua função, por exemplo, "Apresentação" ou "Serviços". Se você tiver um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução, você pode associar cada camada com uma coleção de *artefatos*, como namespaces, projetos, arquivos e assim por diante.  
  
3.  [Descobrir as dependências existentes](#Generate) entre camadas.  
  
4.  [Editar camadas e dependências](#EditArchitecture) para mostrar a atualização que você deseja que o código para refletir de design.  
  
5.  [Criar novas áreas do seu aplicativo](#NewAreas) criar camadas para representar os componentes ou blocos de arquiteturas principais e definindo as dependências para mostrar como cada camada usa os outros.  
  
6.  [Editar o layout e a aparência do diagrama](#EditLayout) para ajudá-lo a discutir isso com seus colegas.  
  
7.  [Valide o código no diagrama de dependência](#Validate) para realçar os conflitos entre o código e a arquitetura que você precisa.  
  
8.  [Atualizar o código de acordo com a nova arquitetura](#UpdateCode). Iterativamente desenvolver e refatorar o código até que a validação não mostra nenhum conflito.  
  
9. [Incluir validação de camada no processo de compilação](#BuildValidation) para garantir que o código continua de acordo com seu design.  
  
##  <a name="a-namecreatea-create-a-dependency-diagram"></a><a name="Create"></a>Criar um diagrama de dependência  
 Um diagrama de dependência deve ser criado dentro de um projeto de modelagem. Você pode adicionar um novo diagrama de dependência para um projeto de modelagem existente, crie um novo projeto de modelagem para o diagrama de dependência ou copie um diagrama de dependência existente dentro do mesmo projeto de modelagem.  
  
> [!IMPORTANT]
>  Não adicione, arraste ou copie um diagrama de dependência existente de um projeto de modelagem a outro projeto de modelagem ou em outro local na solução. Um diagrama de dependência é copiado dessa maneira terá as mesmas referências do diagrama original, mesmo se você modificar o diagrama. Isso impedirá a validação da camada funcione corretamente e pode causar outros problemas, como elementos ausentes ou outros erros ao tentar abrir o diagrama.  
  
 Consulte [criar diagramas de dependência de seu código](../modeling/create-layer-diagrams-from-your-code.md).  
  
##  <a name="a-namecreatelayersa-define-layers-to-represent-functional-areas-or-components"></a><a name="CreateLayers"></a>Definir camadas para representar componentes ou áreas funcionais  
 Camadas representam grupos lógicos de *artefatos*, como projetos, arquivos de código, namespaces, classes e métodos. Você pode criar camadas de artefatos de projetos do Visual c# .NET e Visual Basic .NET, ou você pode anexar especificações ou planos para uma camada vinculando documentos como arquivos do Word ou apresentações do PowerPoint. Cada camada aparece como um retângulo no diagrama e mostra o número de artefatos que estão vinculados a ele. Uma camada pode conter camadas aninhadas que descrevem as tarefas mais específicas.  
  
 Como diretriz geral, camadas de nome de acordo com a sua função, por exemplo, "Apresentação" ou "Serviços". Se os artefatos estão estreitamente interdependentes, colocá-los na mesma camada. Se os artefatos podem ser atualizados separadamente ou usados em aplicativos separados, colocá-los em diferentes camadas. Para saber mais sobre os padrões de camadas, visite o site Patterns Practices < / em [http://go.microsoft.com/fwlink/?LinkId=145794](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
> [!TIP]
>  Há determinados tipos de artefatos que você pode vincular a camadas, mas que não oferecem suporte a validação contra o diagrama de dependência. Para ver se o artefato dá suporte à validação, abra **Gerenciador de camadas** para examinar o **dá suporte à validação** propriedades do link de artefato. Consulte [descobrir dependências existentes entre camadas](#Generate).  
  
 Ao atualizar um aplicativo desconhecido, você também pode criar mapas de código. Esses diagramas podem ajudá-lo a descobrir padrões e dependências enquanto você explora o código. Use o Gerenciador de soluções para explorar namespaces e classes, que normalmente correspondem bem a camadas existentes. Atribua esses artefatos de código em camadas arrastando-os no Gerenciador de soluções para diagramas de dependência. Você pode usar diagramas de dependência para ajudá-lo a atualizar o código e mantê-los consistentes com o design.  
  
 Consulte:  
  
-   [Crie diagramas de dependência de seu código](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Usar mapas de códigos para depurar aplicativos](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)  
  
##  <a name="a-namegeneratea-discover-existing-dependencies-between-layers"></a><a name="Generate"></a>Descobrir dependências existentes entre camadas  
 Existirá uma dependência sempre que um artefato associado a uma camada tiver uma referência a um artefato associado a outra camada. Por exemplo, uma classe em uma camada declara uma variável que tem uma classe em outra camada. Você pode descobrir dependências existentes com a engenharia reversa-los.  
  
> [!NOTE]
>  As dependências não podem sofrer engenharia reversa para determinados tipos de artefatos. Por exemplo, nenhuma dependência sofrerá engenharia reversa de ou para uma camada vinculada a um arquivo de texto. Para ver quais artefatos têm dependências que você pode fazer engenharia reversa, clique uma ou várias camadas e, em seguida, clique em **Exibir Links**. Em **Gerenciador de camadas**, examine o **dá suporte à validação** coluna. As dependências não sofrerão engenharia reversa para artefatos para o qual essa coluna mostra **False**.  
  
#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Para efetuar engenharia reversa de dependências existentes entre camadas  
  
-   Selecione uma camada ou várias camadas, clique em uma camada selecionada e, em seguida, clique em **gerar dependências**.  
  
 Normalmente, você verá algumas dependências que não devem existir. É possível editar essas dependências para alinhá-las com o design desejado.  
  
##  <a name="a-nameeditarchitecturea-edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditArchitecture"></a>Editar camadas e dependências para mostrar o design desejado  
 Para descrever as alterações que você planeja fazer a arquitetura pretendida ou do sistema, use as etapas a seguir para editar o diagrama de dependência. Você também pode fazer algumas alterações de refatoração para melhorar a estrutura do código antes de estendê-lo. Consulte [melhorando a estrutura do código](#Improving).  
  
|**Para**|**Execute estas etapas**|  
|------------|-----------------------------|  
|Excluir uma dependência que não deve existir|Clique na dependência e então pressione **excluir**.|  
|Alterar ou restringir a direção de uma dependência|Definir seu **direção** propriedade.|  
|Criar novas dependências|Use o **dependência** e **dependência bidirecional** ferramentas.<br /><br /> Para desenhar várias dependências, clique duas vezes na ferramenta. Quando tiver terminado, clique o **ponteiro** ferramenta ou pressione a **ESC** chave.|  
|Especificar que os artefatos associados a uma camada não dependem dos namespaces especificados|Digite os namespaces na camada de **dependências de Namespace proibido** propriedade. Use um ponto e vírgula (**;**) para separar os namespaces.|  
|Especificar que os artefatos associados a uma camada não devem pertencer aos namespaces especificados|Digite os namespaces na camada de **Namespaces proibidos** propriedade. Use um ponto e vírgula (**;**) para separar os namespaces.|  
|Especificar que os artefatos associados a uma camada devem pertencer a um dos namespaces especificados|Digite o namespace na camada de **Namespaces obrigatórios** propriedade. Use um ponto e vírgula (**;**) para separar os namespaces.|  
  
###  <a name="a-nameimprovinga-improving-the-structure-of-the-code"></a><a name="Improving"></a>Melhorando a estrutura do código  
 As alterações de refatoração são os aprimoramentos que não afetam o comportamento do aplicativo, mas ajuda a tornar o código mais fácil de alterar e estender no futuro. Código bem estruturado tem um design que seja fácil de abstrair a um diagrama de dependência.  
  
 Por exemplo, se você criar uma camada para cada namespace no código e, em seguida, fazer engenharia reversa de dependências, deve haver um conjunto mínimo de dependências unidirecionais entre as camadas. Se você criar um diagrama mais detalhado usando classes ou métodos como as camadas, o resultado também deve ter as mesmas características.  
  
 Se esse não for o caso, o código será mais difícil alterar ao longo do tempo e menos adequado para validação usando diagramas de dependência.  
  
##  <a name="a-namenewareasa-design-new-areas-of-your-application"></a><a name="NewAreas"></a>Novas áreas de design do seu aplicativo  
 Ao iniciar o desenvolvimento de um novo projeto, ou uma nova área em um novo projeto, você pode desenhar camadas e dependências para ajudar a identificar os principais componentes antes de começar a desenvolver o código.  
  
-   **Mostrar os padrões de arquiteturas identificação** nos diagramas de dependência, se possível. Por exemplo, um diagrama de dependência que descreve um aplicativo de área de trabalho pode incluir camadas como apresentação, lógica de domínio e armazenamento de dados. Um diagrama de dependência que aborda um recurso único dentro de um aplicativo pode ter camadas como modelo, o modo de exibição e o controlador. Para obter mais informações sobre esses padrões, consulte [práticas de < / padrões: arquitetura de aplicativo](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
     Se você costuma cria padrões semelhantes, crie uma ferramenta personalizada. Consulte [definir um personalizado item da caixa de ferramentas de modelagem](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
-   **Criar um artefato de código para cada camada** como um namespace, classe ou componente. Isso torna mais fácil de seguir o código e vincular os artefatos de código em camadas. Assim que você cria cada artefato, vincule-o à camada apropriada.  
  
-   **Você não precisa vincular a maioria das classes e outros artefatos a camadas** porque elas se encaixam em artefatos maiores, como namespaces que você já tiver vinculado a camadas.  
  
-   **Criar um novo diagrama para um novo recurso**. Normalmente, haverá um ou mais diagramas de dependência que descreve o aplicativo inteiro. Se você estiver criando um novo recurso dentro do aplicativo, não adicionar ou alterar os diagramas existentes. Em vez disso, crie seu próprio diagrama que reflete as novas partes do código. As camadas no novo diagrama podem incluir apresentação, lógica de domínio e as camadas de banco de dados para o novo recurso.  
  
     Quando você compila o aplicativo, seu código será validado tanto contra o diagrama como um todo e seu diagrama mais detalhado do recurso.  
  
##  <a name="a-nameeditlayouta-edit-the-layout-for-presentation-and-discussion"></a><a name="EditLayout"></a>Editar o layout de apresentação e discussão  
 Para ajudar a identificar as camadas e dependências ou discuti-las com os membros da equipe, edite a aparência e o layout do diagrama das seguintes maneiras:  
  
-   Altere formas, tamanhos e posições das camadas.  
  
-   Altere as cores de camadas e dependências.  
  
    -   Selecione uma ou mais camadas ou dependências, com o botão direito e clique **propriedades**. No **propriedades** janela, edite o **cor** propriedade.  
  
##  <a name="a-namevalidatea-validate-the-code-against-the-diagram"></a><a name="Validate"></a>Valide o código no diagrama  
 Quando você tiver editado o diagrama, você pode validá-lo contra o código manualmente a qualquer momento ou automaticamente toda vez que você executar uma compilação local ou [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)].  
  
 Consulte:  
  
-   [Validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)  
  
-   [Incluir validação de camada no processo de compilação](#BuildValidation)  
  
##  <a name="a-nameupdatecodea-update-the-code-to-conform-to-the-new-architecture"></a><a name="UpdateCode"></a>O código de acordo com a nova arquitetura de atualização  
 Normalmente, os erros serão exibidos na primeira vez que você valida o código em um diagrama de dependência atualizado. Esses erros podem ter várias causas:  
  
-   Um artefato é atribuído à camada errada. Nesse caso, mova o artefato.  
  
-   Um artefato como, por exemplo, uma classe usa outra classe de maneira a entrar em conflito com a arquitetura. Nesse caso, refatore o código para remover a dependência.  
  
 Para resolver esses erros, atualize o código até que mais nenhum erro seja exibido durante a validação. Isso geralmente é um processo iterativo. Para obter mais informações sobre esses erros, consulte [Validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md).  
  
> [!NOTE]
>  Ao desenvolver ou refatorar o código, você pode ter novos artefatos para vincular ao diagrama de dependência. No entanto, isso talvez não seja necessário, por exemplo, quando você tem camadas que representam os namespaces existentes e o novo código só adiciona mais material para esses namespaces.  
  
 Durante o processo de desenvolvimento, você talvez queira suprimir alguns dos conflitos reportados durante a validação. Por exemplo, você talvez queira suprimir erros que já esteja resolvendo ou que não sejam relevantes para seu cenário específico. Quando você suprime um erro, é uma prática recomendada registrar em log um item de trabalho em [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]. Para executar essa tarefa, consulte [Validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md).  
  
##  <a name="a-namebuildvalidationa-include-layer-validation-in-the-build-process"></a><a name="BuildValidation"></a>Incluir validação de camada no processo de compilação  
 Para garantir que as alterações futuras no código em conformidade com os diagramas de dependência, incluem a validação de camada ao processo de compilação padrão da sua solução. Sempre que outros membros da equipe compilar a solução, as diferenças entre as dependências no código e o diagrama de dependência serão relatadas como erros de compilação. Para obter mais informações sobre como incluir validação da camada no processo de compilação, consulte [Validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md).  
  
## <a name="see-also"></a>Consulte também  
 [Diagramas de dependência: referência](../modeling/layer-diagrams-reference.md)   
 [Crie diagramas de dependência de seu código](../modeling/create-layer-diagrams-from-your-code.md)

