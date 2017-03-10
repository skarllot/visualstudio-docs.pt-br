---
title: "Integra&#231;&#227;o com o Visual Studio (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, resolução de referência"
  - "MSBuild, nomes de destino conhecidos"
  - "MSBuild, hospedagem"
  - "MSBuild, editando arquivos de projeto"
  - "MSBuild, integração do Visual Studio"
  - "MSBuild, IntelliSense"
  - "MSBuild, grupos de saída"
  - "MSBuild, compiladores em processo"
  - "MSBuild, execução de destino em tempo de design"
ms.assetid: 06cd6d7f-8dc1-4e49-8a72-cc9e331d7bca
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Integra&#231;&#227;o com o Visual Studio (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Hosts do Visual Studio [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para carregar e compilar projetos gerenciados. Porque [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] é responsável pelo projeto, quase qualquer projeto no [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] formato pode ser usado com êxito no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], mesmo que o projeto foi criado por uma ferramenta diferente e tem um processo de compilação.  
  
 Este tópico descreve os aspectos específicos do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] de hospedagem que deve ser considerado ao personalizar projetos e arquivos. targets que você deseja carregar e compilar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Isso irá ajudá\-lo a Certifique\-se de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] recursos como o IntelliSense e depuração de trabalho do seu projeto personalizado.  
  
 Para obter informações sobre projetos do C\+\+, consulte [Arquivos de projeto](/visual-cpp/ide/project-files).  
  
## Extensões de nome de arquivo de projeto  
 MSBuild.exe reconhece qualquer extensão de nome de arquivo de projeto correspondentes ao padrão. \* proj. No entanto, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] reconhece apenas um subconjunto dessas extensões de nome de arquivo de projeto, que determinam o sistema de projeto de linguagem específica que irá carregar o projeto.[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] não tem um idioma neutro [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] com base em sistema de projeto.  
  
 Por exemplo, o [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] sistema de projeto carrega os arquivos. csproj, mas [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] não é possível carregar um arquivo .xxproj. Um arquivo de projeto para arquivos de origem em uma linguagem arbitrário deve usar a mesma extensão [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] arquivos a serem carregados no projeto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Nomes de destino bem conhecidos  
 Clicar a **criar** do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] executará o destino padrão do projeto. Geralmente, esse destino também é denominado `Build`. Escolhendo o **recriar** ou **Limpar** comando tentará executar um destino de mesmo nome no projeto. Clicar em **publicar** executará um destino chamado `PublishOnly` no projeto.  
  
## Configurações e plataformas  
 As configurações são representadas no [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projetos por propriedades agrupadas em um `PropertyGroup` elemento que contém um `Condition` atributo.[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] examina essas condições para criar uma lista de plataformas para exibir e configurações de projeto. Para extrair com sucesso, essa lista, as condições devem ter um formato semelhante ao seguinte:  
  
```  
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "  
Condition=" '$(Configuration)' == 'Release' "   
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "  
```  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] examina as condições `PropertyGroup`, `ItemGroup`, `Import`, propriedade e elementos de item para essa finalidade.  
  
## Ações de compilação adicionais  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permite que você altere o nome do tipo de item de um arquivo em um projeto com o **Build Action** propriedade o [Propriedades de arquivo](http://msdn.microsoft.com/pt-br/013c4aed-08d6-4dce-a124-ca807ca08959) janela.`Compile`, `EmbeddedResource`, `Content`, e `None` nomes de tipo de item sempre são listados no menu, juntamente com quaisquer outros nomes de tipo de item já está em seu projeto. Para garantir que quaisquer nomes de tipo de item personalizado estão sempre disponíveis nesse menu, você pode adicionar o nome a um tipo de item chamado `AvailableItemName`. Por exemplo, adicionar o seguinte ao arquivo de projeto adicionará o tipo personalizado `JScript` para esse menu para todos os projetos que importá\-lo:  
  
```  
<ItemGroup>  
    <AvailableItemName Include="JScript"/>  
</ItemGroup>  
```  
  
