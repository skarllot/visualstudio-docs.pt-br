---
title: "Alterações significativas em extensibilidade do Visual Studio de 2017 | Microsoft Docs"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
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
ms.translationtype: MT
ms.sourcegitcommit: 17defdd0b96ec1c3273fc6b845af844b031a4a17
ms.openlocfilehash: ac7a99673eb4dc23dd53a46c3c93fd735325c255
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Alterações de extensibilidade do Visual Studio de 2017

Com o Visual Studio de 2017, estamos oferecendo um [mais rápida e leve experiência de instalação do Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer) que reduz o impacto do Visual Studio em sistemas de usuário, dando aos usuários maior preferência sobre os recursos e cargas de trabalho que estão instalados. Para dar suporte a esses aprimoramentos, fez alterações para o modelo de extensibilidade e fez algumas alterações de quebra de extensibilidade do Visual Studio. Este documento descreve os detalhes técnicos dessas alterações e que pode ser feito para solucioná-los. Observe que algumas informações são detalhes de implementação de point-in-time e podem ser alteradas posteriormente.

## <a name="changes-affecting-vsix-format-and-installation"></a>Alterações que afetam a instalação e o formato do VSIX

Estamos introduzindo o v3 VSIX formato (versão 3) para dar suporte a experiência de instalação leve.

Alterações no formato VSIX incluem:

* Declaração de pré-requisitos de instalação. Para fornecer a promessa de uma leve, fast-instalando o Visual Studio, o instalador agora oferece mais opções de configuração para os usuários. Como resultado, para garantir que os recursos e componentes necessários por uma extensão são instalados, serão necessário extensões declarar suas dependências.
  * O instalador do Visual Studio de 2017 oferecerá automaticamente para adquirir e instalar os componentes necessários para o usuário como parte da instalação sua extensão.
  * Os usuários também serão avisados ao tentar instalar uma extensão que não foi criada usando o novo formato VSIX v3, mesmo se elas foram marcadas em seu manifesto como direcionando a versão 15.0.
* Recursos aprimorados para o formato do VSIX. Para entregar um [instalação de baixo impacto](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install) do Visual Studio que também oferece suporte a instalações lado a lado, nós não salvar a maioria dos dados de configuração no registro do sistema e foram movidos para assemblies do Visual Studio específicos fora do GAC. Também aumentamos as capacidades do formato VSIX e mecanismo de instalação de VSIX, permitindo que você use a ele em vez de um MSI ou EXE para instalar as extensões para alguns tipos de instalação.

  Os novos recursos incluem:

  * Registro para a instância especificada do Visual Studio.
  * Instalação fora do [pasta extensões](set-install-root.md).
  * Detecção da arquitetura do processador.
  * Dependência de pacotes de idiomas separados por idioma.
  * Instalação com [suporte a NGEN](ngen-support.md).

## <a name="building-an-extension-for-visual-studio-2017"></a>Criando uma extensão para o Visual Studio de 2017

Designer de ferramentas para a criação do novo formato do manifesto do VSIX v3 agora está disponível no Visual Studio de 2017. Consulte o documento que acompanha [como: migrar projetos de extensibilidade para Visual Studio de 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) para obter detalhes sobre como usar as ferramentas de designer ou fazer atualizações manuais ao projeto e o manifesto para desenvolver extensões do VSIX v3.

## <a name="change-visual-studio-user-data-path"></a>Alteração: Caminho de dados de usuário do Visual Studio

Anteriormente, apenas uma instalação de cada versão principal do Visual Studio pode existir em cada computador. Para dar suporte a instalações lado a lado do Visual Studio de 2017, vários caminhos de dados de usuário para o Visual Studio podem existir no computador do usuário.

