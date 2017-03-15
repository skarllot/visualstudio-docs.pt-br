---
title: "Como: instalar um plug-in de controle do código-fonte | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
caps.latest.revision: 32
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: dde8fd31854f836f16a927ed9831ffb040f5c066
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-install-a-source-control-plug-in"></a>Como: instalar um plug-in de controle de origem
Criando um controle de fonte de plug-in envolve três etapas:  
  
1.  Crie uma DLL com as funções definidas na seção de referência de API de plug-in de controle de origem desta documentação.  
  
2.  Implemente as funções definidas pelo API de plug-in de controle de origem. Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chamadas para ele, disponibilizar interfaces e caixas de diálogo de plug-in.  
  
3.  Registre a DLL, tornando as entradas do registro apropriadas.  
  
## <a name="integration-with-visual-studio"></a>Integração com o Visual Studio  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]oferece suporte a plug-ins de controle de origem que estão em conformidade com a API de plug-in de controle de origem.  
  
### <a name="registering-the-source-control-plug-in"></a>Registrando o plug-in de controle de origem  
 Antes que possa chamar um ambiente de desenvolvimento integrado (IDE) em execução no sistema de controle de origem, primeiro ele deve localizar a fonte de DLL de plug-in que exporta a API de controle.  
  
##### <a name="to-register-the-source-control-plug-in-dll"></a>Para registrar a fonte de DLL de plug-in de controle  
  
1.  Adicione duas entradas na chave HKEY_LOCAL_MACHINE na subchave do SOFTWARE que especifica a subchave do nome da empresa seguido a subchave de nome de produto. O padrão é HKEY_LOCAL_MACHINE\SOFTWARE\\*[nome da empresa]*\\*[nome do produto]*\\*[entrada]* = valor. As duas entradas sempre são chamadas SCCServerName e SCCServerPath. Cada um é uma cadeia de caracteres regular.  
  
     Por exemplo, se o nome da empresa é Microsoft e seu produto de controle de origem é chamado SourceSafe, esse caminho de registro será HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe. Nessa subchave, a primeira entrada, SCCServerName, é uma cadeia de caracteres legível pelo usuário, nomear o seu produto. A segunda entrada, SCCServerPath, é o caminho completo para a fonte de controle DLL de plug-in que o IDE deve se conectar. Veja a seguir exemplos de entradas do registro:  
  
    |Exemplo de entrada de registro|Valor de exemplo|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|c:\vss\win32\ssscc.dll|  
  
    > [!NOTE]
    >  O SCCServerPath é o caminho completo para o plug-in do SourceSafe. O plug-in de controle de origem usará nomes de produtos e empresas diferentes mas os mesmos caminhos de entrada do registro.  
  
2.  As seguintes entradas de registro opcional podem ser usadas para modificar o comportamento do plug-in de controle de origem. Acesse essas entradas na subchave mesmo como SccServerName e SccServerPath.  
  
    -   A entrada HideInVisualStudioregistry pode ser usada se você não quiser que sua fonte-plug-in controle apareça na lista de seleção de plug-in de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Essa entrada também afetará a comutação automática para o plug-in de controle de origem. Um uso possível para essa entrada é se você fornecer um pacote de controle de origem que substitui o plug-in de controle de origem, mas deseja tornar mais fácil para o usuário migrar do usando o plug-in para o pacote de controle de origem de controle de origem. Quando o pacote de controle de origem estiver instalado, ele define essa entrada do registro, que oculta o plug-in.  
  
         HideInVisualStudio é um valor DWORD e é definido como 1 para ocultar o plug-in ou 0 para mostrar o plug-in. Se a entrada do registro não for exibido, o comportamento padrão é mostrar o plug-in.  
  
    -   A entrada de registro DisableSccManager pode ser usada para desativar ou ocultar o **iniciar \<servidor de controle de origem >** opção de menu que normalmente aparece sob o **arquivo** -> **controle de origem** submenu. Selecionando esse menu opção chamadas a [SccRunScc](../../extensibility/sccrunscc-function.md) função. O plug-in de controle de origem pode não oferecer suporte a um programa externo e, portanto, você talvez queira desativar ou até mesmo ocultar o **iniciar** opção de menu.  
  
         DisableSccManager é um valor DWORD é definido como 0 para habilitar o **iniciar \<servidor de controle de origem >** opção de menu, definido como 1 para desabilitar a opção de menu e definido como 2 para ocultar a opção de menu. Se essa entrada do registro não for exibido, o comportamento padrão é mostrar a opção de menu.  
  
    |Exemplo de entrada de registro|Valor de exemplo|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager|1|  
  