> [!NOTE]
>  Alguns nomes de tipo de item são especiais para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mas não aparecer na lista suspensa.  
  
## Compiladores em processo  
 Quando possível, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tentará usar a versão no processo de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador para melhorar o desempenho. \(Não aplicável para [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].\) Para que isso funcione corretamente, as seguintes condições devem ser atendidas:  
  
-   Em um destino do projeto, deve haver uma tarefa chamada `Vbc` para [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projetos.  
  
-   O `UseHostCompilerIfAvailable` parâmetro da tarefa deve ser definido como true.  
  
## IntelliSense de tempo de design  
 Para obter suporte do IntelliSense em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] antes de uma compilação gerou um assembly de saída, as seguintes condições devem ser atendidas:  
  
-   Deve haver um destino chamado `Compile`.  
  
-   Tanto o `Compile` destino ou uma de suas dependências deve chamar a tarefa do compilador do projeto, como `Csc` ou `Vbc`.  
  
-   Tanto o `Compile` destino ou uma de suas dependências deve fazer com que o compilador receber todos os parâmetros necessários para IntelliSense, particularmente todas as referências.  
  
-   As condições listadas na seção "Compiladores em processo" devem ser atendidas.  
  
## Criando soluções  
 Em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], o arquivo de solução e a ordem de compilação de projeto são controladas por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] em si. Ao criar uma solução com msbuild.exe na linha de comando, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] analisa o arquivo de solução e ordena o projeto é compilado. Em ambos os casos os projetos são compilados individualmente em ordem de dependência e referências de projeto para projeto não são percorridas. Por outro lado, quando os projetos individuais criados com msbuild.exe, referências de projeto a projeto são percorridas.  
  
 Ao criar dentro de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], a propriedade `$(BuildingInsideVisualStudio)` está definida como `true`. Isso pode ser usado em seus arquivos de projeto ou. targets para fazer com que a compilação se comporte de maneira diferente.  
  
## Exibindo propriedades e itens  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] reconhece determinados nomes de propriedades e valores. Por exemplo, fará com que a propriedade a seguir em um projeto **Windows Application** apareçam no **tipo de aplicativo** caixa a **Project Designer**.  
  
```  
<OutputType>WinExe</OutputType>  
```  
  
 O valor da propriedade pode ser editado no **Project Designer** e salvas no arquivo de projeto. Se essa propriedade tem um valor inválido por edição manual, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] irá mostrar um aviso quando o projeto é carregado e substitua o valor inválido com um valor padrão.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Entenda os padrões para algumas propriedades. Essas propriedades não serão mantidas no arquivo de projeto, a menos que tenham valores não padrão.  
  
 Propriedades com nomes arbitrários não são exibidas no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para modificar propriedades arbitrárias em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], você deve abrir o arquivo de projeto no editor de XML e editá\-los manualmente. Para obter mais informações, consulte o [Editando arquivos de projeto no Visual Studio](#BKMK_EditingProjects) seção mais adiante neste tópico.  
  
 Itens definidos no projeto com nomes de tipo de item arbitrários são por padrão exibido no Gerenciador de soluções, sob o nó do projeto. Para ocultar um item da exibição, defina o `Visible` metadados para `false`. Por exemplo, o item a seguir farão parte do processo de compilação, mas não ser exibido no Solution Explorer.  
  
```  
<ItemGroup>  
    <IntermediateFile Include="cache.temp">  
        <Visible>false</Visible>  
    </IntermediateFile>  
</ItemGroup>  
```  
  
 Os itens declarados em arquivos importados para o projeto não são exibidos por padrão. Os itens criados durante o processo de compilação nunca são exibidos no Gerenciador de soluções.  
  
## Condições em itens e propriedades  
 Durante a compilação, todas as condições são respeitadas totalmente.  
  
 Ao determinar os valores de propriedade para exibir propriedades que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] considera depende da configuração são avaliadas de maneira diferente que propriedades considera configuração independente. Para propriedades considera configuração dependente, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] define o `Configuration` e `Platform` Propriedades adequadamente e instrui [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] a reavaliar o projeto. Para propriedades ele considera configuração independente, é indeterminado como condições serão avaliadas.  
  
 Expressões condicionais em itens são sempre ignoradas para fins de decidir se o item deve ser exibido no Gerenciador de soluções.  
  
