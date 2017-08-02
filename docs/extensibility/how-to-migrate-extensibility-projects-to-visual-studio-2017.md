---
title: 'Como: migrar projetos de extensibilidade para o Visual Studio 2017 | Documentos do Microsoft'
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5b6334c38a6c058f274498c06f8e07c934931910
ms.openlocfilehash: efd17a3317302fedcb9bd42aded7a38adee2f75f
ms.lasthandoff: 03/22/2017

---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Como: migrar projetos de extensibilidade para o Visual Studio 2017

Este documento explica como atualizar projetos de extensibilidade para 2017 do Visual Studio. Além de descrever como atualizar os arquivos de projeto, ele também descreve como atualizar da versão de manifesto de extensão 2 (v2 VSIX) para o nova versão 3 VSIX formato de manifesto (VSIX v3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Instalar o Visual Studio 2017 com cargas de trabalho necessárias

Verifique se que a instalação inclui as seguintes cargas de trabalho:

* Desenvolvimento de área de trabalho do .NET
* Desenvolvimento de extensões do Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Abra a solução VSIX em 2017 do Visual Studio

Todos os projetos do VSIX exigirá uma atualização de versão principal unidirecional para 2017 do Visual Studio.

O arquivo de projeto (por exemplo, *. csproj) será atualizado:

* MinimumVisualStudioVersion - agora definido como 15.0
* OldToolsVersion (se existir anteriormente)-agora definido como 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Atualizar o pacote do Microsoft.VSSDK.BuildTools NuGet

>**Observação:** se sua solução não referencia o pacote do Microsoft.VSSDK.BuildTools NuGet, você pode ignorar esta etapa.

Para criar sua extensão na v3 VSIX novas formato (versão 3), sua solução precisa ser compilado com as novas ferramentas de compilação VSSDK. Isso será instalado com o Visual Studio 2017, mas sua extensão de v2 VSIX pode estar mantendo uma referência a uma versão anterior por meio do NuGet. Nesse caso, você precisará instalar manualmente uma atualização do pacote do Microsoft.VSSDK.BuildTools NuGet para sua solução.

Para atualizar as referências de NuGet para Microsoft.VSSDK.BuildTools:

* Clique na solução e escolha **gerenciar pacotes NuGet para solução...**
* Navegue até o **atualizações** guia.
* Selecione Microsoft.VSSDK.BuildTools (versão mais recente).
* Pressione **atualização**.

![Ferramentas de compilação VSSDK](~/extensibility/media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Faça as alterações para o manifesto de extensão do VSIX

Para garantir que a instalação do usuário do Visual Studio tem todos os assemblies necessários para executar a extensão, especifique todos os componentes de pré-requisito ou pacotes no arquivo de manifesto de extensão. Quando um usuário tenta instalar a extensão, o VSIXInstaller verifica se todos os pré-requisitos estão instalados. Se alguns estiverem ausentes, o usuário precisará instalar os componentes ausentes como parte do processo de instalação de extensão.

>**Observação:** no mínimo, todas as extensões devem especificar o componente de editor do Visual Studio core como um pré-requisito.

* Edite o arquivo de manifesto de extensão (geralmente chamado de source.extension.vsixmanifest).
* Certifique-se de `InstallationTarget` inclui 15.0.
* Adicione os pré-requisitos de instalação necessários (conforme mostrado no exemplo abaixo).
  * Recomendamos que você especificar apenas as IDs de componente de pré-requisitos de instalação.
  * Consulte a seção no final deste documento para [instruções na identificação de IDs de componente](#finding-component-ids).

Exemplo:

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Opção: Usar o designer para fazer alterações para o manifesto de extensão do VSIX

Em vez de editar diretamente o XML do manifesto, você pode usar o novo **pré-requisitos** guia no Designer de manifesto para selecionar os pré-requisitos e o XML será atualizado para você.

>**Observação:** o Designer de manifesto só permitirá a seleção de componentes (não as cargas de trabalho ou pacotes) que estão instalados na instância atual do Visual Studio. Se você precisar adicionar um pré-requisito para uma carga de trabalho, pacote ou componente que não está instalado, edite o manifesto XML diretamente.

* Abra o arquivo source.extension.vsixmanifest [Design].
* Selecione **pré-requisitos** guia e pressione **novo** botão.

  ![Designer de manifesto VSIX](~/extensibility/media/vsix-manifest-designer.png)

* O **adicionar novo pré-requisito** janela será aberta.

  ![Adicionar vsix pré-requisito](~/extensibility/media/add-vsix-prerequisite.png)

* Clique no menu suspenso para **nome** e selecione o pré-requisito desejado.
* Atualize a versão, se necessário.

  >Observação: O campo de versão será preenchido com a versão do componente instalado no momento, com um intervalo até a abrangência de chave (mas não incluindo) a próxima versão principal do componente.

  ![Adicionar o pré-requisito de roslyn](~/extensibility/media/add-roslyn-prerequisite.png)

* Press **OK**.

## <a name="if-migrating-from-preview-4-or-preview-5"></a>Se a migração de visualização 4 ou 5 de visualização

* Substitua `SetupDependencies` com `Prerequisites` e mover os elementos do `Installer` elemento. `Prerequisites`encontrar agora diretamente dentro do `PackageManifest` elemento.
* [Opcional] Remover o `GenerateVsixV3` elemento. (Isso foi exigido na visualização 5 somente). O `GenerateVsixV3` elemento será ignorado em versões posteriores 5 de visualização.

## <a name="update-debug-settings-for-project"></a>Atualizar configurações de depuração de projeto

Se você deseja depurar sua extensão em uma instância experimental do Visual Studio, verifique se as configurações do projeto para **depurar** > **iniciar ação** tem o **Iniciar programa externo:** valor definido no arquivo devenv.exe da instalação do Visual Studio 2017.

Ele pode parecer com:

```
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe
```

![Iniciar programa externo](~/extensibility/media/start-external-program.png)

>**Observação:** depurar iniciar ação normalmente é armazenada na. csproj.user arquivo. Esse arquivo geralmente está incluído no arquivo. gitignore e, portanto, não é normalmente salvo com outros arquivos de projeto quando o compromisso de controle de origem. Assim, se você tiver extraídos sua solução atualizada do controle de origem é provavelmente que o projeto não terá nenhum valor definido para iniciar ação. Novos projetos do VSIX criados com o Visual Studio 2017 terá um. csproj.user arquivo criado com padrões apontando para o diretório de instalação atual do Visual Studio. No entanto se você estiver migrando uma extensão do VSIX v2, é provável que o. csproj.user arquivo irá conter referências para o diretório de instalação da versão do Visual Studio anterior. Definir o valor de **depurar** > **iniciar ação** permitirá que a instância experimental do Visual Studio correta iniciar quando você tenta depurar sua extensão.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Verifique se a extensão compilado corretamente (como um v3 VSIX)

* Compile o projeto do VSIX.
* Descompacte o VSIX gerado.
  * Por padrão, a vida do arquivo VSIX em bin/Debug ou bin/Release como. VSIX [YourCustomExtension].
  * Renomear arquivo. VSIX para. zip para exibir facilmente o conteúdo.
* Verificar a existência dos três arquivos:
  * vsixmanifest
  * manifest
  * Catalog.JSON

## <a name="check-when-all-required-prerequisites-are-installed"></a>Verificar quando todos os pré-requisitos necessários são instalados

Teste o VSIX instalada com êxito em um computador com os pré-requisitos necessários instalados.

>**Observação:** antes de instalar qualquer extensão, feche todas as instâncias do Visual Studio.

Ao tente instalar a extensão:

* No Visual Studio 2017

![Instalador VSIX no Visual Studio 2017](~/extensibility/media/vsixinstaller-vs-2017.png)

* Opcional: Verifique nas versões anteriores do Visual Studio.
  * Prova de compatibilidade com versões anteriores.
  * Deve funcionar para o Visual Studio 2012, o Visual Studio 2013, o Visual Studio 2015.
* Opcional: Verificar que o verificador de versão do instalador VSIX oferece uma opção de versões.
  * Inclui versões anteriores do Visual Studio (se instalado).
  * Inclui 2017 do Visual Studio.

Se o Visual Studio foi aberto recentemente, você poderá ver uma caixa de diálogo como esta:

![VS processos em execução](~/extensibility/media/vs-running-processes.png)

Aguarde os processos desligar ou encerrar as tarefas manualmente. Você pode encontrar os processos pelo nome listado ou com o PID listado entre parênteses.

>**Observação:** esses processos não serão automaticamente desligado enquanto uma instância do Visual Studio está em execução. Verifique se você encerrou todas as instâncias do Visual Studio no computador – inclusive os de outros usuários, e continuar tentar novamente.

## <a name="check-when-missing-the-required-prerequisites"></a>Verificar quando tem os pré-requisitos necessários

* Tentativa de instalar a extensão em um computador com Visual Studio 2017 que não CONTÊM todos os componentes definidos nos pré-requisitos (acima).
* Verifique se a instalação identifica o componente ausente/s e lista como um pré-requisito no VSIXInstaller.
* Observação: Elevação será obrigatória se todos os pré-requisitos precisam ser instalados com a extensão.

![pré-requisito ausente vsixinstaller](~/extensibility/media/vsixinstaller-missing-prerequisite.png)

## <a name="deciding-on-components"></a>Decidindo sobre componentes

Ao procurar as suas dependências, você encontrará uma dependência poderia ser vários componentes. Para determinar quais dependências, você deve especificar como o pré-requisito, sugerimos que você escolher um componente que tem uma funcionalidade semelhante a sua extensão e para considerar os usuários e que tipo de componentes seria muito provavelmente terem instalado ou não me incomodaria instalando. Sugerimos também criando suas extensões de forma que os pré-requisitos necessários atendem apenas o mínimo que permitirão que a extensão a ser executada e recursos adicionais de sejam fique inativo se determinados componentes não são detectados.

Para fornecer mais orientação, identificamos alguns tipos comuns de extensão e seus pré-requisitos sugeridos:

Tipo de extensão | Nome de Exibição |    Id
--- | --- | ---
Editor | Editor de núcleo do Visual Studio    | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# e Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Núcleo de carga de trabalho da área de trabalho gerenciada | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Depurador | Depurador Just-In-Time | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="finding-component-ids"></a>Localizar IDs de componente

A lista de componentes, classificados por produto Visual Studio está em [IDs de componente e de carga de trabalho do Visual Studio 2017](https://aka.ms/vs2017componentIDs). Use essas IDs de componente para suas IDs de pré-requisito em seu manifesto.

Se você não souber qual componente contém um download de binário, específico do [componente-> Planilha de mapeamento binário](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017 ComponentBinaryMapping.xlsx

Há quatro colunas na planilha do Excel: **nome do componente**, **ComponentId**, **versão**, e **binário / nomes de arquivo**.  Você pode usar os filtros para pesquisar e localizar os binários e componentes específicos.

Para todas as suas referências, determine quais são no componente principal editor (Microsoft.VisualStudio.Component.CoreEditor).  No mínimo, é necessário o principal componente de editor a ser especificado como um pré-requisito para todas as extensões. As referências restantes que não estão no editor de núcleo, adicionar filtros a **binários / nomes de arquivos** seção para encontrar componentes que tenham qualquer subconjunto essas referências.

Exemplos:

* Se você tiver uma extensão de depurador e sabe que seu projeto possui uma referência ao VSDebugEng.dll e VSDebug.dll, clique no botão de filtro no **binários / nomes de arquivos** cabeçalho.  Pesquise por "VSDebugEng.dll" e selecione Okey.  Em seguida, clique no botão de filtro a **binários / nomes de arquivos** cabeçalho novamente e procure "VSDebug.dll".  Marque a caixa de seleção "Adicionar seleção atual ao filtro" e selecione Okey.  Agora examine a **nome do componente** para localizar um componente mais relacionadas ao tipo de extensão. Neste exemplo, você pode escolher o Just-In-Time do depurador e adicioná-lo ao seu vsixmanifest.
* Se você souber que seu projeto lida com elementos do depurador, você pode pesquisar no "depurador" na caixa de filtro de pesquisa para ver quais componentes contêm o depurador em seu nome.

