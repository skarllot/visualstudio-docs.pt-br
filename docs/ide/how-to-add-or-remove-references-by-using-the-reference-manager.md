---
title: "Como adicionar ou remover referências usando o Gerenciador de Referências | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ReferenceManager
helpviewer_keywords:
- Visual C# projects, references
- references [Visual Studio], adding
- assemblies [Visual Studio], references
- Visual Basic projects, references
- project references, adding
- referencing components, adding references
- project references, removing
- referencing assemblies
- referencing components, removing references
- references [Visual Studio], removing
- referencing components, assemblies not listed
ms.assetid: 1aabb520-99b0-46c6-9368-21b4d84793eb
caps.latest.revision: 45
author: kempb
ms.author: kempb
manager: ghogen
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1e73cc14de8a94b2e2ce631834e36b6bc30fa7a6
ms.contentlocale: pt-br
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Como adicionar ou remover referências usando o Gerenciador de Referências
É possível usar a caixa de diálogo **Gerenciador de Referências** para adicionar e gerenciar referências aos componentes que você, a Microsoft ou outra empresa desenvolveram. Se você estiver desenvolvendo um aplicativo Universal do Windows, o projeto referenciará automaticamente todas as DLLs corretas do SDK do Windows. Se estiver desenvolvendo um aplicativo .NET, o projeto referenciará mscorlib.dll automaticamente. Algumas APIs do .NET são expostas em componentes que precisam ser adicionados manualmente. As referências a componentes COM ou a componentes personalizados devem ser adicionadas manualmente.  

## <a name="adding-and-removing-a-reference"></a>Adicionar e remover referências  

#### <a name="to-add-a-reference"></a>Para adicionar uma referência  

1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó Referências e escolha **Adicionar Referência**.  

2.  Especifique as referências a serem adicionadas e escolha o botão **OK**.  

 O **Gerenciador de Referências** é aberto e lista as referências disponíveis por grupo. O tipo de projeto determina qual dos seguintes grupos são exibidos:  

-   Assemblies, com os subgrupos de Framework e Extensions.  

-   Solução, com o subgrupo de Projetos.  

-   Windows, com os subgrupos Core e Extensions. É possível explorar as referências no SDK do Windows ou nos SDKs de extensão usando o **Pesquisador de Objetos**.  

-   Procurar, com o subgrupo Recente.  