## Depuração  
 Para localizar e iniciar o assembly de saída e anexar o depurador [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] precisa as propriedades `OutputPath`, `AssemblyName`, e `OutputType` definida corretamente. O depurador não conseguirá conectar\-se o processo de compilação não com que o compilador gerar um arquivo. PDB.  
  
## Execução de destino em tempo de design  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tenta executar destinos com determinados nomes quando ele carrega um projeto. Esses destinos incluem `Compile`, `ResolveAssemblyReferences`, `ResolveCOMReferences`, `GetFrameworkPaths`, e `CopyRunEnvironmentFiles`.[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] executa esses destinos que o compilador pode ser inicializado para fornecer o IntelliSense, o depurador pode ser inicializado e referências exibidas no Gerenciador de soluções podem ser resolvidas. Se esses destinos não estiverem presentes, o projeto carregará e compilar corretamente, mas a experiência de tempo de design no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] não será totalmente funcional.  
  
##  <a name="BKMK_EditingProjects"></a> Editando arquivos de projeto no Visual Studio  
 Para editar um [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] diretamente do projeto, você pode abrir o arquivo de projeto no editor de XML do Visual Studio.  
  
#### Para descarregar e editar um arquivo de projeto no Visual Studio  
  
1.  Em **Solution Explorer**, abra o menu de atalho do projeto e escolha **Descarregar projeto**.  
  
     O projeto está marcado **\(não disponível\)**.  
  
2.  Em **Solution Explorer**, abra o menu de atalho para o projeto não está disponível e, em seguida, escolha **Editar \< arquivo de projeto \>**.  
  
     O arquivo de projeto é aberto no Editor de XML do Visual Studio.  
  
3.  Editar, salvar e feche o arquivo de projeto.  
  
4.  Em **Solution Explorer**, abra o menu de atalho para o projeto não está disponível e, em seguida, escolha **Recarregar projeto**.  
  
## IntelliSense e validação  
 Ao usar o editor XML para editar arquivos de projeto, o IntelliSense e validação são controlados pelo [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] arquivos de esquema. Elas são instaladas no cache do esquema, que pode ser encontrado em *\< diretório de instalação do Visual Studio \>*\\Xml\\Schemas\\1033\\MSBuild.  
  
 O núcleo [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] tipos são definidos em Microsoft.Build.Core.xsd e tipos comuns usados por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] são definidos em Microsoft.Build.CommonTypes.xsd. Para personalizar os esquemas para que você tenha o IntelliSense e validação de nomes de tipo de item personalizado, propriedades e tarefas, você pode editar Microsoft.Build.xsd ou criar seu próprio esquema que inclua os esquemas CommonTypes ou principal. Se você criar seu próprio esquema, será necessário direcionar o XML editor para localizá\-lo usando o **propriedades** janela.  
  
## Editando arquivos de projeto carregados  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] armazena em cache o conteúdo dos arquivos de projeto e arquivos importados por arquivos de projeto. Se você editar um arquivo de projeto carregado, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticamente solicitará que você recarregue o projeto para que as alterações tenham efeito. No entanto se você editar um arquivo importado por um projeto carregado, não haverá nenhum prompt recarregar e é necessário descarregar e recarregar o projeto manualmente para que as alterações tenham efeito.  
  
