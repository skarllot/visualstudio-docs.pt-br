---
title: "Espaços de trabalho nas Ferramentas do R para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 6/30/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d610279c-d6c3-4084-939a-bf042f64d4dd
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 4764fb9fc6b0cd2e6160540fdec3f33370d81128
ms.contentlocale: pt-br
ms.lasthandoff: 07/12/2017

---

# <a name="controlling-where-r-code-runs-with-workspaces"></a>Controlando onde o código R é executado com espaços de trabalho

Um espaço de trabalho nas RTVS (Ferramentas do R para Visual Studio) permite configurar onde uma sessão do R é executada, o que pode ocorrer em computadores locais e remotos. A meta é permitir que você trabalhe com uma experiência de usuário semelhante, que ofereça a capacidade de usufruir de computadores baseados em nuvem possivelmente mais poderosos.

Para abrir a janela **Espaços de trabalho**, use o comando **Ferramentas do R > Janelas > Espaços de trabalho** ou pressione Ctrl + 9.

![Janela de espaços de trabalho nas Ferramentas do R para Visual Studio (VS2017)](media/workspaces-window.png)

Nessa janela, a marca de seleção verde indica o espaço de trabalho ativo ao qual as RTVS estão associadas. Selecionar uma seta azul define o espaço de trabalho ativo. O ícone de configurações (engrenagem) à direita de cada espaço de trabalho permite que você altere os argumentos de linha de comando, o local e o nome. O X vermelho remove um espaço de trabalho adicionado manualmente.

Neste tópico:

- [Salvando e redefinindo um espaço de trabalho](#saving-and-resetting-a-workspace)
- [Espaços de trabalho locais](#local-workspaces)
- [Espaços de trabalho remotos](#remote-workspaces)
- [Alternando entre espaços de trabalho](#switching-between-workspaces)
- [Diretórios em computadores locais e remotos](#directories-on-local-and-remote-computers)
- [Copiando arquivos de projeto para espaços de trabalho remotos](#copying-project-files-to-remote-workspaces)
- [Copiando arquivos de um espaço de trabalho remoto](#copying-files-from-a-remote-workspace)

## <a name="saving-and-resetting-a-workspace"></a>Salvando e redefinindo um espaço de trabalho

Por padrão, as RTVS não salvam o estado do espaço de trabalho quando você fecha e reabre um projeto. No entanto, você pode alterar esse comportamento por meio das [Opções de espaço de trabalho](options.md#workspace).

O comando **Ferramentas do R > Sessão > Redefinir** e o botão de barra de ferramentas de redefinição na janela interativa também redefinem o estado do espaço de trabalho a qualquer momento. Com espaços de trabalho remotos, a redefinição exclui o perfil do usuário criado na primeira conexão com o servidor remoto, o que exclui efetivamente todos os arquivos que foram acumulados lá.

## <a name="local-workspaces"></a>Espaços de trabalho locais

A lista de espaços de trabalho locais exibe todos os interpretadores de R instalados em seu computador. 

Quando o Visual Studio é iniciado, ele tenta detectar automaticamente todas as versões do R que você instalou examinando a chave do Registro `HKEY_LOCAL_MACHINE\Software\R-Core\`. Como essa verificação é feita apenas na inicialização, você precisará reiniciar o Visual Studio se instalar um novo interpretador de R.

As RTVS não podem detectar um interpretador de R que é instalado de maneira não padrão (por exemplo, simplesmente ao copiar arquivos para uma pasta em vez de executar um instalador). Nesse caso, crie manualmente um novo Espaço de trabalho do R local da seguinte maneira:

1. Selecione o botão **Adicionar** na janela de espaços de trabalho.
1. Insira um nome para o novo Espaço de trabalho.
1. Insira o caminho para a pasta raiz do R, que é aquele que contém a pasta `bin` com o intérprete, juntamente com quaisquer argumentos de linha de comando opcionais a serem passados para o interpretador quando as RTVS o iniciarem.
1. Selecione **Salvar** quando terminar.

![Adicionando um novo espaço de trabalho](media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Espaços de trabalho remotos

Os espaços de trabalho remotos permitem que você se conecte a uma sessão do R em um computador remoto. (Consulte [Configurando espaços de trabalho remotos](workspaces-remote-setup.md) para saber como configurar um computador com essa finalidade.)

O Visual Studio não detecta os espaços de trabalho remotos automaticamente, você deve adicioná-los manualmente usando o botão **Adicionar** na janela Espaços de trabalho, conforme descrito na seção anterior. Nesse caso, insira o URI do computador remoto, em vez de um caminho local.

> [!Important]
> Espaços de trabalho remotos são identificados por um URI que *deve usar o protocolo HTTPS* para garantir a privacidade e a integridade da comunicação com o computador remoto. O Visual Studio não pode se conectar a um computador remoto que não dá suporte a HTTPS.

> [!Note]
> Os espaços de trabalho remotos estão efetivamente na visualização. Estamos trabalhando em uma implementação melhor do problema de sincronização de arquivo para uma versão futura e são bem-vindas suas ideias e comentários.


## <a name="switching-between-workspaces"></a>Alternando entre espaços de trabalho

As RTVS estão associadas a apenas um espaço de trabalho por vez. O espaço de trabalho associado é indicado por uma marca de seleção verde pequena na janela de Espaços de trabalho. Por padrão, as RTVS são associadas ao último espaço de trabalho local aberto em uma sessão anterior.

Para alterar o espaço de trabalho ativo, selecione a seta azul ao lado do espaço de trabalho desejado. Isso avisa para salvar sua sessão, encerra o espaço de trabalho atual e alterna para o novo.

> [!Tip]
> Para desabilitar prompt de salvamento, selecione o comando **Ferramentas do R > Opções** e defina a opção **Mostrar caixa de diálogo de confirmação antes de alternar espaços de trabalho** como `No`. Consulte [Opções de espaço de trabalho](options.md#workspace).

Se você tentar mudar para um espaço de trabalho local que foi desinstalado ou para um espaço de trabalho remoto indisponível, as RTVS podem não ser associadas a nenhum espaço de trabalho. Como resultado, você pode ver um erro ao inserir o código na janela interativa ou tentar executar o código de outro modo:

![Erro quando não há nenhum espaço de trabalho associado às RTVS](media/workspaces-disconnected-interactive-window.png)

Para corrigir isso, mude para outro espaço de trabalho na janela Espaços de trabalho. Se não houver nenhum espaço de trabalho disponível, você precisará instalar um interpretador de R. Você também poderá tentar reiniciar o Visual Studio se ele estava em execução quando você instalou um interpretador.

### <a name="switching-to-a-remote-workspace"></a>Alternar para um espaço de trabalho remoto

As RTVS solicitam credenciais quando você se conecta pela primeira vez a um espaço de trabalho remoto, em seguida, armazena em cache as credenciais (usando o Cofre de Credenciais seguro do Windows) para as sessões posteriores. A comunicação com o servidor remoto, em seguida, é feita com segurança em HTTPS (o que é necessário).

Dependendo da configuração do servidor, você verá um aviso de certificado ao conectar-se dizendo "O certificado de segurança apresentado pelos serviços remotos do R não permite provar que você realmente está conectado ao computador (nome)."

![Aviso do certificado autoassinado ao conectar-se a um espaço de trabalho remoto](media/workspaces-remote-self-signed-certificate-warning.png)

O certificado é um documento apresentado às RTVS pelo computador ao qual você está tentando se conectar. O certificado contém um campo que identifica o URI do computador. O aviso é exibido quando as RTVS detectam uma incompatibilidade entre o URI no certificado e o URI usado para se conectar ao computador, indicando que segurança do servidor pode ter sido comprometida.

No entanto, esse aviso também será exibido se um *certificado autoassinado* tiver sido usado para habilitar o HTTPS no computador remoto em vez de usar outro de um provedor confiável. Para obter mais informações, consulte [Configurando espaços de trabalho remotos](workspaces-remote-setup.md).

## <a name="directories-on-local-and-remote-computers"></a>Diretórios em computadores locais e remotos

Por padrão, quando você inicia um novo interpretador de R em um espaço de trabalho local, o diretório de trabalho atual é `%userprofile%\Documents`. Você pode alterar o diretório a qualquer momento usando os comandos **Ferramentas do R > Diretório de Trabalho** ou clicando com o botão direito do mouse em um projeto no Gerenciador de Soluções do Visual Studio e selecionando comandos como **Definir Diretório de Trabalho Aqui**.

Quando você se conecta pela primeira vez a um computador remoto, as RTVS criam automaticamente um perfil do usuário em suas credenciais, o que configura o diretório de trabalho para a pasta `Documents` nesse perfil. Essa pasta será usada para todas as sessões remotas subsequentes que usam as mesmas credenciais. 

Como resultado, o local exato em que seu código é executado pode diferir entre espaços de trabalho locais e remotos. No seu código, sempre use caminhos relativos para os arquivos de dados e assim por diante para que seu código seja portátil entre os espaços de trabalho.

Observe também que com os espaços de trabalho remotos, todos os arquivos no diretório de trabalho permanecerão em vigor em sessões para o mesmo perfil do usuário. Conforme observado anteriormente, você pode excluir esses arquivos usando o comando **Ferramentas do R > Sessão > Redefinir** (ou no botão Redefinir na janela interativa) ao usar um espaço de trabalho remoto. Novamente, esse comando exclui o perfil do usuário do servidor, que é recriado quando você se conecta novamente.

## <a name="copying-project-files-to-remote-workspaces"></a>Copiando arquivos de projeto para espaços de trabalho remotos

Ao trabalhar com projetos R no Visual Studio, o computador local sempre tem os arquivos de projeto mais recentes, mesmo quando você está usando um espaço de trabalho remoto. Ou seja, quando você abre um projeto no Visual Studio (que normalmente significa abrir uma solução que contém o projeto), as RTVS supõem que o conteúdo do projeto reside inteiramente no computador local. O espaço de trabalho remoto é, na verdade, apenas um host temporário para os arquivos do projeto e as saídas do código. Isso significa, por exemplo, que ao carregar um arquivo usando `source` na janela interativa, esse arquivo já deve estar no computador remoto no caminho fornecido ou deve estar no diretório de trabalho atual do interpretador de R remoto (definido com a função `setwd()`).

Os arquivos são copiados para o servidor remoto da seguinte maneira:

- Para trabalhar com arquivos remotamente usando a janela interativa, você deve primeiro copiá-los manualmente clicando com o botão direito do mouse nesses arquivos (ou no projeto) no Gerenciador de Soluções e selecionando **Fonte Selecionada**. Para arquivos individuais, eles são copiados para o diretório de trabalho no servidor. Ao copiar um projeto, as RTVS criam uma pasta para o projeto.

- Você também pode copiar arquivos selecionando-os no Gerenciador de Soluções e escolhendo **Arquivos de Origem Selecionados**. Essa ação os carrega na janela interativa e os executa lá. Se a sessão está conectada a um computador remoto, os arquivos são copiados lá primeiro.

- Quando as RTVS estiverem associadas a um espaço de trabalho remoto e você pressionar F5, selecionar **Depurar > Iniciar Depuração** ou iniciar a execução do código de outro modo, as RTVS, por padrão, copiarão o arquivo do projeto para o espaço de trabalho remoto automaticamente (veja abaixo para saber como controlar esse comportamento).

- Todos os arquivos que já existem no servidor são substituídos.

> [!Note]
> Como as RTVS não podem interceptar todas as chamadas de função do R com confiança, as chamadas de funções como `source()` ou `runApp()` (para aplicativos Shiny) na janela interativa *não* copiam arquivos para o espaço de trabalho remoto.

As [Propriedades do projeto](projects.md#project-properties) controlam se o RTVS copia arquivos quando o projeto é executado e exatamente quais arquivos são copiados. Para abrir esta página, selecione o comando de menu **Projeto > Propriedades do (nome)...** ou clique com o botão direito do mouse no projeto no Gerenciador de Soluções e selecione **Propriedades...**.

![Guia de execução de propriedades do projeto com configurações de transferência de arquivo](media/workspaces-remote-file-transfer-filter-settings.png)

Aqui, a propriedade **Transferir arquivos em execução** determina se as RTVS copiam os arquivos do projeto automaticamente. O valor de **Arquivos para transferir** filtra exatamente quais arquivos são transferidos. O padrão é copiar somente arquivos `.R`, `.Rmd`, `.sql`, `.md` e `.cpp`. Esse comportamento é feito para evitar a cópia acidental de grandes arquivos de dados para o servidor em todas as execuções. 

## <a name="copying-files-from-a-remote-workspace"></a>Copiando arquivos de um espaço de trabalho remoto

Se o seu script R gera arquivos no servidor, você pode copiar esses arquivos de volta para o cliente usando a função `rtvs::fetch_file`. Essa função aceita, no mínimo, o caminho remoto para o arquivo que você deseja copiar para o computador e, opcionalmente, o caminho de destino em seu computador. Se você não especificar um caminho, o arquivo será copiado na pasta `%userprofile%\Downloads`.

