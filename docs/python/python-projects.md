---
title: Projetos do Python no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9c53f76-d0ef-4095-8b39-b7eb9bb33aba
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
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
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 3190be68fbba464a84a7a25b2d829979944bdb1f
ms.contentlocale: pt-br
ms.lasthandoff: 05/09/2017

---

# <a name="python-projects"></a>Projetos do Python

Normalmente, os aplicativos do Python são definidos com o uso somente de arquivos e pastas, mas isso pode se tornar complexo conforme os aplicativos ficam maiores e talvez envolvam arquivos gerados automaticamente, JavaScript para aplicativos Web e assim por diante. Para ajudar a gerenciar essa complexidade, é possível criar projetos do Visual Studio para aplicativos do Python. Um projeto do Python (um arquivo `.pyproj`) identifica todos os arquivos de origem e de conteúdo associados ao projeto, contém informações de build de cada arquivo, mantém as informações para integração com sistemas de controle de código-fonte e ajuda você a organizar o aplicativo em componentes lógicos.

Além disso, os projetos são sempre gerenciados em uma *solução* do Visual Studio, que pode conter vários projetos que podem se referenciar mutuamente. Por exemplo, um projeto do Python pode referenciar um módulo de extensão de um projeto do C++, de modo que o Visual Studio compilará o projeto do C++ automaticamente (se necessário) ao iniciar a depuração do projeto do Python. (Para obter uma discussão geral, consulte [Soluções e projetos no Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).)

![Projeto do Python no Gerenciador de Soluções](media/projects-solution-explorer.png)