## Grupos de saída  
 Vários destinos definidos em Microsoft.Common.targets têm nomes que terminam em `OutputGroups` ou `OutputGroupDependencies`.[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] chama esses destinos para obter listas específicas de saídas de projeto. Por exemplo, o `SatelliteDllsProjectOutputGroup` destino cria uma lista de todos os assemblies de satélite criará uma compilação. Esses grupos de saída são usados por recursos como referências de projeto para projeto, implantação e publicação. Projetos que não defini\-los carregará e compilar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], mas alguns recursos podem não funcionar corretamente.  
  
## Resolução de referência  
 Resolução de referência é o processo de usar os itens de referência armazenados em um arquivo de projeto para localizar assemblies reais.[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deve disparar a resolução de referência para mostrar propriedades detalhadas para cada referência no **propriedades** janela. A lista a seguir descreve os três tipos de referências e como eles são resolvidos.  
  
-   Referências de assembly:  
  
     O sistema de projeto chama um destino com o nome conhecido `ResolveAssemblyReferences`. Esse destino deve produzir itens com o nome do tipo de item `ReferencePath`. Cada um desses itens deve ter uma especificação de item \(o valor de `Include` atributo de um item\) que contém o caminho completo para a referência. Os itens devem ter todos os metadados dos itens de entrada passado além os novos metadados a seguir:  
  
    -   `CopyLocal`, que indica se o assembly deve ser copiado para a pasta de saída, definido como true ou false.  
  
    -   `OriginalItemSpec`, que contém a especificação de item original da referência.  
  
    -   `ResolvedFrom`, defina como "{TargetFrameworkDirectory}" se foi resolvido a partir do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] directory.  
  
-   Referências COM:  
  
     O sistema de projeto chama um destino com o nome conhecido `ResolveCOMReferences`. Esse destino deve produzir itens com o nome do tipo de item `ComReferenceWrappers`. Cada um desses itens deve ter uma especificação de item que contém o caminho completo para o assembly de interoperabilidade para referência COM. Os itens devem ter todos os metadados dos itens de entrada passados por meio, além disso, aos novos metadados com o nome `CopyLocal`, que indica se o assembly deve ser copiado para a pasta de saída, definido como true ou false  
  
-   Referências nativas  
  
     O sistema de projeto chama um destino com o nome conhecido `ResolveNativeReferences`. Esse destino deve produzir itens com o nome do tipo de item `NativeReferenceFile`. Os itens devem ter todos os metadados dos itens de entrada passado, além de uma nova parte de metadados chamada `OriginalItemSpec`, que contém a especificação de item original da referência.  
  
## Atalhos de desempenho  
 Se você iniciar a depuração de IU do Visual Studio \(escolhendo a tecla F5 ou escolhendo **Depurar**, **Iniciar depuração** na barra de menus\), o processo de compilação usa uma verificação de atualização rápida para melhorar o desempenho. Em alguns casos em que compilações personalizadas criam arquivos compilados por sua vez, a verificação de atualização rápida não identifica corretamente os arquivos alterados. Projetos que precisam de verificações de atualização mais completas podem desativar a verificação rápida, definindo a variável de ambiente `DISABLEFASTUPTODATECHECK=1`. Como alternativa, os projetos podem definir isso como uma propriedade de MSBuild no projeto ou em um arquivo que de projeto importa.  
  
 Para compilações regulares no Visual Studio, a verificação de atualização rápida não se aplica e o projeto será criado como se você chamou a compilação em um prompt de comando.  
  
## Consulte também  
 [Como estender o processo de compilação do Visual Studio](../msbuild/how-to-extend-the-visual-studio-build-process.md)   
 [Iniciando uma compilação pelo IDE](../msbuild/starting-a-build-from-within-the-ide.md)   
 [Registrando extensões do .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)   
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)   
 [Elemento Item \(MSBuild\)](../msbuild/item-element-msbuild.md)   
 [Elemento Property \(MSBuild\)](../msbuild/property-element-msbuild.md)   
 [Elemento Target \(MSBuild\)](../msbuild/target-element-msbuild.md)   
 [Tarefa Csc](../msbuild/csc-task.md)   
 [Tarefa Vbc](../msbuild/vbc-task.md)