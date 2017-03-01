---
title: "Cenários de instalação de VSPackage | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, deployment considerations
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 21
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
ms.openlocfilehash: f2de7777fb4a8b0e215e8619a1a0bf2216fa58f8
ms.lasthandoff: 02/22/2017

---
# <a name="vspackage-setup-scenarios"></a>Cenários de instalação de VSPackage
É importante criar seu instalador VSPackage flexibilidade. Por exemplo, talvez seja necessário liberar um patch de segurança no futuro, ou você pode alterar uma estratégia de negócios que exige suporte a controle de versão completo lado a lado.  
  
 Em [suporte a várias versões do Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), você pode ler sobre as vantagens e problemas de suporte a instalações lado a lado do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] com instalações lado a lado ou compartilhadas do seu VSPackage. Em resumo, os VSPackages lado a lado lhe dão mais flexibilidade para oferecer suporte a novos recursos do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Os cenários abordados neste tópico não são suas únicas opções, mas eles são apresentados como práticas recomendadas sugeridas.  
  
## <a name="components-privacy-and-sharing"></a>Componentes, privacidade e compartilhamento  
  
##### <a name="make-your-components-independent"></a>Verifique os componentes independentes  
 Depois de identificar e preencher um componente, atribua um `GUID`e implantar o componente, você não pode alterar sua composição. Se você alterar a composição de um componente, o componente resultante deve ser um novo componente com um novo `GUID`. Com esses fatos, a maior flexibilidade de controle de versão é proporcionada pelo tornando cada unidade auto-suficiente, independente do componente. Para obter mais informações sobre as regras que regem os componentes, consulte [alterar o código do componente](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) e [o que acontece se o componente de regras são divididos?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Não misture recursos compartilhados e particulares em um componente  
 Contagem de referência ocorre no nível do componente. Consequentemente, a combinação de recursos compartilhados e particulares em um componente torna impossível atualizar recursos particulares, como um arquivo executável, sem substituir também recursos compartilhados. Este cenário cria problemas de compatibilidade com versões anteriores e o impede de criar o recurso lado a lado.  
  
 Por exemplo, os valores do registro usada para registrar o VSPackage com o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] deve ser mantido em um componente separado de um usado para registrar o VSPackage com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Valores de registro ou arquivos compartilhados vá em outro componente.  
  
