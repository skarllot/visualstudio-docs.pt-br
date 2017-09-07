---
title: "Adicionar validação de arquitetura personalizada a diagramas de dependência | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, adding custom validation
ms.assetid: fed7bc08-295a-46d6-9fd8-fb537f1f75f1
caps.latest.revision: 42
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 25261e06fc2d5ef1d2850b8ecdf159b1085d8d83
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="add-custom-architecture-validation-to-dependency-diagrams"></a>Adicionar validação de arquitetura personalizada a diagramas de dependência
No Visual Studio, os usuários podem validar o código-fonte em um projeto em um modelo de camada para que ele podem verificar se o código-fonte está em conformidade com as dependências em um diagrama de dependência. Há um algoritmo de validação padrão, mas você pode definir suas próprias extensões de validação.  
  
 Quando o usuário seleciona o **validar arquitetura** comando em um diagrama de dependência, o método de validação padrão é chamado, seguido por quaisquer extensões de validação que foram instalados.  
  
> [!NOTE]
>  Em um diagrama de dependência, o principal objetivo da validação é comparar o diagrama com o código de programa em outras partes da solução.  
  
 Você pode empacotar sua extensão de validação de camada em um Visual Studio Integration extensão (VSIX), que você pode distribuir para outros usuários do Visual Studio. Você pode colocar o validador um VSIX sozinho ou combiná-los no mesmo VSIX como outras extensões. Você deve escrever o código do validador em seu próprio projeto do Visual Studio, não no mesmo projeto como outras extensões.  
  