O Visual Studio fornece uma variedade de modelos de projeto do Python para configurar diversas estruturas de aplicativo rapidamente, incluindo um modelo para criar um projeto com base em uma árvore de pastas existente e um modelo para criar um projeto limpo e vazio. Consulte [Modelos de projeto](#project-templates) abaixo para obter um índice.

Neste tópico:

- [Adicionando arquivos, atribuindo um arquivo de inicialização e configurando ambientes](#adding-files-assigning-a-startup-file-and-setting-environments)
- [Modelos de projeto](#project-templates)
- [Arquivos vinculados](#linked-files)
- [Referências](#references)

<a name="lightweight-usage-project-free"</a>
> [!Tip]
> Mesmo sem um projeto, o Visual Studio funciona bem com o código do Python, já que é possível abrir um arquivo do Python isoladamente e aproveitar o preenchimento automático, o IntellSense e a depuração (clicando com o botão direito do mouse no editor e selecionando **Iniciar [com | sem] Depuração**). No entanto, como esse código sempre usará o ambiente global padrão, talvez você veja preenchimentos incorretos ou erros, caso o código se destine a outro ambiente. Além disso, o Visual Studio analisa todos os arquivos e pacotes na pasta da qual o arquivo individual é aberto, o que pode consumir tempo considerável de CPU.
>
> É simples criar um projeto do Visual Studio com base em um código existente, conforme descrito abaixo em [Criando um projeto com base em arquivos existentes](#creating-a-project-from-existing-files).

Para obter uma introdução aos projetos do Python no Visual Studio, assista a [Getting Started with Python Tools Part 2: Projects](https://youtu.be/KHPoVpL7zHg?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) (Introdução às Ferramentas Python, parte 2: Projetos) (youtube.com, 3min18s).

> [!VIDEO https://www.youtube.com/embed/KHPoVpL7zHg]

Assista também ao vídeo [Deep Dive: Using source control with Python projects](https://youtu.be/Aq8eqApnugM) (Aprofundamento: Usando o controle do código-fonte com projetos do Python) (youtube.com, 8min55s).

> [!VIDEO https://www.youtube.com/embed/Aq8eqApnugM]


## <a name="adding-files-assigning-a-startup-file-and-setting-environments"></a>Adicionando arquivos, atribuindo um arquivo de inicialização e configurando ambientes

À medida que você desenvolve seu aplicativo, normalmente, você precisará adicionar novos arquivos de diferentes tipos ao projeto. Isso é feito com facilidade clicando com o botão direito do mouse no projeto e selecionando a opção **Adicionar > Item Existente...**, com a qual você procura um arquivo a ser adicionado ou **Adicionar > Novo Item...**, que abre uma caixa de diálogo com uma variedade de modelos de item, incluindo arquivos vazios do Python, uma classe do Python, um teste de unidade e vários arquivos relacionados a aplicativos Web. Incentivamos você a explorar essas opções com um projeto de teste para saber o que está disponível em sua versão do Visual Studio.

Cada projeto do Python tem um arquivo de inicialização atribuído, mostrado em negrito no Gerenciador de Soluções. Esse é o arquivo que é executado quando você inicia a depuração (F5 ou **Depurar > Iniciar Depuração**) ou executa o projeto na janela interativa (Shift+Alt+F5 ou **Depurar > Executar Projeto na Interativa do Python**). Para alterá-lo, clique com o botão direito do mouse no novo arquivo e selecione **Definir como Arquivo de Inicialização**.

> [!Tip]
> Se você remover o arquivo de inicialização selecionado de um projeto e não selecionar um novo, a tentativa de executar o projeto fará com que uma janela de saída do Python apareça, porém, em seguida, desapareça quase imediatamente. Se você observar esse comportamento, verifique se haverá um arquivo de inicialização atribuído. Além disso, para manter a janela de saída aberta nesses casos, clique com o botão direito do mouse no projeto, selecione **Propriedades**, selecione a guia **Depurar** e, em seguida, adicione `-i` ao campo **Argumentos do Interpretador**. Isso fará com que o interpretador entre no modo interativo após a conclusão de um programa, mantendo a janela aberta até que você pressione Ctrl + Z, Enter para sair.

Um novo projeto sempre é associado ao ambiente global padrão do Python. Para associar o projeto a outro ambiente (incluindo ambientes virtuais), clique com o botão direito do mouse no nó **Ambientes do Python** do projeto, selecione **Adicionar/Remover Ambientes do Python** e selecione os ambientes desejados. Para alterar o ambiente ativo, clique com o botão direito do mouse no ambiente desejado e selecione **Ativar Ambiente**, conforme mostrado abaixo. Para obter mais detalhes, consulte [Ambientes do Python](python-environments.md#project-specific-environments).

![Ativando um ambiente para um projeto do Python](media/projects-activate-environment.png)

<a name="project-types"</a>
## <a name="project-templates"></a>Modelos de projeto

O Visual Studio fornece várias maneiras para configurar um projeto do Python, do zero ou com base em um código existente. Para usar um modelo, selecione o comando de menu **Arquivo > Novo > Projeto...** ou clique com o botão direito do mouse na solução, no Gerenciador de Soluções e selecione **Adicionar > Novo Projeto...**, que abrirá a caixa de diálogo **Novo Projeto** abaixo. Para ver modelos específicos ao Python, pesquise “Python” ou selecione o nó **Modelos > Outros Linguagens > Python**:

![Nova caixa de diálogo do projeto com modelos do Python](media/projects-new-project-dialog.png)

A seguinte tabela resume os modelos disponíveis no Visual Studio 2017 (nem todos os modelos estão disponíveis em todas as versões anteriores):

| Modelo | Descrição | 
| --- | --- |
| [Com Base em um Código Existente do Python](#creating-a-project-from-existing-files) | Cria um projeto do Visual Studio com base em um código existente do Python em uma estrutura de pastas.  |
| Aplicativo do Python | Uma estrutura de projeto básica para um novo aplicativo do Python com um único arquivo de origem vazio. Por padrão, o projeto é executado no interpretador do console do ambiente global padrão, que pode ser alterado com a [atribuição de outro ambiente](python-environments.md#project-specific-environments). |
| [Serviço de Nuvem do Azure](template-azure-cloud-service.md) | Um projeto para um Serviço de Nuvem do Azure escrito em Python. |
| [Projetos Web](template-web.md) | Projetos para servidores Web baseados em várias estruturas, incluindo Bottle, Django, Flask e Flask/Jade. |
| Aplicativo do IronPython | Semelhante ao modelo de Aplicativo do Python, mas usa o IronPython, por padrão, habilitando a interoperabilidade do .NET e a depuração de modo misto com as linguagens .NET. |
| Aplicativo WPF do IronPython | Uma estrutura de projeto que usa o IronPython com arquivos XAML do Windows Presentation Foundation para a interface do usuário do aplicativo. O Visual Studio fornece um designer de interface do usuário XAML, code-behind pode ser escrito no Python e o aplicativo é executado sem exibir um console. |
| Página da Web do IronPython Silverlight | Um projeto do IronPython executado em um navegador usando o Silverlight. O código do aplicativo do Python é incluído na página da Web como um script. Uma marca de script de texto clichê puxa um código JavaScript que inicializa o IronPython em execução dentro do Silverlight, no qual o código do Python pode interagir com o DOM. |
| Aplicativo do Windows Forms do IronPython | Uma estrutura de projeto que usa o IronPython com a interface do usuário usando o código com o Windows Forms. O aplicativo é executado sem exibir um console. |
| Aplicativo em segundo plano (IoT) | Dá suporte à implantação de projetos do Python a serem executados como serviços em segundo plano em dispositivos. Visite a [Central de desenvolvedores do Windows IoT](https://dev.windows.com/en-us/iot) para obter mais informações. |
| Módulo de extensão do Python | Esse modelo é exibido no Visual C++ se você instalou as **ferramentas de desenvolvimento nativo do Python** com a carga de trabalho do Python no Visual Studio 2017 (confira [Instalação](installation.md)). Ele fornece a estrutura principal para uma DLL de extensão do C++, semelhante ao que é descrito em [Criando uma extensão do C++ para o Python](cpp-and-python.md). |

<a name="create-project-from-existing-files"</a>
### <a name="creating-a-project-from-existing-files"></a>Criando um projeto com base em arquivos existentes

1. Selecione o menu **Arquivo > Novo > Projeto...** e, em seguida, selecione o modelo **Com Base em um Código Existente do Python**.
1. Na próxima caixa de diálogo, defina o caminho para o código existente, um filtro para tipos de arquivo e os caminhos de pesquisa exigidos pelo projeto e, em seguida, selecione **Avançar**:

    ![Novo Projeto com base em um Código Existente, etapa 1](media/projects-from-existing-1.png)

1. Escolha um ambiente para o projeto e o arquivo de inicialização e, em seguida, pressione **Avançar**. (Observe que a caixa de diálogo mostra somente os arquivos na raiz da árvore de pastas; se o arquivo desejado estiver em uma subpasta, deixe o arquivo de inicialização em branco e defina-o mais tarde no Gerenciador de Soluções).

    ![Novo Projeto com base em um Código Existente, etapa 2](media/projects-from-existing-2.png)

1. Selecione a localização para salvar o arquivo de projeto (isso não move nem copia os arquivos de origem; portanto, se desejar uma cópia, você deverá fazer uma antes de usar o modelo). Nesta caixa de diálogo, também é possível incluir a detecção automática de ambientes virtuais e personalizar o projeto para outras estruturas Web.

    ![Novo Projeto com base em um Código Existente, etapa 3](media/projects-from-existing-3.png)

1.  Selecione **Concluir** e o Visual Studio criará o projeto e o abrirá no Gerenciador de Soluções. Se desejar mover o arquivo .pyproj para outro lugar, selecione-o no Gerenciador de Soluções e escolha **Arquivo > Salvar Como**. Isso atualiza as referências de arquivo no projeto, mas não moverá nenhum arquivo de código.

## <a name="linked-files"></a>Arquivos vinculados

Arquivos vinculados são aqueles que são inseridos em um projeto, mas que geralmente residem fora das pastas do projeto do aplicativo. Eles são exibidos no Gerenciador de Soluções como arquivos normais com um ícone de atalho sobreposto: ![Ícone de arquivo vinculado](media/projects-linked-file-icon.png)

Arquivos vinculados são especificados no arquivo `.pyproj` usando o elemento `<Compile Include="...">` normal. Eles poderão ser arquivos vinculados implícitos se usarem um caminho relativo fora da estrutura do diretório ou poderão ser arquivos de link explícito com a especificação do caminho no Gerenciador de Soluções:

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

Arquivos vinculados serão ignorados em uma das seguintes condições:

- O arquivo vinculado contém metadados do Link e o caminho especificado no atributo Include reside no diretório do projeto
- O arquivo vinculado duplica um arquivo que existe na hierarquia do projeto
- O arquivo vinculado contém metadados do Link e o caminho do Link é um caminho relativo fora da hierarquia do projeto
- O caminho do link tem raiz

### <a name="working-with-linked-files"></a>Trabalhando com arquivos vinculados

Para adicionar um item existente como um link, clique com o botão direito do mouse na pasta do projeto em que você deseja adicionar o arquivo e selecione **Adicionar > Saindo do Item...**. Na caixa de diálogo exibida, selecione um arquivo e escolha **Adicionar como Link** no menu suspenso do botão **Adicionar**. Desde que não existam arquivos conflitantes, isso criará um link na pasta selecionada. No entanto, o link não será adicionado se já existir um arquivo com o mesmo nome ou se já existir um link para esse arquivo no projeto.

Se você tentar vincular a um arquivo que já existe nas pastas do projeto, ele será adicionado como um arquivo normal e não como um link. Para converter um arquivo em um link, selecione **Arquivo > Salvar Como** para salvar o arquivo em uma localização fora da hierarquia do projeto; o Visual Studio o converterá em um link automaticamente. Da mesma forma, um link pode ser convertido novamente usando a opção **Arquivo > Salvar Como** para salvar o arquivo em algum lugar na hierarquia do projeto. 

Se você mover um arquivo vinculado no Gerenciador de Soluções, o link será movido, mas o arquivo real não será afetado. Da mesma forma, a exclusão de um link removerá o link sem afetar o arquivo.

Os arquivos vinculados não podem ser renomeados.

## <a name="references"></a>Referências

Os projetos do Visual Studio dão suporte à adição de referências a projetos e extensões, que são exibidas no nó **Referências** do Gerenciador de Soluções:

![Referências de extensão em projetos do Python](media/projects-extension-references.png)

Geralmente, referências de extensão indicam dependências entre projetos e são usadas para fornecer o IntelliSense em tempo de design ou a vinculação em tempo de compilação. Os projetos do Python usam referências de forma semelhante, mas devido à natureza dinâmica do Python, elas são usadas principalmente em tempo de design para fornecer um IntelliSense avançado. Elas também podem ser usadas para implantação no Microsoft Azure para instalar dependências adicionais.

### <a name="extension-modules"></a>Módulos de extensão

Uma referência a um arquivo `.pyd` habilita o IntelliSense no módulo gerado. O Visual Studio carrega o arquivo `.pyd`, que é carregado no interpretador do Python e examina seus tipos e suas funções. Ele também tenta analisar as cadeias de caracteres doc em funções para fornecer ajuda da assinatura.

Se, a qualquer momento, o módulo de extensão é atualizado em disco, o Visual Studio analisa o módulo novamente em segundo plano. Isso não tem nenhum efeito no comportamento do tempo de execução, mas alguns preenchimentos só estarão disponíveis quando a análise for concluída.

Talvez você também precise adicionar um [caminho de pesquisa](python-environments.md#search-paths) à pasta que contém o módulo.

### <a name="net-projects"></a>Projetos do .NET

Ao trabalhar com o IronPython, é possível adicionar referências aos assemblies do .NET para habilitar o IntelliSense. Para projetos do .NET na solução, clique com o botão direito do mouse no nó **Referências** do projeto do Python, selecione **Adicionar Referência**, selecione a guia **Projetos** e procure o projeto desejado. Para as DLLs baixadas separadamente, selecione a guia **Procurar** e procure a DLL desejada.

Como as referências no IronPython só estarão disponíveis quando uma chamada a `clr.AddReference('AssemblyName')` for feita, você também precisará adicionar uma chamada `clr.AddReference` ao assembly.

### <a name="webpi-projects"></a>Projetos do WebPI

É possível adicionar referências a entradas de produto do WebPI para implantação no Serviço de Nuvem do Microsoft Azure, em que é possível instalar componentes adicionais por meio do feed do WebPI. Por padrão, o feed exibido é específico ao Python e inclui o Django, o CPython e outros componentes básicos. Você também pode selecionar seu próprio feed, conforme mostrado abaixo. Ao publicar no Microsoft Azure, uma tarefa de instalação instala todos os produtos referenciados.

![Referências do WebPI](media/projects-webPI-components.png)
