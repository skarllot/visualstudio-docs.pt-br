---
title: "Validar o código com diagramas de dependência | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, validating
- validation, dependency diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, dependency diagrams
- MSBuild, validating code
ms.assetid: 70cbe55d-4b33-4355-b0a7-88c770a6f75c
caps.latest.revision: 82
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
ms.sourcegitcommit: 5581224b17a7b42f65b69f741f984a144d78fc26
ms.openlocfilehash: 53c623ce7ab7126c22aaab856a439862252a5d56
ms.lasthandoff: 04/04/2017

---
# <a name="validate-code-with-dependency-diagrams"></a>Validar o código com diagramas de dependência

**Últimas notícias**: consulte [esta postagem de blog](https://blogs.msdn.microsoft.com/visualstudioalm/2016/11/30/live-dependency-validation-in-visual-studio-2017/).

[Vídeo: Validar suas dependências de arquitetura em tempo real](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4) 

## <a name="why-use-dependency-diagrams"></a>Por que usar diagramas de dependência?

Para certificar-se de que o código não causa conflito com seu design, valide seu código com diagramas de dependência no Visual Studio. Isso pode ajudar a:  
  
-   Encontre conflitos entre as dependências em seu código e o diagrama de dependência.  
  
-   Encontre dependências que talvez sejam afetadas por alterações propostas.  
  
     Por exemplo, você pode editar o diagrama de dependência para mostrar possíveis alterações de arquitetura e, em seguida, validar o código para ver as dependências afetadas.  
  
-   Refatore ou migre o código para um design diferente.  
  
     Encontre o código ou as dependências que exijam trabalho quando você move o código para uma arquitetura diferente.  
  
 **Requisitos**  
  
-   Visual Studio  
  
-   Visual Studio em seu servidor do Team Foundation Build para validar o código automaticamente com o Team Foundation Build  
  
-   Uma solução que tem um projeto de modelagem com um diagrama de dependência. Este diagrama de dependência deve ser vinculado aos artefatos em projetos do Visual c# .NET ou Visual Basic .NET que você deseja validar. Consulte [criar diagramas de dependência do seu código](../modeling/create-layer-diagrams-from-your-code.md).  
  
 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Você pode validar o código manualmente a partir de um diagrama de dependência aberto no Visual Studio ou em um prompt de comando. Também é possível validar o código automaticamente durante a execução de compilações locais ou do Team Foundation Build. Consulte [vídeo do Channel 9: Design e validar sua arquitetura usando diagramas de dependência](http://go.microsoft.com/fwlink/?LinkID=252073).  
  
> [!IMPORTANT]
>  Se você deseja executar a validação de camada com o Team Foundation Build, instale também a mesma versão do Visual Studio em seu servidor de compilação.  
  
-   [Se um item dá suporte a validação](#SupportsValidation)  
  
-   [Incluir outros assemblies .NET e projetos para validação](#IncludeReferences)  
  
-   [Validar o código manualmente](#ValidateManually)  
  
-   [Validar o código automaticamente](#ValidateAuto)  
  
-   [Solucionar problemas de validação de camada](#TroubleshootingValidation)  
  
-   [Compreender e resolver erros de validação de camada](#UnderstandingValidationErrors)  

## <a name="live-dependency-validation"></a>Validação de dependência dinâmica

Nesta versão do Visual Studio, ocorre a validação de dependência em tempo real e erros são mostrados imediatamente na janela lista de erros do Visual Studio.

* Há suporte para c# e Visual Basic.NET de validação em tempo real. 

* Para habilitar a análise de solução completa ao usar a validação de dependência em tempo real, abra as configurações de opções na barra de ouro que aparece na lista de erros. 
 - Você poderá ignorar permanentemente esta barra de ouro, se você não estiver interessado em ver todos os problemas de arquitetura em sua solução.
 - Se você não habilitar a análise de solução completa, a análise é feita apenas para os arquivos que está sendo editados.<p /> 

* Ao atualizar projetos para habilitar a validação em tempo real, uma caixa de diálogo mostra o andamento da conversão.

* Ao atualizar um projeto para validação de dependência em tempo real, a versão do pacote do NuGet é atualizada para ser o mesmo para todos os projetos e é a versão mais recente em uso. 

* Adicionando um novo gatilho de projeto de validação de dependência de uma atualização de projeto. 
  
##  <a name="SupportsValidation"></a>Se um item dá suporte a validação  
 É possível vincular camadas a sites, documentos do Office, arquivos de texto sem formatação e arquivos em projetos compartilhados entre vários aplicativos, mas o processo de validação não os incluirá. Os erros de validação não serão exibidos para referências a projetos ou assemblies vinculados a camadas separadas quando nenhuma dependência for exibida entre essas camadas. Essas referências não serão consideradas dependências, a menos que o código use essas referências.  
  
1.  No diagrama de dependência, selecione uma ou mais camadas, com o botão direito sua seleção e, em seguida, clique em **Exibir Links**.  
  
2.  Em **Explorer camada**, examine o **dá suporte à validação** coluna. Se o valor for falso, o item não dará suporte à validação.  
  
##  <a name="IncludeReferences"></a>Incluir outros assemblies .NET e projetos para validação  
 Quando você arrastar itens para o diagrama de dependência, referências a assemblies do .NET correspondentes ou projetos são adicionadas automaticamente para o **referências de camada** pasta do projeto de modelagem. Essa pasta contém referências aos assemblies e aos projetos analisados durante a validação. Você pode incluir outros assemblies .NET e projetos para validação sem manualmente arrastando-os para o diagrama de dependência.  
  
1.  Em **Solution Explorer**, com o botão direito do projeto de modelagem ou **referências de camada** pasta e clique **adicionar referência**.  
  
2.  No **adicionar referência** caixa de diálogo, selecione os assemblies ou projetos e, em seguida, clique em **Okey**.  
  
##  <a name="ValidateManually"></a>Validar o código manualmente  
 Se você tiver um diagrama de dependência aberto que está vinculado a itens de solução, você pode executar o **validar** comando de atalho do diagrama. Você também pode usar o prompt de comando para executar o **msbuild** com o **/p:ValidateArchitecture** propriedade personalizada definida como **True**. Por exemplo, à medida que fizer alterações no código, execute a validação da camada regularmente de forma que você possa capturar conflitos de dependência com antecedência.  
  
#### <a name="to-validate-code-from-an-open-dependency-diagram"></a>Para validar o código de um diagrama de dependência aberto   
  
1.  Clique com botão direito a superfície do diagrama e, em seguida, clique em **validar arquitetura**.  
  
    > [!NOTE]
    >  Por padrão, o **ação de compilação** no arquivo de diagrama (.layerdiagram) dependência estiver definida como **validar** para que o diagrama é incluído no processo de validação.  
  
     O **lista de erros** janela relata os erros que ocorrem. Para obter mais informações sobre erros de validação, consulte [compreender e resolver erros de validação de camada](#UnderstandingValidationErrors).  
  
2.  Para exibir a origem de cada erro, clique duas vezes o erro a **lista de erros** janela.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]pode mostrar um mapa de código ao invés da origem do erro. Isso ocorre quando o código tem uma dependência em um assembly que não for especificado, o diagrama de dependência ou o código está faltando uma dependência que é especificada pelo diagrama de dependência. Examine o mapa de códigos ou o código para determinar se a dependência deve existir. Para obter mais informações sobre mapas de códigos, consulte [mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md).  
  
3.  Para gerenciar erros, consulte [gerenciar erros de validação](#ManageErrors).  
  
#### <a name="to-validate-code-at-the-command-prompt"></a>Para validar o código no prompt de comando  
  
1.  Abra o prompt de comando do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Escolha uma das seguintes opções:  
  
    -   Para validar o código em um projeto de modelagem específico na solução, execute [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] com a propriedade personalizada a seguir.  
  
        ```  
        msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true  
        ```  
  
         - ou –  
  
         Navegue até a pasta que contém o modelo de arquivo (.modelproj) e o diagrama de dependência do projeto e, em seguida, execute [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] com a propriedade personalizada a seguir:  
  
        ```  
        msbuild /p:ValidateArchitecture=true   
        ```  
  
    -   Para validar o código em todos os projeto de modelagem na solução, execute [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] com a propriedade personalizada a seguir:  
  
        ```  
        msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true   
        ```  
  
         - ou –  
  
         Navegue até a pasta de solução, que deve conter um projeto de modelagem que contém um diagrama de dependência e, em seguida, executar [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] com a propriedade personalizada a seguir:  
  
        ```  
        msbuild /p:ValidateArchitecture=true  
        ```  
  
     Todos os erros ocorridos serão listados. Para obter mais informações sobre [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], consulte [MSBuild](../msbuild/msbuild.md) e [tarefa MSBuild](../msbuild/msbuild-task.md).  
  
 Para obter mais informações sobre erros de validação, consulte [compreender e resolver erros de validação de camada](#UnderstandingValidationErrors).  
  
###  <a name="ManageErrors"></a>Gerenciar erros de validação  
 Durante o processo de desenvolvimento, você talvez queira suprimir alguns dos conflitos reportados durante a validação. Por exemplo, você talvez queira suprimir erros que já esteja resolvendo ou que não sejam relevantes para seu cenário específico. Quando você suprime um erro, é uma prática recomendada registrar em log um item de trabalho em [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)].  
  
> [!WARNING]
>  Você já deve estar conectado ao TFS fonte código de controle (SCC) para criar ou vincular a um item de trabalho. Se você tentar abrir uma conexão em um SCC TFS diferentes, o Visual Studio fecha automaticamente a solução atual. Certifique-se de que você já está conectado ao SCC apropriado antes de tentar criar ou vincular a um item de trabalho. Em versões posteriores do Visual Studio, os comandos de menu não estão disponíveis se você não estiver conectado a um SCC.  
  
##### <a name="to-create-a-work-item-for-a-validation-error"></a>Para criar um item de trabalho para um erro de validação  
  
-   No **lista de erros** janela, clique duas vezes o erro, aponte para **Criar Item de trabalho**e, em seguida, clique no tipo de item de trabalho que você deseja criar.  
  
 Use essas tarefas para gerenciar erros de validação de **lista de erros** janela:  
  
|**To**|**Siga estas etapas**|  
|------------|----------------------------|  
|Suprimir erros selecionados durante a validação|Clique um ou vários erros selecionados, aponte para **gerenciar erros de validação**e, em seguida, clique em **suprimir erros**.<br /><br /> Os erros suprimidos são exibidos com formatação de tachado. Quando você executar a validação da próxima vez, esses erros não serão exibidos.<br /><br /> Erros suprimidos são rastreados em um arquivo de .suppressions para o arquivo de diagrama de dependência correspondente.|  
|Parar a supressão de erros selecionados|Clique no erro suprimidas selecionado ou erros, aponte para **gerenciar erros de validação**e, em seguida, clique em **parar suprimir erros**.<br /><br /> Os erros suprimidos selecionados serão exibidos quando você executar a validação na próxima vez.|  
|Restaurar suprimidos todos os erros no **lista de erros** janela|Clique em qualquer lugar no **lista de erros** janela, aponte para **gerenciar erros de validação**e, em seguida, clique em **Mostrar todos os erros suprimidos**.|  
|Ocultar suprimidos todos os erros do **lista de erros** janela|Clique em qualquer lugar no **lista de erros** janela, aponte para **gerenciar erros de validação**e, em seguida, clique em **ocultar todos os erros suprimidos**.|  
  
##  <a name="ValidateAuto"></a>Validar o código automaticamente  
 É possível executar a validação da camada sempre que você executa uma compilação local. Se a equipe usar o Team Foundation Build, será possível executar a validação da camada com check-ins restritos, que você pode especificar criando uma tarefa MSBuild personalizada, e usar relatórios de compilação para coletar erros de validação. Para criar construções de check-in restrito, consulte [usar um processo de build de check-in restrito para validar alterações](http://msdn.microsoft.com/Library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).  
  
#### <a name="to-validate-code-automatically-during-a-local-build"></a>Para validar automaticamente o código durante uma compilação local  
  
-   Use um editor de texto para abrir o arquivo do projeto de modelagem (.modelproj) e, em seguida, inclua a seguinte propriedade:  
  
```  
<ValidateArchitecture>true</ValidateArchitecture>  
```  
  
 \- ou -  
  
1.  Em **Solution Explorer**, com o botão direito do projeto de modelagem que contém o diagrama de dependência ou diagramas e, em seguida, clique em **propriedades**.  
  
2.  No **propriedades** janela, defina o projeto de modelagem **validar arquitetura** propriedade **True**.  
  
     Isso inclui o projeto de modelagem no processo de validação.  
  
3.  Em **Solution Explorer**, clique no arquivo de diagrama (.layerdiagram) de dependência que você deseja usar para validação.  
  
4.  No **propriedades** janela, certifique-se de que o diagrama **ação de compilação** está definida como **validar**.  
  
     Isso inclui o diagrama de dependência no processo de validação.  
  
 Para gerenciar erros na janela lista de erros, consulte [gerenciar erros de validação](#ManageErrors).  
  
#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Para validar automaticamente o código durante um Team Foundation Build  
  
1.  Em **Team Explorer**, clique duas vezes na definição de compilação e, em seguida, clique em **processo**.  
  
2.  Em **parâmetros de processo de compilação**, expanda **compilação**e digite o seguinte no **argumentos de MSBuild** parâmetro:  
  
     `/p:ValidateArchitecture=true`  
  
 Para obter mais informações sobre erros de validação, consulte [compreender e resolver erros de validação de camada](#UnderstandingValidationErrors). Para obter mais informações sobre [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)], consulte:  
  
-   [Compilar o aplicativo](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)  
  
-   [Use o modelo padrão para o processo de compilação](http://msdn.microsoft.com/Library/43930b12-c21b-4599-a980-2995e3d16e31)  
  
-   [Modificar um Build herdado que é baseado em UpgradeTemplate.xaml](http://msdn.microsoft.com/Library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)  
  
-   [Personalizar o modelo de processo de compilação](http://msdn.microsoft.com/Library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
-   [Monitore o andamento de uma compilação em execução](http://msdn.microsoft.com/Library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)  
  
##  <a name="TroubleshootingValidation"></a>Solucionar problemas de validação de camada  
 A tabela a seguir descreve problemas na validação da camada e sua resolução. Esses problemas são diferentes dos erros resultantes de conflitos entre o código e o design. Para obter mais informações sobre esses erros, consulte [compreender e resolver erros de validação de camada](#UnderstandingValidationErrors).  
  
|**Problema**|**Causa possível**|**Resolução**|  
|---------------|------------------------|--------------------|  
|Os erros de validação não ocorrem como esperado.|A validação não funciona em diagramas de dependência que são copiados de outros diagramas de dependência no Gerenciador de soluções e que estão no mesmo projeto de modelagem. diagramas de dependência são copiados dessa forma contêm as mesmas referências como o diagrama de dependência original.|Adicione um novo diagrama de dependência para o projeto de modelagem.<br /><br /> Copie os elementos do diagrama de dependência de origem para o novo diagrama.|  
  
##  <a name="UnderstandingValidationErrors"></a>Compreender e resolver erros de validação de camada  
 Quando validar o código em um diagrama de dependência, ocorrem erros de validação quando o código está em conflito com o design. Por exemplo, as seguintes condições podem fazer os erros de validação ocorrerem:  
  
-   Um artefato é atribuído à camada errada. Nesse caso, mova o artefato.  
  
-   Um artefato como, por exemplo, uma classe usa outra classe de maneira a entrar em conflito com a arquitetura. Nesse caso, refatore o código para remover a dependência.  
  
 Para resolver esses erros, atualize o código até que mais nenhum erro seja exibido durante a validação. É possível realizar essa tarefa de maneira iterativa.  
  
 A seção a seguir descreve a sintaxe usada nesses erros, explica o significado desses erros e sugere o que é possível fazer para o resolver ou gerenciá-los.  
  
|**Sintaxe**|**Descrição**|  
|----------------|---------------------|  
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* é um artefato que está associado uma camada no diagrama de dependência.<br /><br /> *ArtifactTypeN* é o tipo de *ArtifactN*, como um **classe** ou **método**, por exemplo:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|  
|*NamespaceNameN*|O nome de um namespace.|  
|*LayerNameN*|O nome de uma camada no diagrama de dependência.|  
|*DependencyType*|O tipo de relação de dependência entre *Artifact1* e *Artifact2*. Por exemplo, *Artifact1* tem um **chamadas** relação com *Artifact2*.|  
  
|**Erro de sintaxe**|**Descrição do erro**|  
|----------------------|---------------------------|  
|DV0001: **dependência inválida**|Esse problema é relatado quando um elemento de código (namespace, tipo, membro) mapeada para um referências de camada um elemento de código mapeado para outra camada, mas não há nenhuma seta de dependência entre essas camadas no diagrama de validação de dependência que contém este camadas. Essa é uma violação de restrição de dependência.|  
|DV1001: **nome de namespace inválido**|Esse problema é relatado em um elemento de código associado a uma camada que a propriedade "Permitidos em nomes de Namespace" não contém o namespace no qual esse elemento de código é definido. Isso é uma violação de restrição de nomenclatura. Observe que a sintaxe de "Permitidos em nomes de Namespace" deve ser uma lista de ponto e vírgula de namespaces na qual o código elementos associados são camada tem permissão para ser definido.|  
|DV1002: **dependência no namespace unreferenceable**|Esse problema é relatado em um elemento de código associado a uma camada e fazendo referência a outro elemento de código definido em um namespace que é definido na propriedade "Namespace Unreferenceable" da camada. Isso é uma violação de restrição de nomenclatura. Observe que a propriedade "Unreferenceable Namespaces" é definida como uma lista de ponto e vírgula separada de namespaces que não devem ser referenciadas em elementos de código associados a essa camada.|  
|DV1003: **nome do namespace não permitido**|Esse problema é relatado em um elemento de código associado a uma camada que a propriedade "Nomes de Namespace não permitido" contém o namespace no qual esse elemento de código é definido. Isso é uma violação de restrição de nomenclatura. Observe que a propriedade "Nome do namespace não permitido" é definida como uma lista de ponto e vírgula separada de namespaces na qual o código elementos associados a essa camada não devem ser definidos.|  
|DV3001: **Link ausente**|Camada '*LayerName*'contém links para'*artefato*' que não foi encontrado. Você não tem uma referência de assembly?|*LayerName* links para um artefato que não pode ser encontrado. Por exemplo, um link para uma classe talvez não seja encontrado porque o projeto de modelagem não tem uma referência para o assembly que contém a classe.|  
|DV9001: **análise de arquitetura encontro erros internos**|Os resultados talvez não estejam completos. Para obter mais informações, consulte o log de eventos da compilação detalhado ou a janela de saída.|Consulte o log de eventos da compilação ou a janela de saída para obter mais detalhes.|  

 
## <a name="see-also"></a>Consulte também  
 [Validar o sistema durante o desenvolvimento](../modeling/validate-your-system-during-development.md)   
 [Vídeo: Validar suas dependências de arquitetura em tempo real](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)   

