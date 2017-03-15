---
title: "MSI e VSIX implantação de uma DSL | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 2
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: beb505dca6f5b52046ca87e854260f4b222079c8
ms.lasthandoff: 02/22/2017

---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Implantação de uma DSL por MSI e VSIX
Você pode instalar uma linguagem específica do domínio em seu próprio computador ou em outros computadores. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]já deve estar instalado no computador de destino.  
  
##  <a name="a-namewhicha-choosing-between-vsix-and-msi-deployment"></a><a name="which"></a>Escolhendo entre VSIX e implantação MSI  
 Há dois métodos de implantação de uma linguagem específica do domínio:  
  
|Método|Benefícios|  
|------------|--------------|  
|VSX ([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensão)|Muito fácil de implantar: copiar e executar o **. VSIX** arquivo do projeto DslPackage.<br /><br /> Para obter mais informações, consulte [instalação e desinstalação de uma DSL usando a VSX](#Installing).|  
|MSI (arquivo)|-Permite que o usuário abra [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] clicando duas vezes em um arquivo DSL.<br />-Associa um ícone com o tipo de arquivo DSL no computador de destino.<br />-Associa um XSD (esquema XML) com o tipo de arquivo DSL. Isso evita avisos quando o arquivo é carregado no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].<br /><br /> Você deve adicionar um projeto de instalação à sua solução para criar um MSI.<br /><br /> Para obter mais informações, consulte [Implantando uma DSL usando um arquivo MSI](#msi).|  
  
##  <a name="a-nameinstallinga-installing-and-uninstalling-a-dsl-by-using-the-vsx"></a><a name="Installing"></a>Instalando e desinstalando uma DSL usando a VSX  
 Quando sua DSL é instalada por esse método, o usuário pode abrir um arquivo DSL no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], mas não é possível abrir o arquivo do Windows Explorer.  
  
#### <a name="to-install-a-dsl-by-using-the-vsx"></a>Para instalar uma DSL usando a VSX  
  
1.  No seu computador, localize o **. VSIX** arquivo criado com o seu projeto de pacote DSL.  
  
    1.  Em **Solution Explorer**, com o botão direito do **DslPackage** de projeto e, em seguida, clique em **Abrir pasta no Windows Explorer**.  
  
    2.  Locate the file **bin\\\*\\***YourProject***. DslPackage.vsix**  
  
2.  Copie o **. VSIX** arquivo para o computador de destino no qual você deseja instalar a DSL. Isso pode ser seu próprio computador ou outro.  
  
    -   O computador de destino deve ter uma das edições do [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] que dá suporte a DSLs em tempo de execução. Para obter mais informações, consulte [suporte para edições do Visual Studio para o SDK de modelagem de visualização < /](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).  
  
    -   O computador de destino deve ter uma das edições do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] especificado em **DslPackage\source.extensions.manifest**.  
  
3.  No computador de destino, clique duas vezes o **. VSIX** arquivo.  
  
     **Instalador de extensão do Visual Studio** abre e instala a extensão.  
  
