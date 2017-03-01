---
title: "Registro e seleção (VSPackage de controle de origem) | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: 34
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
ms.openlocfilehash: 693955c38d4d53418a92357e54bfc7c2965bdc3e
ms.lasthandoff: 02/22/2017

---
# <a name="registration-and-selection-source-control-vspackage"></a>Registro e seleção (VSPackage de controle de origem)
Um controle de origem VSPackage deve ser registrado para expô-lo para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Se mais de um controle de origem VSPackage é registrado, o usuário pode selecionar quais VSPackage carregar em momentos apropriados. Consulte [VSPackages](../../extensibility/internals/vspackages.md) para obter mais detalhes sobre os VSPackages e como registrá-los.  
  
## <a name="registering-a-source-control-package"></a>Registrar um pacote de controle de origem  
 O pacote de controle de origem está registrado para que o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente pode encontrar ela e consulta de seus recursos com suporte. Isso está de acordo com um esquema de carregamento de atraso no qual uma instância de um pacote é criada somente quando seus recursos e comandos são necessários ou explicitamente solicitou.  
  
 Os VSPackages colocar as informações em uma chave de registro de versão específica, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*x. y*, onde *X* é o número de versão principal e *Y* é o número de versão secundária. Essa prática fornece a capacidade de oferecer suporte à instalação lado a lado de várias versões do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface do usuário (IU) dá suporte à seleção entre o controle de origem instalado vários plug-ins (via o pacote adaptador de controle de origem), bem como controle de origem VSPackages. Pode haver apenas um plug-in de controle de origem ativa ou VSPackage por vez. No entanto, conforme descrito abaixo, o IDE permite alternar entre os plug-ins de controle de origem e os VSPackages através de um solução baseada troca pacote mecanismo automático. Há alguns requisitos na parte do controle de origem VSPackage para habilitar esse mecanismo de seleção.  
  
### <a name="registry-entries"></a>Entradas do registro  
 Um pacote de controle de origem precisa de três GUIDs privadas:  
  
-   GUID do pacote: Esse é o GUID principal para o pacote que contém a implementação de controle de origem (chamada ID_Package nesta seção).  
  
-   GUID de controle de origem: Isso é um GUID para o controle de origem VSPackage usado para registrar com o fragmento de código de controle de origem Studio Visual e também é usado como um contexto de interface do usuário do comando GUID. O serviço de controle de origem GUID é registrado sob o GUID do controle de origem. No exemplo, o GUID do controle de origem é chamado ID_SccProvider.  
  
-   GUID de serviço de controle de origem: Este é o serviço privado GUID usado pelo Visual Studio (chamado SID_SccPkgService nesta seção). Além disso, o pacote de controle de origem precisa definir outros GUIDs para VSPackages, janelas de ferramentas e assim por diante.  
  
 As seguintes entradas do registro devem ser feitas por um controle de origem VSPackage:  
  
