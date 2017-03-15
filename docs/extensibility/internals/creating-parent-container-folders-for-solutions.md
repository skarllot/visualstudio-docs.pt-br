---
title: "Criando pastas de contêiner pai para soluções | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 15
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
ms.openlocfilehash: 14f2c5fd0d85cf18b0c48cdc522ab9f35598ef8d
ms.lasthandoff: 02/22/2017

---
# <a name="creating-parent-container-folders-for-solutions"></a>Criando pastas de contêiner pai para soluções
Na fonte de controle de plug-in API versão 1.2, um usuário pode especificar um destino de controle de origem única raiz para todos os projetos da Web na solução. Essa única raiz é chamado de uma raiz de Unificação de Super (SUR).  
  
 Na fonte de controle de plug-in API versão 1.1, se o usuário adicionado a uma solução multiprojeto ao controle de origem, o usuário foi solicitado a especificar um destino de controle de origem para cada projeto da Web.  
  
## <a name="new-capability-flags"></a>Novos sinalizadores de recurso  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Novas funções  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE quase sempre cria uma pasta SUR ao adicionar uma solução ao controle de origem. Especificamente, isso é feito nos seguintes casos:  
  
-   O projeto é um compartilhamento de arquivo de projeto da Web.  
  
-   Existem diferentes unidades para o projeto e o arquivo de solução.  
  
-   Não há compartilhamentos diferentes para o projeto e o arquivo de solução.  
  
-   Projetos foram adicionados separadamente (em uma solução sob controle de origem).  
  
 Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] recomenda-se que o nome da pasta SUR ser o mesmo que o nome da solução sem a extensão. A tabela a seguir resume o comportamento em duas versões.  
  
|Recurso|tSource controle plug-in API versão 1.1|Versão 1.2 do API de plug-in de controle de origem|  
|-------------|----------------------------------------------|---------------------------------------------|  
|Adicionar solução ao SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Adicionar o projeto à solução de controle do código-fonte|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject() **Observação:** Visual Studio pressupõe que uma solução é um filho direto da SUR.|  
  
## <a name="examples"></a>Exemplos  
 A tabela a seguir lista os dois exemplos. Em ambos os casos, o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usuário é solicitado a fornecer um local de destino para a solução sob controle de origem até que o *user_choice* é especificado como um destino. Quando o user_choice for especificado, a solução e dois projetos são adicionados sem avisar o usuário para destinos de controle de origem.  
  
|Solução contém|Em locais de disco|Estrutura do banco de dados padrão|  
|-----------------------|-----------------------|--------------------------------|  
|sln1.sln<br /><br /> Web1<br /><br /> WEB2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot$\web2|$/*user_choice*/sln1<br /><br /> $/*user_choice * /C/Web1<br /><br /> $/*user_choice*/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/sln1<br /><br /> $/*user_choice * /D/web1<br /><br /> $/*user_choice * /sln1/win1|  
  
 SUR pastas e subpastas do são criadas independentemente da operação seja cancelada ou falha devido a um erro. Eles não são removidos automaticamente em condições de erro ou Cancelar.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]assume como padrão o comportamento da versão 1.1, se o plug-in de controle de origem não retornar `SCC_CAP_CREATESUBPROJECT` e `SCC_CAP_GETPARENTPROJECT` sinalizadores de recurso. Além disso, os usuários do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poderá reverter para o comportamento da versão 1.1, definindo o valor da seguinte chave como DWORD: 00000001:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD:&00000;001  
  
## <a name="see-also"></a>Consulte também  
 [Novidades na origem controle plug-in API versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
