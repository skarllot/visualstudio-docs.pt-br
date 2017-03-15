---
title: "Alterações significativas na extensibilidade do Visual Studio 2017 | Documentos do Microsoft"
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
translationtype: Machine Translation
ms.sourcegitcommit: 221f4911981deec0330f76a82c0cc8a1b968e56e
ms.openlocfilehash: 081a569fc7e38fecc8cc1ae5b0f8138ae8f25521
ms.lasthandoff: 02/22/2017

---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Alterações na extensibilidade do Visual Studio 2017

>**Observação:** esta documentação é preliminar e com base na versão RC do Visual Studio 2017.

Com o Visual Studio de 2017, estamos oferecendo uma [mais rápida e leve experiência de instalação do Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer) que reduz o impacto do Visual Studio em sistemas de usuário, dando aos usuários maior escolha sobre os recursos que estão instalados e cargas de trabalho. Para oferecer suporte a esses aperfeiçoamentos, fez alterações no modelo de extensibilidade e fez algumas alterações para extensibilidade do Visual Studio. Este documento descreve os detalhes técnicos dessas alterações e que pode ser feito para solucioná-los. Observe que algumas informações são detalhes de implementação de point-in-time e podem ser alteradas posteriormente.

## <a name="changes-affecting-vsix-format-and-installation"></a>Alterações que afetam o formato do VSIX e instalação

Estamos introduzindo o v3 VSIX formato (versão 3) para oferecer suporte a experiência de instalação leve.

Alterações no formato VSIX incluem:

* Declaração de pré-requisitos para a instalação. Para cumprir a promessa de uma leve, fast-instalando o Visual Studio, o instalador agora oferece mais opções de configuração para os usuários. Como resultado, para garantir que os recursos e componentes necessários para uma extensão são instalados, serão necessário extensões declarar suas dependências.
  * Com a versão RC, o instalador do Visual Studio 2017 automaticamente se oferecerá para adquirir e instalar os componentes necessários para o usuário como parte da instalação sua extensão.
  * Os usuários também serão avisados quando tentar instalar uma extensão que não foi criada usando o novo formato VSIX v3, mesmo se eles foram marcados em seu manifesto como direcionando a versão 15.0.
* Recursos aprimorados para o formato do VSIX. Fornecer um [instalação de baixo impacto](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install) do Visual Studio que também oferece suporte a instalações lado a lado, nós não salvar mais dados de configuração no registro do sistema e movidos assemblies do Visual Studio específicos fora do GAC. Também aumentamos as capacidades do formato do VSIX e mecanismo de instalação do VSIX, permitindo que você use a ele, em vez de um MSI ou EXE para instalar as extensões para alguns tipos de instalação.

  Os novos recursos incluem:

  * Registro para a instância especificada do Visual Studio.
  * Instalação de fora a [pasta extensões](set-install-root.md).
  * Detecção da arquitetura do processador.
  * Dependência de pacotes de idiomas separados de idioma.
  * Instalação com [suporte NGEN](ngen-support.md).

## <a name="building-an-extension-for-visual-studio-2017"></a>Criando uma extensão para o Visual Studio 2017

Designer de ferramentas para a criação do novo formato do manifesto VSIX v3 agora está disponível no Visual Studio 2017. Consulte o documento [como: migrar projetos de extensibilidade para Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) para obter detalhes sobre como usar as ferramentas de designer ou fazer atualizações manuais ao projeto e manifesto para desenvolver extensões de v3 VSIX.

## <a name="change-visual-studio-user-data-path"></a>Alteração: Caminho de dados de usuário do Visual Studio

Anteriormente, apenas uma instalação de cada versão principal do Visual Studio pode existir em cada computador. Para oferecer suporte a instalações lado a lado do Visual Studio 2017, vários caminhos de dados de usuário para o Visual Studio podem existir no computador do usuário.

Código em execução dentro do processo do Visual Studio deve ser atualizado para usar o Gerenciador de configurações do Visual Studio. Código em execução fora de processo do Visual Studio pode encontrar o caminho de usuário de uma instalação específica do Visual Studio [seguindo as diretrizes aqui](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup).

## <a name="change-global-assembly-cache-gac"></a>Alteração: Cache de Assembly Global (GAC)

A maioria dos assemblies de núcleo do Visual Studio não são mais instalados no GAC. As seguintes alterações foram feitas para que o código em execução no processo do Visual Studio ainda pode encontrar os assemblies necessários no tempo de execução.

* Assemblies que só foram instalados no GAC:
  * Esses assemblies estão instalados em %VsFolder%\Common7\IDE\, %VsFolder%\Common7\IDE\PublicAssemblies ou % VsFolder%\Common7\IDE\PrivateAssemblies. Essas pastas são parte dos caminhos de investigação do processo do Visual Studio.