|Nome da chave|Entradas|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|(padrão) = rg_sz: {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|(padrão) = rg_sz:\<nome amigável do pacote ><br /><br /> Serviço = rg_sz: {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|(padrão) = rg_sz: #\<ID de recurso para o nome localizado ><br /><br /> Pacote = rg_sz: {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Observe que o nome da chave, `SourceCodeControl`, já é usado por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e não está disponível como uma opção para \<PackageName >.)|(padrão) = rg_sz: {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>Selecionando um pacote de controle de origem  
 Vários de plug-ins baseados na API de plug-in de controle de origem e os VSPackages podem ser registrados simultaneamente de controle de origem. O processo de selecionar um plug-in de controle de origem ou VSPackage deve garantir que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carrega o plug-in ou VSPackage no momento apropriado e pode adiar o carregamento de componentes desnecessários até que eles sejam necessários. Além disso, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Remova toda interface do usuário da outros VSPackages inativos, incluindo itens de menu, caixas de diálogo e barras de ferramentas e exibir a interface do usuário para o VSPackage ativo.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]carrega um controle de origem VSPackage quando qualquer uma das seguintes operações é executada:  
  
-   Solução é aberta (quando a solução estiver sob controle de origem).  
  
     Quando uma solução ou projeto sob controle do código-fonte é aberto, o IDE faz com que o controle de origem VSPackage que foi designado para a solução a ser carregado.  
  
-   Qualquer um dos comandos de menu de controle da fonte de VSPackage são executados.  
  
 Um controle de origem que VSPackage deve carregar todos os componentes que é necessário somente quando eles são realmente será usado (conhecido também como carregamento atrasado).  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>Troca automática com base em solução de VSPackage  
 Manualmente, você pode trocar os VSPackages de controle de origem por meio de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **opções** caixa de diálogo no **controle de origem** categoria. Troca automática de pacotes baseados em soluções significa que um pacote de controle de origem que tenha sido designado para uma determinada solução é automaticamente definido como ativa quando essa solução é aberta. Cada pacote de controle de origem deve implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Controla a alternância entre os dois plug-ins de controle (Implementando a API de plug-in de controle de origem) de origem e os VSPackages do controle de origem.  
  
 O pacote de adaptador de controle de origem é usado para alternar para qualquer baseado na API de plug-in de controle de origem plug-in. O processo de alternar para o pacote intermediário do adaptador de controle de origem e determinar quais plug-in de controle de origem deve ser definido como ativo ou inativo é transparente ao usuário. O pacote do adaptador está sempre ativo quando qualquer plug-in de controle de origem está ativo. Alternando entre dois valores de plug-ins de controle de origem simplesmente carregar e descarregar a DLL de plug-in. No entanto, alternando para um controle da fonte de VSPackage, envolve a interagir com o IDE para carregar o VSPackage apropriado.  
  
 Um controle de fonte VSPackage é chamado quando qualquer solução é aberta e a chave do registro para o VSPackage está no arquivo de solução. Quando a solução for aberta, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] localiza o valor do registro e carrega o controle de origem apropriada VSPackage. Os VSPackages todo o controle de origem deve ter as entradas do Registro descritas acima. Uma solução sob controle de origem está marcada como sendo associada a um controle de origem em particular VSPackage. Os VSPackages deve implementar de controle de origem a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>Habilitar automática com base em solução VSPackage permutação.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Interface do usuário para seleção de pacote e mudança de Visual Studio  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Fornece uma interface do usuário para controle de origem VSPackage e seleção de plug-in no **opções** caixa de diálogo sob o **controle de origem** categoria. Ele permite que o usuário selecione o plug-in de controle de origem ativa ou VSPackage. Inclui uma lista suspensa:  
  
-   Todos os pacotes de controle de origem instalados  
  
-   Todos instalados plug-ins de controle de origem  
  
-   Opção um "none", que desabilita o controle do código fonte  
  
 A interface de usuário para a opção de controle de origem ativa está visível. A seleção de VSPackage oculta a interface do usuário para o VSPackage anterior e mostra a interface do usuário para uma nova. O VSPackage ativo é selecionado em uma base por usuário. Se um usuário tiver várias cópias de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] abrir simultaneamente, cada um pode usar um VSPackage ativo diferente. Se vários usuários fizerem logon no mesmo computador, cada usuário pode ter instâncias separadas do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] abrir, cada um com um VSPackage ativo diferente. Quando várias instâncias do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fechado por um usuário, o controle de origem VSPackage que estava ativa para a última solução aberta se torna o controle da fonte padrão VSPackage, sejam definidos ativos na reinicialização.  
  
 Diferentemente das versões anteriores do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], uma reinicialização do IDE não é a única maneira de alternar os VSPackages de controle de origem. Seleção de VSPackage é automática. Alternância de pacotes exige privilégios de usuário do Windows (não administrador ou usuário avançado).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [Recursos](../../extensibility/internals/source-control-vspackage-features.md)   
 [Criando um controle da fonte de plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [VSPackages](../../extensibility/internals/vspackages.md)
