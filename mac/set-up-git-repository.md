---
title: "Configurar um repositório Git no Visual Studio para Mac"
description: Usando o Git e o Subversion no Visual Studio para Mac.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 9f25eda17648ba7eb3c264660ee0eb3b8eee166c
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---

# <a name="setting-up-a-git-repository"></a>Configurando um repositório Git

O Git é um sistema de controle de versão distribuído que permite que as equipes trabalhem nos mesmos documentos simultaneamente. Isso significa que há um único servidor que contém todos os arquivos, mas sempre que um repositório passar por check-out nessa fonte central, todo o repositório será clonado localmente para seu computador.

Há muitos hosts remotos que permitem trabalhar com o Git para controle de versão, porém o mais comuns deles é o GitHub. O exemplo a seguir usa um host do GitHub, mas você pode usar qualquer host Git para controle de versão no Visual Studio para Mac.

Se você quiser usar GitHub, verifique se você tem uma conta criada e configurada antes de seguir as etapas abaixo. 

## <a name="creating-a-remote-repo-on-github"></a>Criando um repositório remoto no GitHub

O exemplo a seguir usa um host do GitHub, mas você pode usar qualquer host Git para controle de versão no Visual Studio para Mac.

Para configurar um repositório Git, execute as seguintes etapas:

1. Crie um novo repositório Git em github.com:

    ![Criar um novo repositório Git](media/version-control-git1-sml.png)

2. Defina o nome do repositório, a descrição e a privacidade. **Não** inicialize o repositório. Defina .gitignore e a licença como Nenhum:

    ![Defina os detalhes do repositório git](media/version-control-git2.png)

3. O próximo local fornecerá uma opção para exibir e copiar o endereço HTTP ou SSH para o repositório que você acabou de criar:

    ![exibir e copiar endereço](media/version-control-git3.png) Você precisará do endereço HTTPS para apontar o Visual Studio para Mac para este repositório.


## <a name="publishing-an-existing-project"></a>Publicar um projeto existente

4. Retorne ao seu Projeto aberto no Visual Studio para Mac. 

5. Na barra de menus, selecione **Controle de versão > Publicar no Controle de versão...**:

    ![Iniciar o check-out no Visual Studio para Mac](media/version-control-git4-sml.png)

6. Isso exibirá a caixa de diálogo **Selecionar repositório**. Escolha a guia **Repositórios registrados** e pressione o botão **Adicionar**:

    ![](media/version-control-git5.png)

7. Digite o nome do repositório como você gostaria de exibi-lo localmente e cole a URL da etapa 3. A caixa de diálogo de Configuração do repositório deve ser semelhante ao seguinte. Pressione OK: 

    ![Caixa de diálogo Insira os detalhes do git](media/version-control-git6.png)

    Observe que também é possível usar o SSH para se conectar-se ao Git.

8. Para tentar publicar o aplicativo no Git, selecione o repositório que você acabou de criar e verifique se ambos os campos de texto **Nome do módulo** e **Mensagem** foram preenchidos:

    ![Tentativa de publicar o projeto para o git](media/version-control-git7.png)

9. Clique em **OK** e em **Publicar** na caixa de diálogo de alerta.

10. Se você já não tiver inserido suas credenciais do Git nas preferências do Visual Studio para Mac, digite-as agora. Primeiro, será necessário criar um Token de acesso, que é usado em vez de uma senha. Siga as etapas na documentação de [Token de acesso](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) do Git para fazer isso.

11. Insira o nome de usuário e o token de acesso pessoal e pressione **OK**:

    ![Insira o nome de usuário e a senha para o git](media/version-control-git9-sml.png)

12. Depois de alguns segundos, a Solução deverá ser publicada com sua confirmação inicial. Confirme isso navegando o item de menu de Controle de versão, que agora deve ser populado com várias opções: 

    ![Menu de Controle de versão](media/version-control-git10.png)

13. Depois de começar a fazer mais alterações, selecione **Efetuar push nas alterações...** para enviar por push as alterações para o repositório **remoto**. Isso permitirá que todos os usuários apropriados possam exibi-las em github.com: 

    ![Enviar alterações por push para um repositório remoto](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Publicar um novo projeto

A caixa de diálogo Novo projeto pode ser usada para publicar um novo projeto usando o git. Para habilitá-lo, marque a caixa de seleção **Usar o git para controle de versão.** conforme ilustrado na captura de tela a seguir. Isso inicializará seu repositório e adicionará um arquivo .gitignore opcional:

![Enviar alterações por push para um repositório remoto](media/version-control-git12.png)

## <a name="troubleshooting"></a>Solução de problemas

Se você tiver problemas ao inicializar seu projeto com um repositório remoto vazio, você poderá tentar executar as seguintes etapas:

- Acesse a pasta da solução.
- Pressione `Command + Shift + . ` para mostrar os arquivos e as pastas ocultos.
- Se houver uma pasta `.git`, exclua-a.
- Se houver um arquivo `gitignore`, exclua-o.
- Pressione `Command + Shift + . ` para ocultar os arquivos e as pastas.
- Abra a solução no VS para Mac.
- No painel de soluções, selecione o nó da sua solução.
- Navegue para o menu de Controle de versão e escolha **Publicar no controle de versão**.
- Siga as etapas do tutorial acima a partir da etapa 6.