* Assemblies que foram instalados em um caminho não investigação e no GAC:
  * A cópia no GAC foi removida da configuração.
  * Um arquivo pkgdef foi adicionado para especificar uma entrada de base de código do assembly.

    Por exemplo:
    
    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    Em tempo de execução, o subsistema do Visual Studio pkgdef mesclar essas entradas no arquivo de configuração de tempo de execução do processo do Visual Studio (em % VsAppDataFolder%\devenv.exe.config) como [ `<codeBase>` ](https://msdn.microsoft.com/en-us/library/efs781xb(v=vs.110).aspx) elementos. Essa é a maneira recomendada para permitir que o processo do Visual Studio encontrar o assembly, porque evita pesquisando por meio de caminhos de investigação.

### <a name="reacting-to-this-breaking-change"></a>Reagir a essa alteração de quebra

* Se sua extensão é executado dentro do processo do Visual Studio:
  * Seu código será capaz de encontrar os assemblies de núcleo do Visual Studio.
  * Considere o uso de um arquivo pkgdef para especificar um caminho para os assemblies, se necessário.
* Se a extensão estiver em execução fora do processo do Visual Studio:
  * Considere procurando assemblies de núcleo do Visual Studio em %VsFolder%\Common7\IDE\, %VsFolder%\Common7\IDE\PublicAssemblies ou %VsFolder%\Common7\IDE\PrivateAssemblies usando o resolvedor de arquivo ou assembly de configuração.

## <a name="change-reduce-registry-impact"></a>Alteração: Reduzir o impacto do registro

### <a name="global-com-registration"></a>Registro global de COM

* Visual Studio instalado anteriormente, muitas chaves do registro para as seções HKEY_CLASSES_ROOT e HKEY_LOCAL_MACHINE para dar suporte a registro COM nativo. Para eliminar esse impacto, o Visual Studio agora usa [ativação sem registro para componentes COM](https://msdn.microsoft.com/en-us/library/ms973913.aspx).
* Como resultado, a maioria dos TLB / OLB / arquivos DLL em % ProgramFiles (x86) %\Common Files\Microsoft Shared\MSEnv não são instalados por padrão pelo Visual Studio. Agora, esses arquivos são instalados em % VsFolder % com correspondentes manifestos COM sem registro usados pelo processo de host do Visual Studio.
* Como resultado, o código externo que se baseia no registro global de COM para interfaces de COM do Visual Studio não encontrará esses registros. Código em execução dentro do processo do Visual Studio não verá uma diferença.

### <a name="visual-studio-registry"></a>Registro do Visual Studio

* Visual Studio instalado anteriormente, muitas chaves do registro em HKEY_LOCAL_MACHINE e HKEY_CURRENT_USER seções em uma chave específica do Visual Studio do sistema:
  * HKLM\Software\Microsoft\VisualStudio\\**versão**: chaves de Registro criadas pelos instaladores MSI e extensões de por máquina.
  * HKCU\Software\Microsoft\VisualStudio\\**versão**: chaves de Registro criadas pelo Visual Studio para armazenar configurações específicas do usuário.
  * HKCU\Software\Microsoft\VisualStudio\\**versão**_Config: uma cópia do Visual Studio HKLM chave acima, além de chaves do registro mesclado de arquivos. pkgdef pelas extensões.
* Para reduzir o impacto sobre o registro, o Visual Studio agora usa o [RegLoadAppKey](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724886(v=vs.85).aspx) função para armazenar as chaves do registro em um arquivo binário privado em % VsAppDataFolder%\privateregistry.bin. Somente um número muito pequeno de chaves do Visual Studio específicas permanecem no registro do sistema.
* Código existente em execução dentro do processo do Visual Studio não é afetado. Visual Studio redirecionará todas as operações de registro na chave HKCU Visual Studio específicos no registro particular. Lendo e gravando em outros locais do registro continuarão a usar o registro do sistema.
* Código externo será necessário carregar e ler este arquivo para entradas de registro do Visual Studio.

### <a name="reacting-to-this-breaking-change"></a>Reagir a essa alteração de quebra

* Código externo deve ser convertido para usar a ativação sem registro de componentes também.
* Componentes externos podem encontrar o local do Visual Studio [seguindo as diretrizes aqui](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup).
* Recomendamos que usam componentes externos a [externo Settings Manager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.settings.externalsettingsmanager.aspx) em vez de ler/gravar diretamente para as chaves de registro do Visual Studio.
* Verifique se os componentes que está usando sua extensão podem ter implementado outra técnica para o registro. Por exemplo, extensões de depurador poderá tirar proveito do novo [msvsmon registro arquivo JSON COM](migrate-debugger-COM-registration.md).

## <a name="change-lightweight-solution-load"></a>Alteração: Carga de solução leve

Carga de solução leve (LSL) reduz o tempo de carregamento de solução não totalmente Carregando projetos até que o usuário começar a trabalhar com eles. Isso pode afetar extensões que consideram que um projeto foi completamente carregado. Consulte [carga de solução leve](lightweight-solution-load-extension-impact.md) para saber se sua extensão pode ser afetada e obter orientação sobre como atualizar sua extensão.

