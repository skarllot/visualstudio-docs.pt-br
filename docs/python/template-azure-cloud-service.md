---
title: "Modelo de Projeto do Serviço de Nuvem do Azure para o Python | Microsoft Docs"
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2ce82ee-8c73-419a-bbd2-4c3513fd394d
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
translationtype: Human Translation
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: 5dd1c40c925327c9494e3a334cdf348692a4981d
ms.lasthandoff: 04/10/2017

---

# <a name="azure-cloud-service-projects-for-python"></a>Projetos do Serviço de Nuvem do Azure para o Python

O Visual Studio fornece modelos para ajudá-lo a começar a criar Serviços de Nuvem do Azure usando o Python.

Um [Serviço de Nuvem](http://go.microsoft.com/fwlink/?LinkId=306052) consiste em várias *funções de trabalho* e *funções web*, com cada uma executando uma tarefa separada conceitualmente, mas que podem ser replicadas separadamente em máquinas virtuais, conforme necessário para colocação em escala. As funções web fornecem hospedagem para aplicativos Web de front-end. Quanto ao Python, qualquer estrutura Web que dá suporte ao WSGI pode ser usada para escrever um aplicativo desse tipo (com suporte no [Modelo de Projeto Web](template-web.md)). As funções de trabalho destinam-se a processos de execução longa que não interagem diretamente com os usuários. Geralmente, elas fazem uso de bibliotecas de [dados](http://go.microsoft.com/fwlink/?LinkId=401571) e de [serviço de aplicativo](http://go.microsoft.com/fwlink/?LinkId=401572), que podem ser instaladas com `pip install`&nbsp;[`azure`](http://pypi.org/project/azure).

Este tópico contém detalhes sobre o modelo de projeto e outros tipos de suporte no Visual Studio 2017 (as versões anteriores são semelhantes, mas com algumas diferenças). Para obter mais informações sobre como trabalhar com o Azure no Python, visite a [Central de desenvolvedores do Azure Python](http://go.microsoft.com/fwlink/?linkid=254360).

## <a name="create-a-project"></a>Criar um projeto

1. Instale o [SDK do .NET do Azure para Visual Studio](https://www.visualstudio.com/vs/azure-tools/), que é necessário para usar o modelo do Serviço de Nuvem.
1. No Visual Studio, selecione **Arquivo > Novo > Projeto...**, pesquise “Azure Python” e selecione **Serviço de Nuvem do Azure** na lista:

    ![Modelo de Projeto de Nuvem do Azure para o Python](~/docs/python/media/template-azure-cloud-project.png)

1. Selecione uma ou mais funções a serem incluídas. Projetos de nuvem podem combinar funções escritas em linguagens diferentes; portanto, é possível escrever com facilidade cada parte do aplicativo na linguagem mais adequada. Para adicionar novas funções ao projeto depois de concluir essa caixa de diálogo, clique com o botão direito do mouse em **Funções** no Gerenciador de Soluções e selecione um dos itens em **Adicionar**.

    ![Adicionando funções no modelo de Projeto de Nuvem do Azure](~/docs/python/media/template-azure-cloud-service-project-wizard.png)

1. Conforme os projetos de função individuais são criados, você poderá precisar instalar pacotes adicionais do Python, como as estruturas Django, Bottle ou Flask, caso tenha selecionado uma função que usa uma delas.

1. Depois de adicionar uma nova função ao projeto, você verá algumas instruções de configuração. Em geral, elas são desnecessárias, mas podem ser úteis para personalização futura dos projetos. Observe que, ao adicionar várias funções ao mesmo tempo, somente as instruções para a última função permanecerão abertas. No entanto, é possível encontrar as instruções e dicas de solução de problemas para outras funções em seus respectivos arquivos `readme.mht`, localizados na raiz da função ou na pasta `bin`.

1. Uma pasta `bin` do projeto também contém um ou dois scripts do PowerShell que são usados para configurar a máquina virtual remota, incluindo a instalação do Python, qualquer arquivo [requirements.txt](#dependencies) no projeto e a configuração do IIS, se necessário. É possível editar esses arquivos conforme desejado para sua implantação, embora as opções mais comuns possam ser gerenciadas de outras maneiras (consulte [Configurando a implantação de função](#configuring-role-deployment) abaixo). Não sugerimos a remoção desses arquivos, pois um script de configuração herdado será usado no lugar deles, caso eles não estejam disponíveis.

    ![Arquivos de suporte à função de trabalho](~/docs/python/media/template-azure-cloud-service-worker-role-support-files.png)

    Para adicionar esses scripts de configuração a um novo projeto, clique com o botão direito do mouse no projeto, selecione **Adicionar > Novo Item...** e selecione **Arquivos de Suporte da Função Web** ou **Arquivos de Suporte da Função de Trabalho**.
   

## <a name="configuring-role-deployment"></a>Configurando a implantação de função

Os scripts do PowerShell na pasta `bin` de um projeto de função controlam a implantação da função e podem ser editados para personalizar a configuração:

- `ConfigureCloudService.ps1` é usado para funções web e de trabalho, normalmente, para instalar e configurar dependências e definir a versão do Python.
- `LaunchWorker.ps1` é usado somente para funções de trabalho e para alterar o comportamento de inicialização, adicionar argumentos de linha de comando ou adicionar variáveis de ambiente.

Os dois arquivos contêm instruções de personalização. Você também pode instalar sua própria versão do Python adicionando outra tarefa ao arquivo `ServiceDefinition.csdef` principal do projeto do serviço de nuvem, configurando a variável `PYTHON` com seu caminho `python.exe` instalado (ou equivalente). Quando `PYTHON` for definido, o Python não será instalado por meio do NuGet.

Uma configuração adicional pode ser feita da seguinte maneira:

1. Instale os pacotes usando `pip` com a atualização do arquivo `requirements.txt` no diretório raiz do projeto. O script `ConfigureCloudService.ps1` instalará esse arquivo durante a implantação.
1. Defina variáveis de ambiente modificando o arquivo `web.config` (funções web) ou a seção `Runtime` do arquivo `ServiceDefinition.csdef` (funções de trabalho).
1. Especifique o script e os argumentos a serem usados para uma função de trabalho modificando a linha de comando na seção `Runtime/EntryPoint` do arquivo `ServiceDefinitions.csdef`.
1. Defina o script principal do manipulador para uma função web por meio do arquivo `web.config`.

## <a name="testing-role-deployment"></a>Testando a implantação de função

Ao escrever as funções, é possível testar o projeto de nuvem localmente usando o Emulador do Serviço de Nuvem. O emulador está incluído nas Ferramentas do SDK do Azure e é uma versão limitada do ambiente usado quando o Serviço de Nuvem é publicado no Azure.

Para iniciar o emulador, primeiro verifique se o projeto de nuvem é o projeto de inicialização na solução clicando com o botão direito do mouse e selecionando **Definir como projeto de inicialização**. Em seguida, selecione **Depurar > Iniciar Depuração** (F5) ou **Depurar > Iniciar sem Depuração** (Ctrl+F5).

Observe que, devido a limitações no emulador, não é possível depurar o código do Python. Portanto, recomendamos que você depure as funções executando-as de forma independente e, em seguida, use o emulador para o teste de integração antes da publicação.


## <a name="deploying-a-role"></a>Implantando uma função

Para abrir o assistente para **Publicação**, selecione a função de projeto no Gerenciador de Soluções e selecione **Compilar > Publicar** no menu principal ou clique com o botão direito do mouse no projeto e selecione **Publicar**.

O processo de publicação envolve duas fases. Primeiro, o Visual Studio cria um único pacote que contém todas as funções para o serviço de nuvem. Esse pacote é o que é implantado no Azure, que inicializa uma ou mais máquinas virtuais para cada função e implanta a fonte.

Conforme cada máquina virtual é ativada, ele executa o script `ConfigureCloudService.ps1` e instala as dependências. Por padrão, esse script instala uma versão recente do Python por meio do [nuget](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) e os pacotes especificados em um arquivo `requirements.txt`. 

Por fim, as funções de trabalho executam `LaunchWorker.ps1`, que inicia a execução do script do Python; as funções web inicializam o IIS e começam a manipular solicitações da Web.


## <a name="dependencies"></a>Dependências

Para o Serviço de Nuvem, o script `ConfigureCloudService.ps1` usa `pip` para instalar um conjunto de dependências do Python. Elas devem ser especificadas em um arquivo chamado `requirements.txt` (personalizável com a modificação de `ConfigureCloudService.ps1`). O arquivo é executado com `pip install -r requirements.txt` como parte da inicialização.

Observe que as instâncias do Serviço de Nuvem não incluem compiladores do C e, portanto, todas as bibliotecas com extensões do C devem fornecer binários pré-compilados.

O PIP e suas dependências, bem como os pacotes em `requirements.txt`, serão baixados automaticamente e poderão ser contados como uso de largura de banda passível de cobrança. Consulte [Gerenciando os pacotes necessários](python-environments.md#managing-required-packages) para obter detalhes sobre como gerenciar arquivos `requirements.txt`.

## <a name="troubleshooting"></a>Solução de problemas

Se a função web ou a função de trabalho não funcionar corretamente após a implantação, verifique o seguinte:

- O projeto do Python inclui uma pasta bin\ com (no mínimo):
    - `ConfigureCloudService.ps1`
    - `LaunchWorker.ps1` (para funções de trabalho)
    - `ps.cmd`

- O projeto do Python inclui um arquivo `requirements.txt` que lista todas as dependências (ou, como alternativa, uma coleção de arquivos de roda).
- Habilite a Área de Trabalho Remota no Serviço de Nuvem e investigue os arquivos de log.
- Os logs de `ConfigureCloudService.ps1` e `LaunchWorker.ps1` são armazenados na pasta `C:\Resources\Directory\%RoleId%.DiagnosticStore\LogFiles` do computador remoto.
- As funções web podem gravar logs adicionais para um caminho configurado em `web.config`, ou seja, o caminho na appSetting `WSGI_LOG`. O log do IIS ou FastCGI normal do host também funcionará.
- Atualmente, o arquivo `LaunchWorker.ps1.log` é a única maneira de exibir a saída ou os erros exibidos pela função de trabalho do Python.