4.  Iniciar ou reiniciar [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
5.  Para testar o DSL, use [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para criar um novo arquivo que tenha a extensão que você definiu para sua DSL.  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Para desinstalar uma DSL que tenha sido instalada usando VSX  
  
1.  Sobre o **ferramentas** menu, clique em **Extension Manager**.  
  
2.  Expanda **extensões instaladas**.  
  
3.  Selecione a extensão na qual a DSL é definida e clique **desinstalar**.  
  
 Raramente, uma extensão com defeito não pode carregar e cria um relatório na janela de erros, mas não aparece no Gerenciador de extensões. Nesse caso, você pode remover a extensão, excluindo o arquivo:  
  
 *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**  
  
##  <a name="a-namemsia-deploying-a-dsl-in-an-msi"></a><a name="msi"></a>Implantando uma DSL em um MSI  
 Definindo um arquivo MSI (Windows Installer) para sua DSL, você pode permitir que os usuários abram arquivos DSL do Windows Explorer. Você também pode associar um ícone e uma descrição curta com sua extensão de nome de arquivo. Além disso, o MSI pode instalar um XSD que pode ser usado para validar os arquivos DSL. Se desejar, você pode adicionar outros componentes no MSI que será instalado ao mesmo tempo.  
  
 Para obter mais informações sobre arquivos MSI e outras opções de implantação, consulte [implantação de aplicativos, serviços e componentes](../deployment/deploying-applications-services-and-components.md).  
  
 Para criar um MSI, você adicionar um projeto de instalação para sua [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução. O método mais fácil de criar um projeto de instalação é usar o modelo CreateMsiSetupProject.tt, que pode ser baixado de [site VMSDK](http://go.microsoft.com/fwlink/?LinkID=186128).  
  
#### <a name="to-deploy-a-dsl-in-an-msi"></a>Para implantar uma DSL em um MSI  
  
1.  Defina `InstalledByMsi` no manifesto de extensão. Isso impede que o VSX seja instalado e desinstalado exceto pelo MSI. Isso é importante se você incluir outros componentes em MSI.  
  
    1.  Abra DslPackage\source.extension.tt  
  
    2.  Insira a seguinte linha antes de `<SupportedProducts>`:  
  
        ```  
        <InstalledByMsi>true</InstalledByMsi>  
        ```  
  
2.  Criar ou editar um ícone que representa sua DSL no Windows Explorer. Por exemplo, editar **DslPackage\Resources\File.ico**  
  
3.  Certifique-se de que os seguintes atributos de sua DSL estão corretos:  
  
    -   No Gerenciador de DSL, clique no nó raiz e na janela Propriedades, examine:  
  
        -   Descrição  
  
        -   Versão  
  
    -   Clique o **Editor** nó e na janela Propriedades, clique em **ícone**. Defina o valor para fazer referência a um arquivo de ícone em **DslPackage\Resources**, como **File.ico**  
  
    -   Sobre o **criar** menu, abrir **do Configuration Manager**e selecione a configuração que você deseja criar, como **versão** ou **depurar**.  
  
4.  Vá para [home page do SDK de visualização e modelagem](http://go.microsoft.com/fwlink/?LinkID=186128)e o **Downloads** guia, baixe **CreateMsiSetupProject.tt**.  
  
5.  Adicionar **CreateMsiSetupProject.tt** ao seu projeto de Dsl.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]criará um arquivo chamado **CreateMsiSetupProject.vdproj**.  
  
6.  No Windows Explorer, copie Dsl\\*.vdproj em uma nova pasta denominada programa de instalação.  
  
     (Se desejar, você pode excluir CreateMsiSetupProject.tt do seu projeto de Dsl.)  
  
7.  Em **Solution Explorer**, adicionar **instalação\\\*. vdproj** como um projeto existente.  
  
8.  Sobre o **projeto** menu, clique em **dependências do projeto**.  
  
     No **dependências do projeto** caixa de diálogo, selecione o projeto de instalação.  
  
     Marque a caixa ao lado **DslPackage**.  
  
9. Recompile a solução.  
  
10. No Windows Explorer, localize o arquivo MSI criado no seu projeto de instalação.  
  
     Copie o arquivo MSI em um computador no qual você deseja instalar a DSL. Clique duas vezes no arquivo MSI. O instalador for executado.  
  
11. No computador de destino, crie um novo arquivo que tenha a extensão de arquivo de sua DSL. Verifique se:  
  
    -   Na exibição de lista do Windows Explorer, o arquivo é exibido com o ícone e a descrição que você definiu.  
  
    -   Quando você clica duas vezes o arquivo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] inicia e abre o arquivo DSL em seu editor de DSL.  
  
 Se preferir, você pode criar o projeto de instalação manualmente, em vez de usar o modelo de texto. Para uma explicação passo a passo que inclui esse procedimento, consulte Capítulo 5 do [visualização e modelagem SDK laboratório](http://go.microsoft.com/fwlink/?LinkId=208878).  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Para desinstalar uma DSL que foi instalada de um MSI  
  
1.  No Windows, abra o **programas e recursos** painel de controle.  
  
2.  Desinstale a DSL.  
  
3.  Reinicie o Visual Studio.
