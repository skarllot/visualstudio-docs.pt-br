---
title: "Espaços de trabalho nas Ferramentas do R para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/27/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d610279c-d6c3-4084-939a-bf042f64d4dd
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
ms.openlocfilehash: 8ac025a9da5c07cbc9efff416d07c93b91aa2c14
ms.contentlocale: pt-br
ms.lasthandoff: 05/12/2017

---


## <a name="controlling-where-r-code-runs-with-workspaces"></a>Controlando onde o código R é executado com espaços de trabalho

Um espaço de trabalho nas RTVS (Ferramentas do R para Visual Studio) permite configurar onde uma sessão do R é executada, o que pode ocorrer em computadores locais e remotos. A meta é permitir que você trabalhe com uma experiência de usuário semelhante, que ofereça a capacidade de usufruir de computadores baseados em nuvem possivelmente mais poderosos.

Para abrir a janela **Espaços de trabalho**, use o comando **Ferramentas do R > Janelas > Espaços de trabalho** ou pressione Ctrl + 9.

![Janela de espaços de trabalho nas Ferramentas do R para Visual Studio (VS2017)](~/rtvs/media/workspaces-window.png)

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

O comando **Ferramentas do R > Sessão > Redefinir** e o botão de barra de ferramentas de redefinição na janela interativa também redefinem o estado do espaço de trabalho a qualquer momento. No caso de espaços de trabalho remotos, uma redefinição tem o efeito de excluir o perfil do usuário criado na primeira conexão com o servidor remoto, o que exclui efetivamente todos os arquivos que foram acumulados lá.

## <a name="local-workspaces"></a>Espaços de trabalho locais

A lista de espaços de trabalho locais exibe todos os interpretadores de R instalados em seu computador. 

