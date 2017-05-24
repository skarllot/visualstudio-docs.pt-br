---
title: "Solucionando problemas de instalação | Microsoft Docs"
description: "{{ESPAÇO RESERVADO}}"
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: d8125873ab5a92d9af26c556cb2f953a606c28d9
ms.contentlocale: pt-br
ms.lasthandoff: 05/09/2017

---
# <a name="troubleshooting-visual-studio-2017-installation-and-upgrade-failures"></a>Solucionando problemas de falhas de instalação e atualização do Visual Studio 2017

## <a name="symptoms"></a>Sintomas
Quando você tentar instalar ou atualizar o Microsoft Visual Studio 2017, a operação falhará.

## <a name="workaround"></a>Solução alternativa
Para encontrar uma solução alternativa para esse problema, siga estas etapas.

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Etapa 1: verificar se esse é um problema conhecido
Existem alguns problemas conhecidos com o instalador do Visual Studio que a Microsoft está trabalhando para corrigir. Verifique a [seção Problemas conhecidos em nossas notas de versão](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#KIinstall) para ver se há uma solução para o problema.

### <a name="step-2---check-with-the-developer-community"></a>Etapa 2: conferir com a comunidade de desenvolvedores
Pesquise na mensagem de erro com a [Comunidade de Desenvolvedores do Visual Studio] (https://developercommunity.visualstudio.com/spaces/8/index.html. Outros membros da comunidade podem ter documentado uma solução para o seu problema.

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Etapa 3 - excluir o diretório de instalação do Visual Studio para corrigir problemas de atualização
O bootstrapper de instalação do Visual Studio é um executável leve mínimo que instala o restante do instalador do Visual Studio. A exclusão de arquivos de instalação do Visual Studio e a nova execução do bootstrapper podem resolver algumas falhas de atualização. Para fazer isso, execute estas etapas:

1. Fechar o instalador do Visual Studio.
2. Exclua o diretório de instalação do Visual Studio. Normalmente, o diretório é C:\Program Files (x86) \Microsoft Visual Studio\Installer.
3. Execute o bootstrapper de instalação do Visual Studio. Você pode encontrar o bootstrapper na pasta Downloads com um nome de arquivo que segue um padrão ```vs_[Visual Studio edition]__*.exe```. Se não encontrar esse aplicativo, você poderá baixar o bootstrapper indo para a página [Downloads do Visual Studio](https://www.visualstudio.com/downloads/) e clicando em **baixar** para sua edição do Visual Studio. Execute o arquivo executável para redefinir os metadados de instalação.
4. Tente instalar ou atualizar o Visual Studio. Se o instalador continuar a falhar, vá para a etapa 4 imediatamente abaixo.
<br/>**Observação:** essa etapa reinstalará arquivos de instalação do Visual Studio e redefinirá os metadados de instalação. 

### <a name="step-4---report-a-problem"></a>Etapa 4 - relatar um problema
Em algumas situações, como aquelas relacionadas a arquivos corrompidos, os problemas talvez precisem ser resolvidos caso a caso:

1. Baixe o [Microsoft Visual Studio e a ferramenta de coleta de Log do .NET Framework](https://www.microsoft.com/en-us/download/details.aspx?id=12493) e execute-o. Essa ferramenta coleta e compila os logs de instalação disponíveis para instalações do Visual Studio, do .NET Framework e do SQL Server.
2. Abra o instalador do Visual Studio e clique em **Relatar um problema** para abrir a ferramenta de comentários do Visual Studio.
![Você pode pressionar Tab até acessar o botão Fornecer Comentários para abrir a ferramenta de comentários](media/report-a-problem.png)
3. Dê um título ao relatório de problemas e forneça detalhes relevantes. Clique em **Avançar** para ir até a seção **Anexos** e anexar o arquivo de log gerado (normalmente, o arquivo está em %TEMP%\vslogs.zip).
![Pressione Tab até acessar o botão Relatar Novo Problema e siga as etapas](media/problem-report-details.png)
4. Clique em **Avançar** para examinar o relatório de problemas e clique em **Enviar**.

### <a name="step-5---run-installcleanupexe-to-clean-up-installation-files"></a>Etapa 5 - Executar InstallCleanup.exe para limpar os arquivos de instalação
Como último recurso, você pode executar InstallCleanup.exe. InstallCleanup.exe é um utilitário que é fornecido com o instalador do Visual Studio e limpa os arquivos de instalação. Essa não é uma reinstalação completa. Esse utilitário exclui dados de cache e de instância para o Visual Studio 2017.

1. Fechar o instalador do Visual Studio.
2. Abrir um prompt de comando de administrador. Para fazer isso, execute estas etapas:
   * No menu **Iniciar**, clique em **Executar** (Iniciar + R).
   * Digite **cmd**.
   * Clique com o botão direito do mouse em **Prompt de Comando** e escolha **Executar como administrador**.
3. Digite o caminho completo do utilitário InstallCleanup.exe e passe a seguinte opção de linha de comando: -f. Por padrão, o caminho do utilitário é o seguinte:
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```
4. Execute novamente o bootstrapper descrito na Etapa 3.
5. Tente instalar ou atualizar o Visual Studio.

## <a name="how-to-troubleshoot-an-offline-installer"></a>Como solucionar problemas de um instalador offline
Aqui está uma tabela de problemas conhecidos e algumas soluções alternativas durante a instalação em um layout local que pode ajudar.

| Problema       | Item                   | Solução |
| ----------- | ---------------------- | -------- |
| Os usuários não têm acesso aos arquivos. | permissões (ACLs) | Lembre-se de ajustar as permissões (ACLs) para que elas concedam acesso de Leitura aos outros usuários *antes* de você compartilhar a instalação offline. |
| Falha na instalação de novas cargas de trabalho, novos componentes ou idiomas.  | `--layout`  | Verifique se você tem acesso à Internet se estiver instalando com base em um layout parcial e selecione as cargas de trabalho, os componentes ou idiomas que não estão disponíveis no layout anterior. |