> [!WARNING]
>  Depois de você ter criado um projeto de validação, copie o [código de exemplo](#example) no final deste tópico e edite que suas próprias necessidades.  
  
## <a name="requirements"></a>Requisitos  
 Consulte [requisitos](../modeling/extend-layer-diagrams.md#prereqs).  
  
## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Definindo um validador de camada em um novo VSIX  
 O método mais rápido de criar um validador é usar o modelo de projeto. Isso coloca o código e o manifesto do VSIX no mesmo projeto.  
  
#### <a name="to-define-an-extension-by-using-a-project-template"></a>Para definir uma extensão usando um modelo de projeto  
  
1.  Criar um projeto em uma nova solução, usando o **novo projeto** comando o **arquivo** menu.  
  
2.  No **novo projeto** caixa de diálogo **projetos de modelagem**, selecione **extensão de validação do Designer de camada**.  
  
     O modelo cria um projeto que contém um exemplo pequeno.  
  
    > [!WARNING]
    >  Modelo makethe funcione corretamente:  
    >   
    >  -   Editar chamadas para `LogValidationError` para remover os argumentos opcionais `errorSourceNodes` e `errorTargetNodes`.  
    > -   Se você usar as propriedades personalizadas, aplique a atualização mencionada na [adicionar propriedades personalizadas a diagramas de dependência](../modeling/add-custom-properties-to-layer-diagrams.md).  
  
3.  Edite o código para definir a validação. Para obter mais informações, consulte [programação validação](#programming).  
  
4.  Para testar a extensão, consulte [validação de camada de depuração](#debugging).  
  
    > [!NOTE]
    >  O método será chamado apenas em determinadas circunstâncias, e os pontos de interrupção não funcionará automaticamente. Para obter mais informações, consulte [validação de camada de depuração](#debugging).  
  
5.  Para instalar a extensão na instância principal do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ou em outro computador, localize o **.vsix** arquivo **bin\\\***. Copie-o para o computador onde você deseja instalá-lo e, em seguida, clique duas vezes nele. Para desinstalá-lo, use **extensões e atualizações** no **ferramentas** menu.  
  
## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Adicionando um validador de camada para um VSIX separado  
 Se você quiser criar um VSIX que contém os validadores de camada, comandos e outras extensões, é recomendável que você crie um projeto para definir o VSIX e projetos separados para os manipuladores. 
  
#### <a name="to-add-layer-validation-to-a-separate-vsix"></a>Adicionar validação de camada para um VSIX separado  
  
1.  Crie um projeto de biblioteca de classes em uma solução do Visual Studio nova ou existente. No **novo projeto** caixa de diálogo, clique em **Visual C#** e, em seguida, clique em **biblioteca de classes**. Este projeto contém a classe de validação de camada.  
  
2.  Identifique ou crie um projeto do VSIX em sua solução. Um projeto do VSIX contém um arquivo chamado **source.extension.vsixmanifest**. Se você precisar adicionar um projeto VSIX, siga estas etapas:  
  
    1.  No **novo projeto** caixa de diálogo caixa, escolha **Visual C#**, **extensibilidade**, **projeto VSIX**.  
  
    2.  Em **Solution Explorer**, no menu de atalho do projeto VSIX, **definir como projeto de inicialização**.  
  
3.  Em **source.extension.vsixmanifest**, em **ativos**, adicione o projeto de validação de camada como um componente MEF:  
  
    1.  Escolha **novo**.  
  
    2.  No **adicionar novo ativo** caixa de diálogo, defina:  
  
         **Tipo** = **Microsoft.VisualStudio.MefComponent**  
  
         **Origem** = **um projeto na solução atual**  
  
         **Projeto** = *seu projeto de validador*  
  
4.  Você também deve adicioná-lo como uma validação de camada:  
  
    1.  Escolha **novo**.  
  
    2.  No **adicionar novo ativo** caixa de diálogo, defina:  
  
         **Tipo** = **Microsoft.VisualStudio.ArchitectureTools.Layer.Validator**. Isso não é uma das opções na lista suspensa. Você deve inseri-lo do teclado.  
  
         **Origem** = **um projeto na solução atual**  
  
         **Projeto** = *seu projeto de validador*  
  
5.  Retornar para o projeto de validação de camada e, em seguida, adicione as seguintes referências de projeto:  
  
    |**Referência**|**O que isso permite que você faça**|  
    |-------------------|------------------------------------|  
    |Microsoft.VisualStudio.GraphModel.dll|Ler o gráfico de arquitetura|  
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|Ler que o código DOM associado com camadas|  
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Ler o modelo de camada|  
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Ler e atualizar formas e diagramas.|  
    |System.ComponentModel.Composition|Definir o componente de validação usando Managed Extensibility Framework (MEF)|  
    |Microsoft.VisualStudio.Modeling.Sdk. [versão]|Definir as extensões de modelagem|  
  
6.  Copie o código de exemplo no final deste tópico para o arquivo de classe no projeto de biblioteca de validador para conter o código para a validação. Para obter mais informações, consulte [programação validação](#programming).  
  
7.  Para testar a extensão, consulte [validação de camada de depuração](#debugging).  
  
    > [!NOTE]
    >  O método será chamado apenas em determinadas circunstâncias, e os pontos de interrupção não funcionará automaticamente. Para obter mais informações, consulte [validação de camada de depuração](#debugging).  
  
8.  Para instalar o VSIX na instância principal do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ou em outro computador, localize o **.vsix** arquivo o **bin** diretório do projeto VSIX. Copie-o para o computador onde você deseja instalar o VSIX. Clique duas vezes no arquivo VSIX no Windows Explorer. (Explorador de arquivos no Windows 8).  
  
     Para desinstalá-lo, use **extensões e atualizações** no **ferramentas** menu.  
  
##  <a name="programming"></a>Validação de programação  
 Para definir uma extensão de validação de camada, você define uma classe que tem as seguintes características:  
  
-   A forma geral da declaração é a seguinte:  
  
    ```  
  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;  
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
    using Microsoft.VisualStudio.GraphModel;  
    ...  
     [Export(typeof(IValidateArchitectureExtension))]  
      public partial class Validator1Extension :  
                      IValidateArchitectureExtension  
      {  
        public void ValidateArchitecture(Graph graph)  
        {  
           GraphSchema schema = graph.DocumentSchema;  
          ...  
      } }  
    ```  
  
-   Quando você descobrir um erro, você pode relatá-lo usando `LogValidationError()`.  
  
    > [!WARNING]
    >  Não use os parâmetros opcionais de `LogValidationError`.  
  
 Quando o usuário chama o **validar arquitetura** menu de comando, o sistema de tempo de execução de camada analisa as camadas e seus artefatos para produzir um gráfico. O gráfico não tem quatro partes:  
  
-   Os modelos de camada do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução são representados como nós e links no gráfico.  
  
-   O código, itens de projeto e outros artefatos que são definidos na solução e são representados como nós e links que representam as dependências descobertas pelo processo de análise.  
  
-   Links de nós de camada para os nós de artefato de código.  
  
-   Nós que representam erros descobertos pelo validador.  
  
 Quando o gráfico foi construído, é chamado o método de validação padrão. Quando isso for concluído, qualquer método de validação de extensão instalada é chamado em ordem não especificada. O gráfico é passado para cada `ValidateArchitecture` método, que pode verificar o gráfico e relatam erros que encontrar.  
  
> [!NOTE]
>  Isso não é o mesmo que o processo de validação que pode ser usado em linguagens específicas de domínio.  
  
 Métodos de validação não devem alterar o modelo de camada ou o código que está sendo validado.  
  
 O modelo de gráfico é definido em <xref:Microsoft.VisualStudio.GraphModel>. Suas classes de entidade são <xref:Microsoft.VisualStudio.GraphModel.GraphNode> e <xref:Microsoft.VisualStudio.GraphModel.GraphLink>.  
  
 Cada nó e cada Link tem uma ou mais categorias que especificam o tipo de elemento ou relação que ele representa. Os nós de um gráfico típico têm as seguintes categorias:  
  
-   Dsl.LayerModel  
  
-   Dsl.Layer  
  
-   Dsl.Reference  
  
-   CodeSchema_Type  
  
-   CodeSchema_Namespace  
  
-   CodeSchema_Type  
  
-   CodeSchema_Method  
  
-   CodeSchema_Field  
  
-   CodeSchema_Property  
  
 Links de camadas para elementos no código apresentam a categoria "Representa".  
  
##  <a name="debugging"></a>Validação de depuração  
 Para depurar sua extensão de validação de camada, pressione CTRL + F5. Uma instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é aberto. Nesse caso, abra ou crie um modelo de camada. Esse modelo deve ser associado ao código e deve ter pelo menos uma dependência.  
  
### <a name="test-with-a-solution-that-contains-dependencies"></a>Teste com uma solução que contém as dependências  
 A validação não é executada, a menos que as seguintes características estão presentes:  
  
-   Há pelo menos um link de dependência no diagrama de dependência.  
  
-   Há camadas no modelo que estão associadas a elementos de código.  
  
 Na primeira vez que você inicia uma instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para testar sua extensão de validação, abra ou crie uma solução que tem as seguintes características.  
  
### <a name="run-clean-solution-before-validate-architecture"></a>Execução limpar solução antes de validar arquitetura  
 Sempre que você atualizar seu código de validação, use o **limpar solução** comando o **criar** menu na solução experimental, antes de você testar o comando de validação. Isso é necessário porque os resultados da validação são armazenados em cache. Se você não tiver atualizado o diagrama de dependência de teste ou em seu código, os métodos de validação não serão executados.  
  
### <a name="launch-the-debugger-explicitly"></a>Iniciar o depurador explicitamente  
 A validação é executada em um processo separado. Portanto, os pontos de interrupção em seu método de validação não serão disparados. Você deve anexar o depurador ao processo explicitamente quando a validação é iniciada.  
  
 Para anexar o depurador ao processo de validação, inserir uma chamada a `System.Diagnostics.Debugger.Launch()` no início de seu método de validação. Quando for exibida a caixa de diálogo de depuração, selecione a instância principal do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Como alternativa, você pode inserir uma chamada para `System.Windows.Forms.MessageBox.Show()`. Quando for exibida a caixa de mensagem, vá para a instância principal do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e na **depurar** menu clique **anexar ao processo**. Selecione o processo é denominado **Graphcmd.exe**.  
  
 Sempre iniciar a instância experimental pressionando CTRL + F5 (**iniciar sem depuração**).  
  
### <a name="deploying-a-validation-extension"></a>Implantando uma extensão de validação  
 Para instalar a extensão de validação em um computador em que uma versão adequada do Visual Studio está instalada, abra o arquivo VSIX no computador de destino. Para instalar em um computador no qual [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] é instalado, copie manualmente o conteúdo do VSIX para uma pasta de extensões. Para obter mais informações, consulte [implantar uma extensão de modelo de camada](../modeling/deploy-a-layer-model-extension.md).  
  
##  <a name="example"></a>Exemplo de código  
  
```csharp  
using System;  
using System.ComponentModel.Composition;  
using System.Globalization;  
using System.Linq;  
using System.Text.RegularExpressions;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
using Microsoft.VisualStudio.GraphModel;  
  
namespace Validator3  
{  
    [Export(typeof(IValidateArchitectureExtension))]  
    public partial class Validator3Extension : IValidateArchitectureExtension  
    {  
        /// <summary>  
        /// Validate the architecture  
        /// </summary>  
        /// <param name="graph">The graph</param>  
        public void ValidateArchitecture(Graph graph)  
        {  
            if (graph == null) throw new ArgumentNullException("graph");  
  
            // Uncomment the line below to debug this extension during validation  
            // System.Windows.Forms.MessageBox.Show("Attach 2 to GraphCmd.exe with process id " + System.Diagnostics.Process.GetCurrentProcess().Id);  
  
            // Get all layers on the diagram  
            foreach (GraphNode layer in graph.Nodes.GetByCategory("Dsl.Layer"))  
            {  
                System.Threading.Thread.Sleep(100);  
                // Get the required regex property from the layer node  
                string regexPattern = "^[a-zA-Z]+$"; //layer[customPropertyCategory] as string;  
                if (!string.IsNullOrEmpty(regexPattern))  
                {  
                    Regex regEx = new Regex(regexPattern);  
  
                    // Get all referenced types in this layer including those from nested layers so each  
                    // type is validated against all containing layer constraints.  
                    foreach (GraphNode containedType in layer.FindDescendants().Where(node => node.HasCategory("CodeSchema_Type")))  
                    {  
                        // Check the type name against the required regex                          
                        CodeGraphNodeIdBuilder builder = new CodeGraphNodeIdBuilder(containedType.Id, graph);  
                        string typeName = builder.Type.Name;  
                        if (!regEx.IsMatch(typeName))  
                        {  
                            // Log an error  
                            string message = string.Format(CultureInfo.CurrentCulture, Resources.InvalidTypeNameMessage, typeName);  
                            this.LogValidationError(graph, typeName + "TypeNameError", message, GraphErrorLevel.Error, layer);  
                        }  
                    }  
                }  
  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Estender diagramas de dependência](../modeling/extend-layer-diagrams.md)