Código em execução dentro do processo do Visual Studio deve ser atualizado para usar o Gerenciador de configurações do Visual Studio. Código executado fora do processo do Visual Studio pode localizar o caminho de usuário de uma instalação do Visual Studio específico [seguindo as diretrizes aqui](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Alteração: Cache de Assembly Global (GAC)

A maioria dos assemblies de núcleo do Visual Studio não são mais instalados no GAC. As seguintes alterações foram feitas para que o código em execução no processo do Visual Studio ainda pode encontrar os assemblies necessários em tempo de execução.

> [!NOTE]
> [INSTALLDIR] abaixo refere-se para o diretório raiz de instalação do Visual Studio. VSIXInstaller.exe automaticamente irá popular isso, mas para escrever código de implantação personalizada, leia [localizando o Visual Studio](locating-visual-studio.md).

* Assemblies que só foram instalados no GAC:
  * Esses assemblies estão instalados em \Common7\IDE [INSTALLDIR]\, [INSTALLDIR] \Common7\IDE\PublicAssemblies ou \Common7\IDE\PrivateAssemblies [INSTALLDIR]. Essas pastas são parte dos caminhos de investigação do processo do Visual Studio.
* Assemblies que foram instalados em um caminho de investigação não e no GAC:
  * A cópia no GAC foi removida da instalação.
  * Um arquivo .pkgdef foi adicionado para especificar uma entrada de base de código para o assembly.

    Por exemplo:
    
    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    Em tempo de execução, o subsistema de pkgdef do Visual Studio mesclar essas entradas no arquivo de configuração de tempo de execução do processo do Visual Studio (em [VSAPPDATA]\devenv.exe.config) como [ `<codeBase>` ](https://msdn.microsoft.com/en-us/library/efs781xb(v=vs.110).aspx) elementos. Essa é a maneira recomendada para permitir que o processo do Visual Studio encontrar o assembly, porque ela evita pesquisar caminhos de investigação.

### <a name="reacting-to-this-breaking-change"></a>Reagindo para essa alteração de quebra

* Se a extensão estiver em execução no processo do Visual Studio:
  * O código será capaz de encontrar assemblies de núcleo do Visual Studio.
  * Considere o uso de um arquivo .pkgdef para especificar um caminho para os assemblies, se necessário.
* Se a extensão estiver em execução fora do processo do Visual Studio:
  * Considere a possibilidade de busca de assemblies de núcleo do Visual Studio em \Common7\IDE [INSTALLDIR]\, [INSTALLDIR] \Common7\IDE\PublicAssemblies ou \Common7\IDE\PrivateAssemblies [INSTALLDIR] usando o resolvedor de arquivo ou assembly de configuração.

## <a name="change-reduce-registry-impact"></a>Alteração: Reduzir o impacto do registro

### <a name="global-com-registration"></a>Registro global de COM

* Anteriormente, o Visual Studio instalado várias chaves de registro para as seções HKEY_CLASSES_ROOT e HKEY_LOCAL_MACHINE para dar suporte a registro COM nativo. Para eliminar esse impacto, o Visual Studio agora usa [ativação sem registro de componentes COM](https://msdn.microsoft.com/en-us/library/ms973913.aspx).
* Como resultado, a maioria dos TLB / OLB / arquivos DLL em % ProgramFiles (x86) %\Common Files\Microsoft Shared\MSEnv não são instalados por padrão pelo Visual Studio. Agora, esses arquivos são instalados em [INSTALLDIR] com correspondentes manifestos COM sem registro usados pelo processo de host do Visual Studio.
* Como resultado, o código externo que se baseia no registro global de COM para interfaces de COM do Visual Studio não encontrará esses registros. Código em execução dentro do processo do Visual Studio não verá uma diferença.

### <a name="visual-studio-registry"></a>Registro do Visual Studio

* Anteriormente, o Visual Studio instalado várias chaves de registro em seções HKEY_LOCAL_MACHINE e HKEY_CURRENT_USER do sistema em uma chave específica do Visual Studio:
  * HKLM\Software\Microsoft\VisualStudio\\**versão**: as chaves de Registro criadas pela instaladores MSI e extensões por máquina.
  * HKCU\Software\Microsoft\VisualStudio\\**versão**: chaves de Registro criadas pelo Visual Studio para armazenar configurações específicas do usuário.
  * HKCU\Software\Microsoft\VisualStudio\\**versão**_Config: uma cópia da chave de HKLM do Visual Studio acima, mais as chaves do registro mesclado de arquivos .pkgdef por extensões.
* Para reduzir o impacto sobre o registro, o Visual Studio agora usa o [RegLoadAppKey](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724886(v=vs.85).aspx) função para armazenar as chaves do registro em um arquivo binário privado em [VSAPPDATA]\privateregistry.bin. Somente um número muito pequeno de chaves do Visual Studio específicos permanecem no registro do sistema.
* O código existente em execução dentro do processo do Visual Studio não é afetado. O Visual Studio redirecionará todas as operações de registro na chave HKCU Visual Studio específicos no registro particular. Lendo e gravando em outros locais do registro continuarão a usar o registro do sistema.
* Código externo será necessário carregar e ler este arquivo para entradas de registro do Visual Studio.

### <a name="reacting-to-this-breaking-change"></a>Reagindo para essa alteração de quebra

* Código externo deve ser convertido para usar a ativação sem registro de componentes COM também.
* Componentes externos podem encontrar o local do Visual Studio [seguindo as diretrizes aqui](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup).
* É recomendável que componentes externos é usar o [Gerenciador de configurações externo](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.settings.externalsettingsmanager.aspx) em vez de ler/gravar diretamente para as chaves de registro do Visual Studio.
* Verifique se os componentes de que sua extensão está usando podem ter implementado outra técnica para o registro. Por exemplo, extensões de depurador poderá tirar proveito do novo [msvsmon registro arquivo JSON COM](migrate-debugger-COM-registration.md).

## <a name="change-lightweight-solution-load"></a>Alteração: Carga de solução leve

Carga de solução leve (LSL) reduz o tempo de carregamento da solução não totalmente Carregando projetos até que o usuário começa a trabalhar com eles. Isso pode afetar as extensões que supor que um projeto é completamente carregado. Consulte [Lightweight solução carga](lightweight-solution-load-extension-impact.md) para saber se sua extensão pode ser afetada e obter orientação sobre como atualizar sua extensão.