## <a name="assemblies-tab"></a>Guia Assemblies  
 A guia **Assemblies** lista todos os assemblies do .NET Framework que estão disponíveis para referência. A guia **Assemblies** não lista os assemblies do GAC (cache de assembly global), pois os assemblies no GAC fazem parte do ambiente de tempo de execução. Se você implantar um aplicativo que contém uma referência a um assembly registrado no GAC, o assembly não será implantado ou copiado com o aplicativo, independentemente da configuração do Local da Cópia. Para obter mais informações, consulte [Referências do projeto](http://go.microsoft.com/fwlink/?LinkId=238512).  

 Ao adicionar manualmente uma referência a qualquer namespace EnvDTE (EnvDTE, EnvDTE80, EnvDTE90, EnvDTE90a ou EnvDTE100), defina a propriedade de Inserir Tipos Interop da referência como Falso na janela Propriedades. Definir essa propriedade como Verdadeiro poderá causar problemas de compilação devido a determinadas propriedades de EnvDTE que não podem ser inseridas.  

 Todos os projetos da área de trabalho contêm uma referência implícita a mscorlib. Os projetos do [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] contêm uma referência implícita em Microsoft.VisualBasic. No [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], todos os projetos contêm uma referência implícita a System.Core, mesmo se for removido da lista de referências.  

 Se um tipo de projeto não der suporte a Assemblies, a guia não será exibida na caixa de diálogo **Gerenciador de Referências**.  

 A guia Assemblies consiste em duas subguias:  

1.  O Framework lista todos os assemblies que constituem o Framework de destino.  

    -   Os assemblies anunciados estão no Framework completo e estão enumerados na lista de Frameworks quando o projeto tem como objetivo um perfil do Framework de destino. Os assemblies anunciados são cinzas para diferenciá-los dos assemblies que existem no perfil do Framework de destino do projeto. Por exemplo, se um projeto tem como objetivo o .NET Framework 4 Client, a lista do Framework exibirá assemblies anunciados do .NET Framework 4. Quando um usuário adiciona um assembly anunciado, o usuário é notificado de que, depois que a caixa de diálogo **Gerenciador de Referências** for fechada, o projeto terá o destino redefinido como o .NET Framework 4 e o assembly anunciado será adicionado.  

    -   Os projetos para aplicativos do [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] contêm referências a todos os assemblies do [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] de destino por padrão na criação do projeto. Em projetos gerenciados, um nó somente leitura na pasta Referências em **Gerenciador de Soluções** indica a referência a todo o Framework. Consequentemente, a guia Framework não enumerará nenhum dos assemblies do Framework e exibirá a seguinte mensagem: “Todos os assemblies do Framework já estão referenciados. Use o Pesquisador de Objetos para explorar as referências no Framework.” Para projetos de área de trabalho, a guia Framework enumera os assemblies do Framework de destino e o usuário deve adicionar as referências exigidas pelo aplicativo.  

2.  As extensões listam todos os assemblies que os fornecedores externos de componentes e controles desenvolveram para estender o Framework de destino. Dependendo da finalidade do aplicativo do usuário, esses assemblies podem ser necessários.  

    -   As extensões são populadas enumerando-se os assemblies registrados nos seguintes locais:  

        ```  
        32-bit machine:  
        HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
        64-bit machine:  
        HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
        And older versions of the [Target Framework Identifier]  
        ```  

         Por exemplo, se um projeto tiver como destino o .NET Framework 4 em um computador de 32 bits, as Extensões enumerarão os assemblies registrados em \Microsoft\\.NETFramework\v4.0\AssemblyFoldersEx\\, \Microsoft\\.NETFramework\v3.5\AssemblyFoldersEx\\, \Microsoft\\.NETFramework\v3.0\AssemblyFoldersEx\\ e \Microsoft\\.NETFramework\v2.0\AssemblyFoldersEx\\.  

 Alguns componentes na lista podem não ser exibidos, dependendo da versão [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] do projeto. Isso pode ocorrer nas seguintes condições:  

-   Um componente que usa uma versão recente do .NET Framework não é compatível com um projeto que tem uma versão anterior do .NET Framework como destino.  

     Para obter informações sobre como alterar a versão de destino do .NET Framework de um projeto, consulte [Como definir uma versão do .NET Framework como destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  

-   Um componente que usa [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] não é compatível com um projeto que tem [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] como destino.  

     Ao criar um novo aplicativo, alguns projetos têm [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] como destino por padrão.  

-   Você deve evitar adicionar referências de arquivo às saídas de outro projeto na mesma solução, porque essa ação poderá causar erros de compilação. Em vez disso, use a guia **Projetos** da caixa de diálogo **Adicionar Referência** para criar referências projeto a projeto. Essa ação facilita o desenvolvimento em equipe, permitindo um melhor gerenciamento das bibliotecas de classes criadas nos projetos. Para obter mais informações, consulte [Solução de problemas de referências desfeitas](../ide/troubleshooting-broken-references.md).  

-   > [!NOTE]
    >  No Visual Studio 2015 ou posterior, uma referência de arquivo será criada em vez de uma referência de projeto se a versão de destino do .NET Framework de um projeto for a versão 4.5 ou posterior e a versão de destino de outro projeto for 2, 3, 3.5 ou 4.0.  

#### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Para exibir um assembly na caixa de diálogo Adicionar Referência  

-   Mova ou copie o assembly para um dos seguintes locais:  

    -   O diretório atual do projeto. (É possível encontrar esses assemblies usando a guia **Procurar**.)  

    -   Outros diretórios do projeto na mesma solução. (É possível encontrar esses assemblies usando a guia **Projetos**.)  

     \- ou -  

-   Defina uma chave do Registro que especifica o local dos assemblies a ser exibido:  

     Para um sistema operacional de 32 bits, adicione uma das chaves do Registro a seguir.  

    -   [HKEY_CURRENT_USER\SOFTWARE\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"  

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"  

     Para um sistema operacional de 64 bits, adicione uma das chaves do Registro a seguir em um hive do Registro de 32 bits.  

    -   [HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"  

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"  

     *VersionMinimum* é a versão mínima do .NET Framework aplicável. Se *VersionMinimum* for v3.0, as pastas especificadas em AssemblyFoldersEx se aplicarão a projetos que têm como destino o .NET Framework 3.0 e posterior.  

     *AssemblyLocation* é o diretório dos assemblies que você deseja que sejam exibidos na caixa de diálogo **Adicionar Referência**, por exemplo, C:\MyAssemblies\\.  

     A criação da chave do Registro sob o nó HKEY_LOCAL_MACHINE permite que todos os usuários vejam os assemblies no local especificado na caixa de diálogo **Adicionar Referência**. A criação da chave do Registro sob o nó HKEY_CURRENT_USER afeta somente a configuração do usuário atual.  

     Abra a caixa de diálogo **Adicionar Referência** novamente. Os assemblies devem ser exibidos na guia **.NET**. Caso contrário, verifique se os assemblies estão localizados no diretório *AssemblyLocation* especificado, reinicie o Visual Studio e tente novamente.  

## <a name="com-tab"></a>Guia COM  
 A guia COM lista todos os componentes COM disponíveis para consulta. Se você deseja adicionar uma referência a uma DLL COM registrada que contém um manifesto interno, cancele o registro da DLL primeiro. Caso contrário, em vez de adicionar a referência do assembly como uma DLL nativa, o Visual Studio a adicionará como um Controle do ActiveX.  

 Se um tipo de projeto não der suporte ao COM, a guia não será exibida na caixa de diálogo **Gerenciador de Referências**.  

## <a name="solution-tab"></a>Guia Solução  
 A guia Solução lista todos os projetos compatíveis dentro da solução atual, na subguia Projetos.  

 Um projeto pode referenciar outro projeto que tenha como destino uma versão diferente do .NET Framework. Por exemplo, você pode criar um projeto que tenha como destino o [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)], mas que faça referência a um assembly que foi criado para o .NET Framework 2. Porém, o projeto do .NET Framework 2 não pode referenciar um projeto do [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]. Para obter mais informações, consulte [Definindo uma versão específica do .NET Framework como destino](../ide/targeting-a-specific-dotnet-framework-version.md).  

 Um projeto que tem como destino o [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] é incompatível com um projeto que tenha como destino o [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].  

 No [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], uma referência de arquivo em vez de uma referência de projeto será criada se um projeto tiver como destino o .NET Framework 4 e um outro projeto tiver como destino uma versão anterior.  

 Um projeto que tem como destino o [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] não pode adicionar uma referência de projeto a um projeto que tem como destino o .NET Framework e vice-versa.  

## <a name="windows-tab"></a>Guia Windows  
 A guia Windows lista todos os SDKs específicos às plataformas na qual sistemas operacionais Windows estão em execução.  

 Você pode gerar um arquivo WinMD no Visual Studio de duas maneiras:  

-   **[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] Projetos gerenciados pelo aplicativo**: os projetos do aplicativo [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] podem produzir binários WinMD definindo Propriedades do Projeto &#124; Tipo de Saída = Arquivo WinMD. O nome do arquivo WinMD deve ser o namespace do superconjunto de todos os namespaces existentes dentro dele. Por exemplo, se um projeto consiste nos namespaces A.B e A.B.C, os possíveis nomes para o WinMD emitido serão A.winmd e A.B.winmd. Se um usuário entrar em um valor de Propriedade do Projeto &#124; Nome do Assembly ou Propriedades do Projeto &#124; Namespace não contíguo ao conjunto de namespaces no projeto ou se não houver nenhum namespace de superconjunto em um projeto, um aviso de build será gerado: “A.winmd” não é um nome de arquivo .winmd válido para esse assembly. Todos os tipos em um arquivo de metadados do Windows devem existir em um namespace secundário do nome do arquivo. Tipos que não existem em um namespace secundário do nome de arquivo não poderão ser localizados no tempo de execução. Nesse assembly, o menor namespace comum é “CSWSClassLibrary1”. A área de trabalho do Visual Basic ou um projeto do Visual C# só podem consumir WinMDs gerados usando [!INCLUDE[win8](../debugger/includes/win8_md.md)] SDKs, conhecidos como primeira parte do WinMDs, e não podem gerar WinMDs.  

-   **[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] Projetos nativos do aplicativo**: um arquivo WinMD nativo consiste apenas em metadados. Sua implementação existe em um arquivo separado da DLL. É possível gerar binários nativos escolhendo o modelo de projeto do componente do Tempo de Execução do Windows na caixa de diálogo **Novo Projeto** ou em um projeto em branco e modificando as propriedades do projeto para gerar um arquivo WinMD. Se o projeto consiste em namespaces separados, um erro de compilação dirá ao usuário para combinar os namespaces ou executar a ferramenta MSMerge.  

 A guia Windows consiste em dois subgrupos.  

### <a name="core-subgroup"></a>Subgrupo Núcleo  
 O subgrupo Núcleo lista todos os WinMDs (para elementos de Tempo de Execução do Windows) no SDK para a versão de destino do Windows.  

 Os projetos de aplicativos [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] contêm referências a todos os WinMDs no [!INCLUDE[win8](../debugger/includes/win8_md.md)] SDK por padrão na criação do projeto. Em projetos gerenciados, um nó somente leitura na pasta Referências em **Gerenciador de Soluções** indica a referência a todo o SDK do [!INCLUDE[win8](../debugger/includes/win8_md.md)]. Consequentemente, o subgrupo Núcleo no Gerenciador de Referências não enumerará alguns assemblies do [!INCLUDE[win8](../debugger/includes/win8_md.md)] SDK e exibirá uma mensagem: “O SDK do já está referenciado. Use o Pesquisador de Objetos para explorar as referências no SDK Windows.”  

 Em projetos da área de trabalho, o subgrupo Núcleo não é exibido por padrão. É possível adicionar o Windows Runtime abrindo o menu de atalho do nó do projeto, escolhendo **Descarregar Projeto**, adicionando o trecho a seguir e reabrindo o projeto (no nó do projeto, escolha **Recarregar Projeto**). Ao invocar a caixa de diálogo **Gerenciador de Referências**, o subgrupo Núcleo é exibido.  

```  
<PropertyGroup>  
  <TargetPlatformVersion>8.0</TargetPlatformVersion>  
</PropertyGroup>  
```  

 Verifique se você marcou a caixa de seleção **Windows** nesse subgrupo. Você deve conseguir usar elementos de Tempo de Execução do Windows. No entanto, você também pode querer adicionar o System.Runtime, no qual o Tempo de Execução do Windows define algumas classes e interfaces padrão, como IEnumerable, usadas nas bibliotecas do Tempo de Execução do Windows. Para obter mais informações sobre como adicionar System.Runtime, consulte [Aplicativos da área de trabalho gerenciados e Windows Runtime](http://msdn.microsoft.com/library/windows/apps/jj856306.aspx#consuming_standard_windows_runtime_types).  

### <a name="extensions-subgroup"></a>Subgrupos Extensões  
 As extensões listam o usuário de SDKs que estendem a plataforma de destino do Windows. Essa guia é exibida somente para projetos de aplicativo [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. Os projetos de área de trabalho não exibirão essa guia porque podem consumir apenas arquivos de primeira parte .winmd.  

 O SDK é uma coleção de arquivos que o Visual Studio trata como um único componente. Na guia Extensões, os SDKs que se aplicam ao projeto do qual a caixa de diálogo **Gerenciador de Referências** foi invocada são listados como entradas únicas. Quando adicionado a um projeto, todo o conteúdo do SDK é consumido pelo Visual Studio de modo que o usuário não precisa realizar uma ação adicional para aproveitar os conteúdos do SDK no IntelliSense, na caixa de ferramentas, no designer, no Pesquisador de Objetos, na criação, implantação, depuração nem nos pacotes. Para obter informações sobre como exibir o SDK na guia Extensões, consulte [Criando um Software Development Kit](../extensibility/creating-a-software-development-kit.md).  

> [!NOTE]
>  Se um projeto referencia o SDK que depende de outro SDK, o Visual Studio não consumirá o segundo SDK a menos que o usuário adicione manualmente uma referência ao segundo SDK. Quando um usuário escolhe um SDK na guia **Extensões**, a caixa de diálogo **Gerenciador de Referências** ajuda o usuário a identificar dependências do SDK listando não apenas o nome e a versão do SDK, mas também o nome de todas as dependências do SDK no painel de detalhes. Se um usuário não observar as dependências e adicionar somente aquele SDK, o MSBuild solicitará que o usuário adicione dependências.  

 Se um tipo de projeto não der suporte a **Extensões**, a guia não será exibida na caixa de diálogo **Gerenciador de Referências**.  

## <a name="browse-button"></a>Botão Procurar  
 É possível usar o botão **Procurar** para procurar um componente no sistema de arquivos.  

 Um projeto pode referenciar um componente que tenha como destino uma versão diferente do .NET Framework. Por exemplo, você pode criar um aplicativo que tem como destino o .NET Framework 4 Client Profile, que referencia um componente que tem como destino o .NET Framework 2. Para obter mais informações, consulte [Definindo uma versão específica do .NET Framework como destino](../ide/targeting-a-specific-dotnet-framework-version.md).  

 Você deve evitar adicionar referências de arquivo às saídas de outro projeto na mesma solução, porque essa tática pode causar erros de compilação. Em vez disso, use a guia **Solução** da caixa de diálogo **Gerenciador de Referências** para criar referências projeto a projeto. Essa tática torna o desenvolvimento em equipe mais fácil, permitindo um melhor gerenciamento das bibliotecas de classes criadas em seus projetos. Para obter mais informações, consulte [Solução de problemas de referências desfeitas](../ide/troubleshooting-broken-references.md).  

 Não é possível navegar até o SDK e adicioná-lo ao projeto. Você pode apenas procurar um arquivo (por exemplo, um assembly ou um .winmd) e adicioná-lo ao seu projeto.  

 Ao fazer uma referência de arquivo a um WinMD, o layout previsto é que os arquivos *FileName*.winmd, *FileName*.dll e *FileName*.pri sejam colocados um ao lado do outro. Se você referenciar um WinMD nos seguintes cenários, um conjunto incompleto de arquivos será copiado no diretório de saída do projeto e, consequentemente, falhas de compilação e de tempo de execução ocorrerão.  

-   **Componente nativo**: um projeto nativo criará um WinMD para cada conjunto não contínuo de namespaces e uma DLL que consiste na implementação. O WinMDs terá nomes distintos. Ao fazer referência a esse arquivo de componente nativo, o MSBuild não reconhecerá que os WinMDs nomeados de forma diferente formam um componente. Consequentemente, somente o *FileName*.dll e *FileName*.winmd de nome idêntico serão copiados, e ocorrerão erros de tempo de execução. Para resolver esse problema, crie uma SDK de Extensão. Para obter mais informações, consulte [Criando um Software Development Kit](../extensibility/creating-a-software-development-kit.md).  

-   **Consumindo controles**: no mínimo, um controle XAML consiste em um *FileName*.winmd, *FileName*.dll, *FileName*.pri, *XamlName*.xaml e *ImageName*.jpg. Quando o projeto é compilado, os arquivos de recursos associados à referência de arquivo não serão copiados no diretório de saída do projeto, e apenas *FileName*.winmd, *FileName*.dll e *FileName*.pri serão copiados. Um erro de build é registrado para informar ao usuário que os recursos *XamlName*.xaml e *ImageName*.jpg estão ausentes. Para ter êxito, o usuário precisará copiar manualmente esses arquivos de recurso no diretório de saída do projeto para a compilação e a depuração/tempo de execução. Para resolver esse problema, crie um SDK de Extensão seguindo as etapas em [Criando um Software Development Kit](../extensibility/creating-a-software-development-kit.md) ou edite o arquivo de projeto para adicionar a seguinte propriedade:  

    ```  
    <PropertyGroup>  
    <GenerateLibraryOutput>True</GenerateLibraryOutput>  
    </PropertyGroup>  
    ```  

    > [!NOTE]
    >  Se você adicionar a propriedade, a compilação pode ficar mais lenta.  

## <a name="recent"></a>Recente  
 Assemblies, COM, Windows e Navegador suportam uma guia Recente, que enumera a lista de componentes adicionados recentemente aos projetos.  

## <a name="search"></a>Pesquisar  
 A barra de pesquisa na caixa de diálogo **Gerenciador de Referências** opera na guia que está no foco. Por exemplo, se um usuário digitar “Sistema” na barra de pesquisa enquanto a guia **Solução** estiver no foco, a pesquisa não retornará nenhum resultado a menos que a solução consista em um nome de projeto que contém “Sistema”.  

## <a name="see-also"></a>Consulte também  
 [NIB: como adicionar ou remover referências usando a caixa de diálogo Adicionar Referência](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md)

