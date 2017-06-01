---
title: "Espaços de trabalho remotos com as Ferramentas do R para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/27/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5778c9cf-564d-47b0-8d64-e5dc09162479
caps.latest.revision: 1
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
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 1016f07c0f4505f2dd652482dd4d568655565cf0
ms.contentlocale: pt-br
ms.lasthandoff: 05/12/2017

---


# <a name="setting-up-remote-workspaces"></a>Configurando espaços de trabalho remotos

Para usar um espaço de trabalho remoto com as RTVS (Ferramentas do R para Visual Studio), o computador remoto deve ser configurado com SSL e um serviço do R apropriado conforme explicado neste tópico. 

- [Requisitos do computador remoto](#remote-computer-requirements)
- [Instalar um certificado SSL](#install-an-ssl-certificate)
- [Instalar serviços do R](#install-r-services)
- [Configurar serviços do R](#configure-r-services)
- [Solução de problemas](#troubleshooting)

## <a name="remote-computer-requirements"></a>Requisitos do computador remoto

- Windows 10, Windows Server 2016 ou Windows Server 2012 R2. As RTVS também requerem
- [.NET framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) ou superior

## <a name="install-an-ssl-certificate"></a>Instalar um certificado SSL

As RTVS requerem que todas as comunicações com um servidor remoto ocorram por HTTP, o que requer um certificado SSL no servidor. Você pode usar um certificado assinado por uma autoridade de certificação confiável (recomendado) ou um certificado autoassinado (que fará com que as RTVS emitam avisos durante a conexão). Nas duas opções, você precisa instalá-lo no computador e permitir o acesso a sua chave privada.

### <a name="obtaining-a-trusted-certificate"></a>Obtendo um certificado confiável

Um certificado confiável é emitido por uma autoridade de certificação (consulte [autoridades de certificação na Wikipédia](https://en.wikipedia.org/wiki/Certificate_authority) para saber mais). Como obter um cartão de identificação do governo, isso envolve um processo maior e possíveis taxas, mas verifica a autenticidade da solicitação e do solicitante.

O campo de chave que precisa estar no certificado é o nome de domínio totalmente qualificado do computador do servidor R. A autoridade de certificação exigirá uma prova de que você está autorizado a criar um novo servidor para o domínio ao qual o seu servidor pertence.

Para obter mais informações, consulte [Public key certificate](https://en.wikipedia.org/wiki/Public_key_certificate) (certificados de chave pública) na Wikipédia.

### <a name="obtaining-a-self-signed-certificate"></a>Obtendo um certificado autoassinado

Em comparação com um certificado de uma autoridade confiável, um certificado autoassinado é como criar um cartão de identificação para você. Isso é, naturalmente, muito mais simples do que trabalhar com uma autoridade confiável, mas também não tem autenticação forte, o que significa que um invasor pode substituir seus próprios certificados pelo certificado não assinado e capturar todo o tráfego entre o cliente e o servidor. *Portanto, o certificado autoassinado deve ser usado somente para testar cenários, em uma rede confiável e nunca em produção.*

Por esse motivo, as RTVS sempre emitem o seguinte aviso durante a conexão com um servidor com um certificado autoassinado:

![Caixa de diálogo de aviso de certificado autoassinado](media/workspaces-remote-self-signed-certificate-warning.png)

Para emitir um certificado autoassinado:

1. Faça logon no computador do servidor R usando uma conta Administrador.
1. Abra um novo prompt de comando do PowerShell do administrador e execute o seguinte comando, substituindo `"remote-machine-name"` pelo nome de domínio totalmente qualificado do computador servidor.

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. Se você nunca executou o Powershell antes no computador do servidor R, será necessário executar o comando a seguir para habilitar a execução de comandos explicitamente:

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

Para obter informações, consulte [self-signed certificates](https://en.wikipedia.org/wiki/Self-signed_certificate) (certificados autoassinados) na Wikipédia.

### <a name="installing-the-certificate"></a>Instalando o certificado

Para instalar o certificado no computador remoto, execute `certlm.msc` (o gerenciador de certificados) em um prompt de comando. Clique com botão direito do mouse na pasta **Pessoal** e selecione o comando **Todas as Tarefas > Importar**:

![Comando Importar certificado](media/workspaces-remote-certificate-import.png)


### <a name="granting-permissions-to-read-the-ssl-certificates-private-key"></a>Concedendo permissões para ler a chave privada do certificado SSL

Depois que o certificado for importado, conceda à conta `NETWORK SERVICE` permissões para ler a chave privada, conforme as instruções abaixo. `NETWORK_SERVICE` é a conta usada para executar o agente de serviços do R, que é o serviço que termina as conexões SSL de entrada para o computador servidor.

1. Execute `certlm.msc` (o Gerenciador de Certificados) em um prompt de comando do administrador.
1. Expanda **Pessoal > Certificados**, clique com o botão direito do mouse no seu certificado e selecione **Todas as Tarefas > Gerenciar Chaves Privadas**.
1. Clique com o botão direito do mouse no certificado e selecione o comando Gerenciar Chaves Privadas em Todas as Tarefas
1. Na caixa de diálogo que aparece, selecione **Adicionar** e insira `NETWORK SERVICE` como o nome da conta:

    ![Caixa de diálogo Gerenciar Chaves Privadas, adicionando NETWORK_SERVICE](media/workspaces-remote-manage-private-key-dialog.png)

1. Selecione **OK** duas vezes para fechar as caixas de diálogo e confirmar suas alterações.


## <a name="install-r-services"></a>Instalar serviços do R

Para executar o código R, o computador remoto deve ter um interpretador de R instalado da seguinte maneira:

1. Baixe e instale um dos seguintes:

    - [Microsoft R Open](https://mran.microsoft.com/open/)
    - [CRAN R para Windows](https://cran.r-project.org/bin/windows/base/)

    Ambos têm funcionalidade idêntica, mas o Microsoft R Open beneficia-se de bibliotecas de álgebra linear aceleradas por hardware como cortesia do [Intel Math Kernel Library](https://software.intel.com/intel-mkl).

1. Execute o [Instalador de serviços do R](https://aka.ms/rtvs-services) e reinicie quando solicitado. O instalador faz o seguinte:

    -    Cria uma pasta no `%PROGRAMFILES%\R Tools for Visual Studio\1.0\` e copia todos os binários necessários.
    -    Instala `RHostBrokerService` e `RUserProfileService` e configura para iniciar automaticamente.
    -    Configura o serviço `seclogon` para iniciar automaticamente.
    -    Adiciona `Microsoft.R.Host.exe` e `Microsoft.R.Host.Broker.exe` às regras de entrada do firewall na porta padrão 5444.

Os serviços do R serão iniciados automaticamente quando o computador for reiniciado:

- O **Serviço de agente de host do R** lida com todo o tráfego HTTPS entre o Visual Studio e o processo em que o código R é executado no computador.
- O **Serviço de perfil do usuário do R** é um componente com privilégios que lida com a criação de perfil do usuário do Windows. Ele é chamado quando um novo usuário faz logon pela primeira vez no computador do servidor R.

Você pode ver isso no console de gerenciamento de serviços (`compmgmt.msc`).  

## <a name="configure-r-services"></a>Configurar serviços do R

Com os serviços do R em execução no computador remoto, você também precisa criar contas de usuário, definir regras de firewall, configurar a rede do Azure e configurar o certificado SSL.

1. Contas de usuário: crie contas para cada usuário que vai acessar o computador remoto. Você pode criar contas de usuário local padrão (sem privilégios) ou você pode ingressar o computador do servidor R em seu domínio e adicionar os grupos de segurança apropriados ao grupo de segurança `Users`.
1. Regras de firewall: por padrão, o `R Host Broker` escuta na porta TCP 5444. Portanto, verifique se há regras de firewall do Windows habilitadas para o tráfego de entrada e saída (a saída é necessária para instalar pacotes e cenários semelhantes).  O instalador de serviços do R define essas regras automaticamente para o firewall do Windows interno. Se você estiver usando um firewall de terceiros, será necessário abrir manualmente a porta 5444 para o `R Host Broker`.
1. Configuração do Azure: se o computador remoto for uma máquina virtual no Azure, você também precisará abrir a porta 5444 para tráfego de entrada na rede do Azure, que é independente do firewall do Windows. Para obter detalhes, consulte [Filtrar o tráfego de rede com grupos de segurança de rede](https://docs.microsoft.com/azure/virtual-network/virtual-networks-nsg) na documentação do Azure.
1. Informar ao Agente de Host do R qual certificado SSL deve ser carregado: se você estiver instalando o certificado em um servidor de Intranet, é provável que o nome de domínio totalmente qualificado do servidor seja o mesmo que seu nome NETBIOS. Nesse caso não há nada que você precise fazer, pois esse é o certificado padrão que é carregado.

    No entanto, se você estiver instalando o certificado em um servidor voltado para à Internet (como uma VM do Azure), use o FQDN (nome de domínio totalmente qualificado) do servidor, porque o FQDN de um servidor de acesso à Internet nunca será o mesmo que seu nome NETBIOS.

    Para fazer isso, navegue até onde os serviços do R estão instalados (`%PROGRAM FILES%\R Remote Service for Visual Studio\1.0` por padrão), abra o arquivo `Microsoft.R.Host.Broker.Config.json` em um editor de texto e substitua seu conteúdo pelo seguinte, atribuindo CN para o FQDN do servidor, como `foo.westus.cloudapp.azure.com`:

    ```json
    {
      "server.urls": "https://0.0.0.0:5444",
      "security": {
        "X509CertificateName": "CN=your-server-fully-qualified-domain-name"
      }
    }
    ```

    Salve o arquivo e reinicie o computador para aplicar as alterações.

## <a name="troubleshooting"></a>Solução de problemas

**O computador do servidor R não está respondendo, o que devo fazer?**

Verifique se você puder executar ping no computador remoto usando a linha de comando: `ping remote-machine-name`. Se o ping falhar, verifique se o computador está em execução.

**P. A janela R Interativo diz quo computador remoto está ativado, mas por que o serviço não está em execução?**

Há três possíveis razões para isso:

-    O [.NET framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) ou superior não está instalado no computador.
-    As regras de firewall para `Microsoft.R.Host.Broker` e `Microsoft.R.Host` não estão habilitadas para conexões de entrada e saída na porta 5444.
-    Um certificado SSL com `CN=<remote-machine-name>` não foi instalado.

Reinicie o computador depois de fazer as alterações acima. Verifique se `RHostBrokerService` e `RUserPofileService` estão em execução por meio de um Gerenciador de Tarefas (guia de serviços) ou `services.msc`.

**P. Por que a janela R Interativo disse "401 acesso negado" ao fazer a conexão com o servidor R?**

Há dois motivos possíveis:

- É muito provável que a conta `NETWORK SERVICE` não tenha acesso à chave privada do certificado SSL. Siga as instruções anteriores para conceder o acesso `NETWORK SERVICE` à chave privada.
- Verifique se o serviço `seclogon` está em execução. Use `services.msc` para configurar o `seclogon` para ser iniciado automaticamente.                                                         
**P. Por que a janela R Interativo disse "404 não encontrado" ao fazer a conexão com o servidor R?**

Isso provavelmente ocorre devido à ausência de bibliotecas redistribuíveis do Visual C++. Verifique a janela R Interativo para ver se há uma mensagem sobre biblioteca ausente (DLL). Verifique se o VS 2015 redistribuível está instalado e se o R está instalado também.

**P. Não consigo acessar a Internet e os recursos da janela R Interativo, o que devo fazer?**

Verifique se as regras de firewall para `Microsoft.R.Host.Broker` e `Microsoft.R.Host` permitem acesso de saída na porta 5444. Reinicie o computador após a aplicação das alterações.

**P. Tentei todos os itens acima e ele ainda não funciona. E agora?**

Examine os arquivos de log em `C:\Windows\ServiceProfiles\NetworkService\AppData\Local\Temp`. Você encontrará um arquivo de log separado para cada instância do Serviço de Agente do R que foi executada. Em outras palavras, se o serviço precisa ser reiniciado por algum motivo, é criado um novo arquivo de log. Examine aquele que tem o carimbo de data/hora mais recente para obter pistas sobre o que pode estar dando errado.