## <a name="scenario-1-shared-vspackage"></a>Cenário 1: Compartilhados VSPackage  
 Nesse cenário, um VSPackage compartilhado (um binário único que oferece suporte a várias versões do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) é fornecido em um pacote do Windows Installer. Registrando com cada versão do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é controlada pelos recursos selecionáveis pelo usuário. Isso também significa que quando atribuído para separar os recursos, cada componente pode ser selecionada individualmente para instalação ou desinstalação, colocando o usuário no controle de integrar o VSPackage versões diferentes do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. (Consulte [recursos do Windows Installer](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) para obter mais informações sobre como usar recursos em pacotes do Windows Installer.)  
  
 ![Gráfico de VSPackage compartilhado do VS](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")  
Instalador de VSPackage compartilhado  
  
 Conforme mostrado na ilustração, componentes compartilhados fazem parte do recurso Feat_Common, que é sempre instalado. Tornando os recursos Feat_VS2002 e Feat_VS2003 visível, os usuários podem escolher no momento da instalação em quais versões do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que desejam integrar o VSPackage. Usuários também podem usar o modo de manutenção do Windows Installer para adicionar ou remover recursos, que nesse caso adiciona ou remove as informações de registro de VSPackage de diferentes versões do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
> [!NOTE]
>  A definição de coluna de exibição do recurso como 0 oculta. Um valor de coluna de nível baixo, como 1, garante que ele sempre será instalado. Para obter mais informações, consulte [installlevel SIGNIFICAM propriedade](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) e [recurso tabela](http://msdn.microsoft.com/library/aa368585.aspx).  
  
## <a name="scenario-2-shared-vspackage-update"></a>Cenário 2: Atualização de VSPackage compartilhado  
 Nesse cenário, uma versão atualizada do instalador do VSPackage no cenário 1 é enviada. Para nossa discussão, a atualização adiciona suporte para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], mas também pode ser um simples segurança patch ou correção de bug service pack. Regras do Windows Installer para instalar os componentes mais recentes exigem inalterados componentes já está no sistema não são copiados novamente. Nesse caso, um sistema com a versão 1.0 já está presente substituirá o componente de atualização Comp_MyVSPackage.dll e permitir que os usuários optar por adicionar o novo recurso Feat_VS2005 com seu componente Comp_VS2005_Reg.  
  
> [!CAUTION]
>  Sempre que um VSPackage é compartilhado entre várias versões do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], é essencial que as versões subsequentes do VSPackage mantenham compatibilidade com versões anteriores do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Onde não é possível manter compatibilidade com versões anteriores, você deve usar os VSPackages lado a lado, privados. Para obter mais informações, consulte [suporte a várias versões do Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
 ![Imagem de atualização de pacote VS compartilhado](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")  
Instalador de atualização de VSPackage de compartilhado  
  
 Este cenário apresenta um novo instalador de VSPackage, tirando proveito do suporte do Windows Installer para pequenas atualizações. Os usuários simplesmente instalar a versão 1.1 e ele atualiza a versão 1.0. No entanto, não é necessário ter a versão 1.0 do sistema. O mesmo instalador instalará a versão 1.1 em um sistema sem versão 1.0. A vantagem para fornecer atualizações secundárias dessa maneira é que não é necessário percorrer o trabalho de desenvolvimento de um instalador de upgrade e um instalador do produto completo. Um instalador faz ambos os trabalhos. Uma correção de segurança ou service pack pode em vez disso, tirar proveito de patches do Windows Installer. Para obter mais informações, consulte [atualizações e aplicação de patch](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).  
  
## <a name="scenario-3-side-by-side-vspackage"></a>Cenário 3: Lado a lado VSPackage  
 Este cenário apresenta dois instaladores VSPackage — uma para cada versão do Visual Studio .NET 2003 e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Cada instalador instala um lado a lado ou privado, VSPackage (que é especificamente criado e instalado para uma versão específica do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]). Cada VSPackage está em seu próprio componente. Consequentemente, cada um pode ser individualmente atendido com patches ou manutenção versões. Como a DLL VSPackage agora é específico da versão, é seguro incluir suas informações de registro no mesmo componente como DLL.  
  
 ![Gráfico de VSPackage lado a lado do VS](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")  
Instalador de VSPackage lado a lado  
  
 Cada instalador também inclui código que é compartilhado entre os dois instaladores. Se o código compartilhado é instalado em um local comum, instalar os dois arquivos. msi instalará o código compartilhado somente uma vez. O instalador do segundo apenas incrementa uma contagem de referência no componente. A contagem de referência garante que, se um dos VSPackages for desinstalado, o código compartilhado permanecerá por outro VSPackage. Se o segundo VSPackage for desinstalado, bem, o código compartilhado será removido.  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>Cenário 4: Atualização de VSPackage lado a lado  
 Nesse cenário, o VSPackage para [!INCLUDE[vsprvslong](../../code-quality/includes/vsprvslong_md.md)] sofreu de segurança vulnerabilidade e você precisa emitir uma atualização. Como no cenário 2, você pode criar um novo arquivo. msi que atualiza uma instalação existente para incluir a correção de segurança, bem como implantar novas instalações com a correção de segurança já no lugar.  
  
 Nesse caso, o VSPackage é um VSPackage gerenciado instalado no cache de assembly global (GAC). Quando você recompilá-lo para incluir a correção de segurança, você deve alterar a parte de número de revisão do número de versão do assembly. As informações de registro para o novo número de versão do assembly substitui a versão anterior, causando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para carregar o assembly fixo.  
  
 ![Gráfico de atualização de VSPackage lado a lado do VS](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")  
Instalador de atualização de VSPackage lado a lado  
  
 **Observação** para obter mais informações sobre a implantação dos assemblies lado a lado, consulte [simplificando a implantação e resolvendo inferno da DLL com o .NET Framework](http://msdn.microsoft.com/library/ms973843.aspx).  
  
## <a name="see-also"></a>Consulte também  
 [O Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Suporte a várias versões do Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