3.  Adicione a subchave SourceCodeControlProvider, sob a chave HKEY_LOCAL_MACHINE na subchave do SOFTWARE.  
  
     Sob essa subchave, a entrada do registro ProviderRegKey é definido como uma cadeia de caracteres que representa a subchave que você inseriu no registro na etapa 1. O padrão é HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey = SOFTWARE\\*[nome da empresa]*\\*[nome do produto]*.  
  
     A seguir está o conteúdo de exemplo para essa subchave.  
  
    |Entrada de registro|Valor de exemplo|  
    |--------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  O plug-in de controle de origem usará o mesmo subchave e nomes de entrada, mas o valor será diferente.  
  
4.  Crie uma subchave denominada InstalledSCCProviders sob a subchave SourceCodeControlProvider e, em seguida, coloque uma entrada sob essa subchave.  
  
     O nome dessa entrada é o nome legível pelo usuário do provedor (o mesmo que o valor especificado para a entrada SCCServerName) e o valor for, mais uma vez, a subchave criada na etapa 1. O padrão é HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\*[nome para exibição]* = SOFTWARE\\*[nome da empresa]*\\*[nome do produto]*.  
  
     Por exemplo:  
  
    |Exemplo de entrada de registro|Valor de exemplo|  
    |---------------------------|------------------|  
    |Visual SourceSafe HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Pode haver vários fonte controle plug-ins registrados dessa maneira. Isso é como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] localiza todos instalados plug-ins baseados na API de plug-in de controle de origem.  
  
## <a name="how-an-ide-locates-the-dll"></a>Como um IDE localiza a DLL  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE tem duas maneiras de localizar a fonte de DLL de plug-in de controle:  
  
-   Localize o controle de origem padrão plug-in e conectá-lo silenciosamente.  
  
-   Localize fonte registrada todos os plug-ins de controle, do qual o usuário escolhe um.  
  
 Para localizar a DLL da primeira forma, o IDE procura na subchave HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider para a entrada ProviderRegKey. O valor dessa entrada aponta para outra subchave. O IDE procurará uma entrada denominada SccServerPath nessa segunda subchave em HKEY_LOCAL_MACHINE. O valor dessa entrada aponta o IDE para a DLL.  
  
> [!NOTE]
>  O IDE não carregar DLLs de caminhos relativos (por exemplo,.\NewProvider.DLL). Especifique um caminho completo para a DLL (por exemplo, c:\Providers\NewProvider.DLL). Isso fortalece a segurança do IDE, impedindo o carregamento de DLLs de plug-in não autorizados ou representados.  
  
 Para localizar a DLL a segunda maneira, o IDE procura em todas as entradas na subchave HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders*.* Cada entrada tem um nome e um valor. O IDE exibe uma lista desses nomes para o usuário*.* Quando o usuário escolhe um nome, o IDE localiza o valor para o nome selecionado que aponta para uma subchave. O IDE procura uma entrada denominada SccServerPath nessa subchave em HKEY_LOCAL_MACHINE. O valor dessa entrada aponta o IDE para a DLL correta.  
  
 Um plug-in de controle de origem precisa oferecer suporte a duas formas de localizar a DLL e, consequentemente, defina ProviderRegKey, substituindo qualquer configuração anterior. Mais importante, ele deve se adicionar à lista de InstalledSccProviders para que o usuário possa ter uma escolha de quais plug-in de controle de origem para usar.  
  
> [!NOTE]
>  Como a chave HKEY_LOCAL_MACHINE é usada, plug-in de controle de origem apenas uma pode ser registrado como o controle de origem padrão plug-in em um determinado computador (no entanto, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] permite que os usuários determinem quais plug-in de controle de origem que desejam usar para uma determinada solução). Durante o processo de instalação, verifique se um plug-in de controle de origem já está definido; em caso afirmativo, pergunte ao usuário se deseja ou não definir o controle de origem novo plug-in que está sendo instalado como padrão. Durante a desinstalação, não remova outros subchaves do registro que são comuns ao controle de origem todos os plug-ins em HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider; Remova apenas a subchave SCC específico.  
  
## <a name="how-the-ide-detects-version-1213-support"></a>Como o IDE detecta a versão 1.2/1.3 suporte  
 Como does [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] detectar se uma funcionalidade do plug-in oferece suporte à API de plug-in de controle de origem versão 1.2 e 1.3? Para declarar um recurso avançado, o plug-in de controle de origem deve implementar a função correspondente.  
  
 Primeiro, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verifica o valor retornado pela chamada a [SccGetVersion](../../extensibility/sccgetversion-function.md). Ele deve ser maior ou igual a 1.2.  
  
 Em seguida, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] determina se o novo recurso específico tem suporte por meio do exame de `lpSccCaps` argumento o [SccInitialize](../../extensibility/sccinitialize-function.md).  
  
 Se estas duas condições forem atendidas, novas funções de suporte em versões 1.2 e 1.3 podem ser chamadas.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
