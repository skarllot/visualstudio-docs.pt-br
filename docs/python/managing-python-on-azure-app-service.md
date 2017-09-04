---
title: "Gerenciando o Python no Serviço de Aplicativo do Azure | Microsoft Docs"
ms.custom: 
ms.date: 7/12/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e56b5d55-6e6b-48af-af40-5172c768cabc
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: c00adbbabf0d3b82acb17f4a269dfc693246bc69
ms.openlocfilehash: 56fccdd5e103cf29c8ea4a93ab80de7187275642
ms.contentlocale: pt-br
ms.lasthandoff: 08/01/2017

---

# <a name="managing-python-on-azure-app-service"></a>Gerenciando o Python no Serviço de Aplicativo do Azure

O [Serviço de Aplicativo do Azure](https://azure.microsoft.com/services/app-service/) é uma oferta de plataforma como serviço para aplicativos Web, quer eles sejam sites acessados por meio de um navegador, APIs REST usadas por seus próprios clientes ou processamento disparado por evento. O Serviço de Aplicativo dá suporte total ao uso do Python para implementar aplicativos.

O suporte ao Python no Serviço de Aplicativo do Azure é fornecido como um conjunto de extensões do site do Serviço de Aplicativo e cada um contém uma versão específica do tempo de execução do Python. A versão mais recente do Python 3 é recomendada, obviamente, mas você pode escolher uma versão mais antiga quando necessário. Este tópico explica como instalar e configurar uma extensão de site junto com todos os pacotes desejados.

> [!Note]
> Os processos descritos aqui estão sujeitos a alterações e especialmente a aperfeiçoamento. As alterações são anunciadas no [blog Python Engineering at Microsoft](https://blogs.msdn.microsoft.com/pythonengineering/) (Engenharia do Pyhton na Microsoft).

## <a name="choosing-a-python-version-through-the-azure-portal"></a>Escolhendo uma versão do Python por meio do Portal do Azure

Se seu site já estiver implantado e em execução no Serviço de Aplicativo do Azure, navegue até a folha de Serviço de Aplicativo, vá para a seção **Ferramentas de Desenvolvimento** e selecione **Extensões > Adicionar**. Percorra a lista para localizar as extensões específicas para a versão do Python desejada. (Infelizmente, a lista não é classificável, então as diferentes versões geralmente estão espalhadas na lista):

![Portal do Azure mostrando extensões do Python](media/python-on-azure-extensions.png)

## <a name="choosing-a-python-version-through-the-azure-resource-manager"></a>Escolhendo uma versão do Python por meio do Azure Resource Manager

Se você estiver implantando seu site com um modelo do Azure Resource Manager, adicione a extensão do site como um recurso. A extensão é exibida como um recurso aninhado de seu site com o tipo `siteextensions` e o nome de [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22).

Por exemplo, depois de adicionar uma referência a `python361x64` (Python 3.6.1 x64), o modelo pode se parecer com o seguinte:

```json
  "resources": [
    {
      "apiVersion": "2015-08-01",
      "name": "[parameters('siteName')]",
      "type": "Microsoft.Web/sites",
      ...
      "resources": [
        {
          "apiVersion": "2015-08-01",
          "name": "python361x64",
          "type": "siteextensions",
          "properties": { },
          "dependsOn": [
            "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
          ]
        },
      ...
```

## <a name="configuring-your-site"></a>Configurando seu site

Depois de instalar a extensão de site (por meio do portal ou um modelo do Azure Resource Manager), o caminho de instalação do Python será algo como `d:\home\python361x64\python.exe`. Para ver o caminho específico, selecione a extensão na lista mostrada para o Serviço de Aplicativo para abrir sua página de descrição contendo o caminho:

![Lista de extensão no Serviço de Aplicativo do Azure](media/python-on-azure-extension-list.png)

![Detalhes de extensão no Serviço de Aplicativo do Azure](media/python-on-azure-extension-detail.png)

A próxima etapa é fazer referência à instalação de Python no arquivo `web.config` do site para os manipuladores de solicitação da Plataforma HTTP e do FastCGI.

### <a name="using-the-fastcgi-handler"></a>Usando o manipulador do FastCGI

O FastCGI é uma interface que funciona no nível da solicitação. O IIS recebe conexões de entrada e encaminha cada solicitação para um aplicativo WSGI em execução em um ou mais processos Python persistentes. O [pacote wfastcgi](https://pypi.io/project/wfastcgi) é pré-instalado e configurado com cada extensão de site do Python, portanto você pode habilitá-lo facilmente incluindo o código a seguir em `web.config`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <add key="WSGI_HANDLER" value="app.wsgi_app"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule" scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py" resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

Os `<appSettings>` estão disponíveis para seu aplicativo como variáveis de ambiente:
- O valor de `PYTHONPATH` pode ser estendido gratuitamente, mas deve incluir a raiz do seu site.
- `WSGI_HANDLER` deve apontar para um aplicativo WSGI importável do seu site.
- `WSGI_LOG` é opcional, mas recomendado para depuração de seu site. 

Em `<handlers>`, verifique se atributo `scriptProcessor` no elemento `<add>` contém os caminhos adequados para sua instalação específica. O caminho é mostrado novamente na folha de detalhes da extensão.

### <a name="using-the-http-platform-handler"></a>Usando o manipulador de Plataforma HTTP

O módulo HttpPlatform passa as conexões de soquete diretamente para um processo de Python autônomo. Essa passagem permite que você execute qualquer servidor Web que desejar, mas requer um script de inicialização que executa um servidor Web local. Você especifica o script no elemento `<httpPlatform>`, em que o atributo `processPath` aponta para o Python e o atributo `arguments` aponta para seu script e quaisquer argumentos que você desejar fornecer:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="D:\home\Python361x64\python.exe"
                  arguments="D:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="D:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

O caminho para `python.exe` em sua configuração é, logicamente, específico para a versão instalada.

A variável de ambiente `HTTP_PLATFORM_PORT` mostrada no código contém a porta que o servidor local deve ouvir para as conexões de localhost. Este exemplo também mostra como criar outra variável de ambiente, se desejado, nesse caso `SERVER_PORT`.

## <a name="installing-packages"></a>Instalando pacotes

Como seu aplicativo provavelmente depende de uma variedade de pacotes, você precisa se certificar de que esses pacotes estão instalados em seu ambiente de Python no Serviço de Aplicativo por meio de um dos três métodos:

- O console do Serviço de Aplicativo do Azure no Portal do Azure
- A API REST do Kudu
- Copiando cada biblioteca no código-fonte do aplicativo

### <a name="kudu-console"></a>Console do Kudu

O [console Kudu](https://github.com/projectkudu/kudu/wiki/Kudu-console) fornece acesso de linha de comando com privilégios elevados e direto para o servidor do Serviço de Aplicativo e seu sistema de arquivos. Além de ser uma ferramenta de depuração valiosa, ele também pode ser usado para configurações de CLI.

Acesse o Kudu da folha do seu Serviço de Aplicativo selecionando **Ferramentas de Desenvolvimento > Ferramentas Avançadas** e selecione **Ir** para navegar para uma URL igual à sua URL do Serviço de Aplicativo base, exceto com `.scm` inserido. Por exemplo, se a URL base for `https://vspython-test.azurewebsites.net/`, o Kudu está em `https://vspython-test.scm.azurewebsites.net/`:

![O console do Kudu para o Serviço de Aplicativo do Azure](media/python-on-azure-console01.png)

Selecione **Console de depuração > CMD** para abrir o console, no qual você pode navegar em sua instalação do Python e ver quais bibliotecas já estão lá.

Para instalar um único pacote:

1. Navegue até a pasta da instalação do Python em que você deseja instalar o pacote, como `d:\home\python361x64`.
1. Use `python.exe -m pip install <package_name>` para instalar um pacote.

![Exemplo de instalação do matplotlib por meio do console do Kudu para Serviço de Aplicativo do Azure](media/python-on-azure-console02.png)

Para instalar os pacotes de seu `requirements.txt` (recomendado):

1. Navegue até a pasta da instalação do Python em que você deseja instalar o pacote, como `d:\home\python361x64`.
1. Use `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt` para instalar um pacote.

Usar requirements.txt é recomendado porque é fácil reproduzir seu conjunto de pacote exato localmente e no servidor.

> [!Note]
> Não há nenhum compilador C em seu servidor Web, portanto você precisa instalar a roda para todos os pacotes com módulos de extensão nativos. Muitos pacotes populares fornecem suas próprias rodas. Para pacotes que não o fazem, use `pip wheel <package_name>` em seu computador de desenvolvimento local e, em seguida, carregue a roda para seu site. Para obter um exemplo, consulte [Gerenciando pacotes necessários](python-environments.md#managing-required-packages)

### <a name="kudu-rest-api"></a>API REST do Kudu

Em vez de usar o console de Kudu por meio do portal do Azure, você pode executar comandos remotamente por meio da API REST do Kudu postando o comando para `https://yoursite.scm.azurewebsites.net/api/command`. Por exemplo, para instalar o pacote `matplotlib`, poste o seguinte JSON para `/api/command`:

```json
{
    "command": 'python.exe -m pip install matplotlib',
    "dir": '\home\python361x64'
}
```

Para obter informações sobre comandos e autenticação, consulte a [Documentação do Kudu](https://github.com/projectkudu/kudu/wiki/REST-API). Você também pode ver as credenciais usando o [`az webapp deployment list-publishing-profiles command`](https://docs.microsoft.com/cli/azure/webapp/deployment#list-publishing-profiles) da CLI do Azure. Uma biblioteca de ajuda para publicar comandos Kudu também está [disponível no GitHub](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42).


### <a name="copying-libraries-into-app-source-code"></a>Copiando bibliotecas no código-fonte do aplicativo

Em vez de instalar os pacotes diretamente no servidor, você pode copiar bibliotecas em seu próprio código-fonte e implantá-las como se fizessem parte do seu aplicativo. Dependendo de quantas dependências você tem e da frequência com que você os atualiza, esse método pode ser a maneira mais fácil de dar início à implantação.

A limitação é que essas bibliotecas devem corresponder precisamente à versão do Python no servidor, caso contrário, você verá erros obscuros após a implantação. No entanto, como as versões do Python nas extensões de site do Serviço de Aplicativo são exatamente as mesmas lançadas em python.org, você pode obter uma versão compatível para desenvolvimento local facilmente.

### <a name="avoiding-virtual-environments"></a>Evitando ambientes virtuais

Embora trabalhar em um ambiente virtual localmente possa ajudá-lo a entender completamente as dependências necessárias para seu site, o uso de ambientes virtuais no Serviço de Aplicativo não é recomendável. Em vez disso, apenas instale as bibliotecas em sua pasta principal do Python e implante-as com seu aplicativo para evitar ter dependências conflitantes.