As RTVS tentam detectar automaticamente todas as versões do R que você instalou, examinando a chave do Registro `HKEY_LOCAL_MACHINE\Software\R-Core\` quando o Visual Studio é iniciado. Como essa verificação é feita apenas na inicialização, você precisará reiniciar o Visual Studio se instalar um novo interpretador de R.

As RTVS não podem detectar um interpretador de R que é instalado de maneira não padrão (por exemplo, simplesmente ao copiar arquivos para uma pasta em vez de executar um instalador). Nesse caso, crie manualmente um novo Espaço de trabalho do R local da seguinte maneira:

1. Selecione o botão **Adicionar** na janela de espaços de trabalho.
1. Insira um nome para o novo Espaço de trabalho.
1. Insira o caminho para a pasta raiz do R, que é aquele que contém a pasta `bin` com o intérprete e quaisquer argumentos de linha de comando opcionais a serem passados para o interpretador quando as RTVS o iniciarem.
1. Selecione **Salvar** quando terminar.

![Adicionando um novo espaço de trabalho](~/rtvs/media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Espaços de trabalho remotos

Os espaços de trabalho remotos permitem que você se conecte a uma sessão do R em um computador remoto. (Consulte [Configurando espaços de trabalho remotos](workspaces-remote-setup.md) para saber como configurar um computador com essa finalidade.)

Os espaços de trabalho remotos não são detectados automaticamente pelas RTVS, você deve adicioná-los manualmente usando o botão **Adicionar** na janela Espaços de trabalho, conforme descrito na seção anterior. Nesse caso, insira o URI do computador remoto, em vez de um caminho local.

> [!Important]
> Espaços de trabalho remotos são identificados por um URI que *deve usar o protocolo HTTPS* para garantir a privacidade e a integridade da comunicação com o computador remoto. As RTVS não se conectarão a um computador remoto que não ofereça suporte a HTTPS.

> [!Note]
> Os espaços de trabalho remotos estão efetivamente na visualização. Estamos trabalhando em uma melhor implementação do problema de sincronização de arquivo para uma versão futura e são bem-vindas suas ideias e comentários sobre o que podemos fazer para melhorar a experiência para você.


## <a name="switching-between-workspaces"></a>Alternando entre espaços de trabalho

As RTVS são associadas a apenas um espaço de trabalho por vez, que é indicado por uma marca de seleção verde pequena ao lado desse espaço de trabalho na janela Espaços de trabalho. Por padrão, as RTVS são associadas ao último Espaço de trabalho local que foi aberto em uma sessão anterior.

Para alterar o espaço de trabalho ativo, selecione a seta azul ao lado do espaço de trabalho desejado. Isso avisa para salvar sua sessão, encerra o espaço de trabalho atual e alterna para o novo.

> [!Tip]
> Para desabilitar prompt de salvamento, selecione o comando **Ferramentas do R > Opções** e defina a opção **Mostrar caixa de diálogo de confirmação antes de alternar espaços de trabalho** como `No`. Consulte [Opções de espaço de trabalho](options.md#workspace).

Se você tentar mudar para um espaço de trabalho local que foi desinstalado ou para um espaço de trabalho remoto indisponível, poderão ocorrer situações em que um projeto RTVS não está associado a nenhum espaço de trabalho. Como resultado, poderá ocorrer um erro como o mostrado abaixo ao inserir o código na janela interativa ou tentar executar o código de algum outro modo. Para corrigir isso, basta mudar para outro espaço de trabalho na janela Espaços de trabalho. Se não houver nenhum disponível, você precisará instalar um interpretador de R. Você também poderá reiniciar o Visual Studio se ele estava em execução quando você instalou um interpretador.

![Erro quando não há nenhum espaço de trabalho associado às RTVS](~/rtvs/media/workspaces-disconnected-interactive-window.png)

### <a name="switching-to-a-remote-workspace"></a>Alternar para um espaço de trabalho remoto

As RTVS solicitam credenciais quando você se conecta pela primeira vez a um espaço de trabalho remoto, em seguida, armazena em cache as credenciais (usando o Cofre de Credenciais seguro do Windows) para as sessões posteriores. A comunicação com o servidor remoto, em seguida, é feita com segurança em HTTPS (o que é necessário).

Dependendo da configuração do servidor, você verá um aviso de certificado ao conectar-se, "O certificado de segurança apresentado pelos serviços remotos do R não permite provar que você realmente está conectado ao computador (nome)."

![Aviso do certificado autoassinado ao conectar-se a um espaço de trabalho remoto](~/rtvs/media/workspaces-remote-self-signed-certificate-warning.png)

O certificado é um documento que é apresentado às RTVS pelo computador que você está tentando se conectar, que contém um campo que identifica o URI desse computador. O aviso é exibido quando as RTVS detectam uma incompatibilidade entre o URI no certificado e o URI usado para conectar-se ao computador, indicando que segurança do servidor pode ter sido comprometida.

No entanto, esse aviso também será exibido se um *certificado autoassinado* tiver sido usado para habilitar o HTTPS no computador remoto em vez de usar outro de um provedor confiável. Para obter mais detalhes, consulte [Configurando espaços de trabalho remotos](workspaces-remote-setup.md).

## <a name="directories-on-local-and-remote-computers"></a>Diretórios em computadores locais e remotos

Por padrão, quando você inicia um novo interpretador de R em um espaço de trabalho local, o diretório de trabalho atual é `%userprofile%\Documents`. Isso pode ser alterado a qualquer momento usando os comandos **Ferramentas do R > Diretório de Trabalho** ou clicando com o botão direito do mouse em um projeto no Gerenciador de Soluções do Visual Studio e selecionando comandos como **Definir Diretório de Trabalho Aqui**.

Em computadores remotos, as RTVS criam automaticamente um perfil do usuário com base em suas credenciais quando você se conecta pela primeira vez a esse servidor, portanto, o diretório de trabalho é a pasta `Documents` nesse perfil. Ele será usado para todas as sessões remotas subsequentes que usarem as mesmas credenciais. 

Como resultado, o local exato em que seu código é executado pode diferir entre espaços de trabalho locais e remotos. Portanto, no seu código, evite usar caminhos absolutos para arquivos de dados e outros, pois seu código provavelmente não será portátil entre os espaços de trabalho. Use caminhos relativos.

Observe também que com os espaços de trabalho remotos, todos os arquivos no diretório de trabalho permanecerão em vigor em sessões para o mesmo perfil do usuário. Conforme observado anteriormente, você pode excluir esses itens usando o comando **Ferramentas do R > Sessão > Redefinir** (ou no botão Redefinir na janela interativa) ao usar um espaço de trabalho remoto. Novamente, isso exclui o perfil do usuário do servidor, que é recriado quando você se conecta novamente.

## <a name="copying-project-files-to-remote-workspaces"></a>Copiando arquivos de projeto para espaços de trabalho remotos

Ao trabalhar com projetos R no Visual Studio, o computador local sempre tem os arquivos mais recentes do projeto, mesmo quando você está usando um espaço de trabalho remoto. Ou seja, quando você abre um projeto no Visual Studio (que normalmente significa abrir uma solução que contém o projeto), as RTVS supõem que o conteúdo do projeto reside inteiramente no computador local. O espaço de trabalho remoto é, na verdade, apenas um host temporário para os arquivos do projeto e as saídas do código. Isso significa, por exemplo, que ao carregar um arquivo usando `source` na janela interativa, esse arquivo já deve estar no computador remoto no caminho fornecido ou deve estar no diretório de trabalho atual do interpretador de R remoto (definido com a função `setwd()`).

Os arquivos são copiados para o servidor remoto da seguinte maneira:

- Para trabalhar com arquivos remotamente usando a janela interativa, você deve primeiro copiá-los manualmente clicando com o botão direito do mouse nesses arquivos (ou no projeto) no Gerenciador de Soluções e selecionando **Fonte Selecionada**. Para arquivos individuais, eles serão copiados para o diretório de trabalho no servidor. Ao copiar um projeto, as RTVS criarão uma pasta para o projeto.

- Você também pode copiar arquivos selecionando-os no Gerenciador de Soluções e escolhendo **Arquivos de Origem Selecionados**. Isso carrega-os na janela interativa e executa-os lá. Se a sessão está conectada a um computador remoto, os arquivos são copiados lá primeiro.

- Quando as RTVS estiverem associadas a um espaço de trabalho remoto e você pressionar F5, selecionar **Depurar > Iniciar Depuração** ou iniciar a execução do código de outro modo, as RTVS, por padrão, copiarão o arquivo do projeto para o espaço de trabalho remoto automaticamente (veja abaixo para saber como controlar isso).

- Todos os arquivos que já existem no servidor serão substituídos.

> [!Note]
> Como as RTVS não podem interceptar todas as chamadas de função do R com confiança, as chamadas de funções como `source()` ou `runApp()` (para aplicativos Shiny) na janela interativa *não* copiarão arquivos para o espaço de trabalho remoto.

Opções como se as RTVS copiam arquivos quando um projeto é executado e exatamente quais arquivos são copiados são controladas por meio das [propriedades do projeto](projects.md#project-properties). Para abrir esta página, selecione o comando de menu **Projeto > Propriedades do (nome)...** ou clique com o botão direito do mouse no projeto no Gerenciador de Soluções e selecione **Propriedades...**.

![Guia de execução de propriedades do projeto com configurações de transferência de arquivo](~/rtvs/media/workspaces-remote-file-transfer-filter-settings.png)

Aqui, **Transferir arquivos em execução** determina se as RTVS copiam os arquivos do projeto automaticamente. O valor de **Arquivos para transferir** filtra exatamente quais arquivos são transferidos. O padrão é copiar somente arquivos `.R`, `.Rmd`, `.sql`, `.md` e `.cpp`. Isso é feito para evitar a cópia acidental de grandes arquivos de dados para o servidor em todas as execuções. 

## <a name="copying-files-from-a-remote-workspace"></a>Copiando arquivos de um espaço de trabalho remoto

Se o seu script R gera arquivos no servidor, você pode copiar esses arquivos de volta para o cliente usando a função `rtvs::fetch_file`. Essa função aceita, no mínimo, o caminho remoto para o arquivo que você deseja copiar para o computador e, opcionalmente, o caminho no seu computador para o qual você deseja que esse arquivo seja copiado. Se você não especificar um caminho, o arquivo será copiado na pasta `%userprofile%\Downloads`.

