---
title: "Como criar e executar uma instala&#231;&#227;o aut&#244;noma do Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Instalando o Visual Studio, autônoma"
  - "instalação autônoma, o Visual Studio"
ms.assetid: 3867b5dc-ed34-4ee2-be32-a42e7e320517
caps.latest.revision: 44
caps.handback.revision: 40
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Como criar e executar uma instala&#231;&#227;o aut&#244;noma do Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode executar o aplicativo de instalação para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] como autônomo \(ou seja, silencioso personalizado\) em uma intranet em vez da partir de mídia como DVDs. Este tópico descreve como preparar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para esse tipo de instalação a partir de um compartilhamento de rede.  
  
## Criando uma imagem de rede  
 Primeiro, crie uma imagem de rede do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mídia.  
  
#### Para criar uma imagem de rede  
  
1.  Crie uma pasta no servidor \(por exemplo, *unidade*: \\IDEinstall\\\).  
  
2.  Execute uma das seguintes etapas:  
  
    -   Baixe o bootstrapper da web e, em seguida, execute *produto*.exe \/Layout *unidade*: \\IDEinstall\\.  
  
         OR  
  
    -   Copie o conteúdo da mídia para o Visual Studio para a pasta IDEinstall. Em seguida, baixe qualquer software de terceiros que você deseja instalar.  
  
3.  Compartilhe a pasta IDEinstall na rede e, em seguida, defina as configurações de segurança apropriadas.  
  
     O caminho de rede do aplicativo de instalação para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é semelhante a \\ \\*ServerName*\\IDEinstall\\*produto*.exe.  
  
    > [!NOTE]
    >  A instalação pode falhar se qualquer combinação de nome de arquivo e caminho exceder 260 caracteres. O comprimento máximo de um caminho no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é de 221 caracteres.  O nome do caminho local não deve exceder 70 caracteres e o nome do caminho de rede não deve exceder 39 caracteres.  
  
     A instalação também pode falhar se os nomes de pasta no caminho incluam espaços \(por exemplo, "\\ \\*ServerName*\\IDE install" ou \\ \\*ServerName*\\Visual Studio\\\).  
  
## Implantando o Visual Studio no modo autônomo  
 Para implantar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no modo autônomo, você deve modificar o arquivo Admindeployment XML. Para fazer isso, primeiro você deve criar o arquivo Admindeployment XML usando o `/CreateAdminFile` *\< local do arquivo \>* parâmetro de linha de comando. Em seguida, você pode usar esse arquivo para enviar por push uma implantação do Visual Studio à sua rede ou inseri\-lo em uma instalação, se você colocar esse arquivo de *unidade*: \\ideinstall\\packages. directory. O arquivo Admindeployment XML não é exclusivo para um sistema operacional, a arquitetura, a edição do Visual Studio ou o idioma do sistema operacional.  
  
> [!CAUTION]
>  Às vezes, os itens listados como selecionado no arquivo Admindeployment não instalados. Para resolver esse problema, coloque os itens marcados como "selecionados \="yes"" no **final** do arquivo Admindeployment.  
>   
>  Se você não quiser instalar as dependências opcionais de um item, você deve primeiro selecionar o pai e cancele as dependências opcionais após o pai, conforme mostrado na seguinte captura de tela:  
>   
>  ![Installation items at the end of the AdminDeployment.xml file](../install/media/vs2015_install_endoffileadmindeploy.PNG "vs2015\_Install\_EndOfFileAdminDeploy")  
>   
>  Outra maneira de fazer isso é simplesmente omitir opcionais filhos de um pai — em outras palavras, não incluem nenhum "selecionados \="no"" itens — mas você ainda precisa colocar todos o "selecionados \="yes"" itens no final do arquivo Admindeployment.  
  
> [!IMPORTANT]
>  Durante a instalação, o computador pode reiniciar automaticamente uma ou mais vezes. Depois que ele for reiniciado, faça logon novamente com a mesma conta de usuário com a qual logon para executar a instalação antes do computador é reiniciado. Você pode evitar reinícios automáticos instalando os componentes de pré\-requisito antes de executar uma instalação autônoma. Para obter mais informações, consulte a seção intitulada "Evite reiniciar durante a instalação" no [Guia do Administrador do Visual Studio](../install/visual-studio-administrator-guide.md).  
  
 O esquema de arquivo AdminDeployment contém os seguintes elementos:  
  
|Elemento|Atributo|Valores|Descrição|  
|--------------|--------------|-------------|---------------|  
|BundleCustomizations|TargetDir|*Caminho*|Se comporta como substituir o caminho na interface do usuário do aplicativo de instalação. Esse elemento será ignorado se o Visual Studio já está instalado.|  
|BundleCustomizations|NoWeb|Sim &#124; padrão|Se o valor desse elemento for Sim, o aplicativo de instalação nunca tentará ir para a web durante a ação de instalação.|  
|SelectableItemCustomization|Oculto|Sim &#124; Não|Se o valor desse elemento for Sim, oculta um item selecionável na árvore de personalização.|  
|SelectableItemCustomization|Selecionado|Sim &#124; Não|Marca ou desmarca um item selecionável na árvore de personalização.|  
|BundleCustomizations|Feed|Caminho|Local do feed que o usuário deseja usar.  Esse feed é usado para subsequentes modificar operações no computador \("padrão" por padrão\).|  
|BundleCustomizations|SuppressRefreshPrompt|Sim &#124; padrão|Impedirá que o usuário seja solicitado a atualizar a instalação se houver mais recente disponível.|  
|BundleCustomizations|NoRefresh|Sim &#124; padrão|Não atualizar a instalação se houver mais recente disponível.|  
|BundleCustomizations|NoCacheOnlyMode|Sim &#124; padrão|Impede pré\-população do cache do pacote.|  
  
> [!WARNING]
>  O aplicativo de instalação respeitará o estado selecionado de um selectableitem, mesmo se ele estiver oculto. Por exemplo, se você quiser instalar sempre um item selecionável, marcá\-lo como oculto e selecionado.  
  
#### Para criar uma instalação autônoma do Visual Studio  
  
1.  Em *unidade*: \\IDEinstall\\AdminDeployment.xml file, altere o valor do atributo NoWeb do elemento de BundleCustomizations de "padrão" para "yes" como mostra o exemplo a seguir:  
  
     Alterar `<BundleCustomizations TargetDir="default" NoWeb="default"/>` para `<BundleCustomizations TargetDir="default" NoWeb="yes"/>`  
  
2.  Altere o atributo SelectableItemCustomization conforme necessário para componentes opcionais e, em seguida, salve o arquivo.  
  
## Executar uma instalação autônoma  
 Você pode executar uma instalação autônoma ou executando o aplicativo de instalação do Visual Studio em computadores cliente automaticamente, permitindo que os usuários executem o aplicativo por conta própria usando as configurações que você define.  
  
#### Para executar uma instalação autônoma em um computador cliente  
  
-   Abra o **Iniciar** menu, escolha **executar**, e, em seguida, digite \\ \\*ServerName*\\IDEinstall\\vs\_*produto*\/adminfile .exe *PathOfTheAdmindeployment.xmlFile**AdditionalParametersAsNeeded*  
  
     Por exemplo, você pode especificar a seguinte linha de comando: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\ IDEinstall\AdminDeployment.xml /quiet /norestart`  
  
#### Para habilitar os clientes instalem manualmente o Visual Studio com configurações predefinidas  
  
1.  Copie o arquivo Admindeployment XML personalizado para um compartilhamento de rede que é somente leitura \(por exemplo, \\ \\*ServerName*\\IDEinstall\\packages\\AdminDeployment.xml\).  
  
2.  Permitir que os usuários instalem deste compartilhamento.  
  
## Mantendo uma instalação  
 Se você abrir **Painel de controle** e execute novamente o aplicativo de instalação, você pode modificar os recursos do Visual Studio, desinstalar linguagens de programação e reparar ou desinstalar o Visual Studio.  
  
> [!NOTE]
>  Você deve ter credenciais administrativas no computador local para usar o modo de manutenção.  
  
#### Para manter uma instalação em um computador cliente  
  
-   Abra **Painel de controle**, e, em seguida, escolha **programas e recursos**.  
  
-   Escolha [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], e, em seguida, escolha **alteração**.  
  
#### Para alterar as configurações de AdminDeployment em um computador cliente após a instalação do Visual Studio  
  
1.  Atualize Admindeployment conforme necessário.  
  
2.  Abra o **Iniciar** menu e, em seguida, escolha **executar**.  
  
3.  Digite o seguinte texto: \\ \\*ServerName*\\IDEinstall\\vs\_*produto*.exe \/AdminFile PathToAdmindeployment.xml arquivo  
  
     AdditionalParametersAsNeeded  
  
     Por exemplo, você pode especificar a seguinte linha de comando: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\IDEinstall\AdminDeployment.xml /quiet /norestart`  
  
 O reparo é o parâmetro padrão após a instalação do Visual Studio. Se você reparar o Visual Studio com um \/AdminFile atualizado, você substituirá as configurações de implantação Admin atuais com aqueles que invoca o arquivo Admindeployment XML atualizado.  
  
## Atualizando uma instalação  
 A Microsoft lançou várias atualizações para o Visual Studio 2015. Esta seção explica como atualizar sua imagem de instalação autônoma do Visual Studio 2015, incluindo as atualizações.  
  
#### Para atualizar uma instalação autônoma do Visual Studio  
  
1.  Localize o arquivo Product.exe na imagem de rede existente, clique duas vezes e, em seguida, clique em **propriedades**.  
  
2.  Clique o **detalhes** guia e anote o **versão do produto** propriedade.  
  
     ![Example of the Properties dialog box in an unattended installation of Visual Studio](../install/media/unattended-install---properties-dialog-box.PNG "Unattended Install \- Properties Dialog Box")  
  
3.  ###### Se a versão do produto for 14.0.24720.0 ou 14.0.24720.1, siga estas etapas:  
4.  1.  Executar *Product.exe* \/Layout *unidade:*\\IDEinstall em um computador que tenha acesso à Internet. \(Por exemplo, execute: `vs_enterprise.exe /Layout d:\IDEinstall`.\)  
  
    2.  Depois que o \/Layout estiver concluído, copie a nova imagem para um novo local.  
  
    3.  Criar e modificar o arquivo Admindeployment XML. Para fazer isso, use o `/CreateAdminFile`*\< local do arquivo \>* parâmetro de linha de comando. \(Para obter mais informações, consulte a seção "Implantando Visual Studio no modo autônomo" deste artigo.\)  
  
    4.  No computador cliente, execute o seguinte comando para atualizar a cópia do Visual Studio que você instalou anteriormente: "\\ \\*servidor1*\\IDEinstall\_Updated\_1\\*Product.exe* \\\\server1\\ IDEinstall\_Updated\_1\\AdminDeployment.xml \/adminfile \/quiet \/norestart".  
  
         Por exemplo, execute: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`  
5.  ###### Para outros valores de versão do produto, siga estas etapas:  
6.  1.  Executar *Product.exe* \/Layout *unidade:*\\IDEinstall em um computador que tenha acesso à Internet. \(Por exemplo, execute `vs-enterprise.exe /Layout d:\IDEinstall`.\)  
  
    2.  Depois que o \/Layout estiver concluído, copie a nova imagem para um novo local. \(Ou você pode substituir a imagem de rede existente em vez disso.\)  
  
    3.  Crie e modifique o arquivo Admindeployment XML. Para fazer isso, use o `/CreateAdminFile`*\< local do arquivo \>* parâmetro de linha de comando. \(Para obter mais informações, consulte a seção "Implantando Visual Studio no modo autônomo" deste artigo.\)  
  
    4.  Se você copiar a imagem para um novo local, você deve executar o comando a seguir no computador cliente para atualizar a cópia do Visual Studio que você instalou anteriormente: "\\ \\*servidor1*\\IDEinstall\_Updated\_1\\*Product.exe* \\\\server1\\ IDEinstall\_Updated\_1\\AdminDeployment.xml \/adminfile \/quiet \/norestart".  
  
         Por exemplo, execute: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`  
  
    5.  Se você substituir a imagem de rede existente, você pode executar o comando, conforme listado na etapa anterior, ou você pode fazer o seguinte:  
  
    6.  1.  Abra **Painel de controle**, e, em seguida, escolha **programas e recursos**.  
  
        2.  Escolha **Visual Studio**, e, em seguida, escolha **alteração**.  
  
        3.  Depois que o Visual Studio é iniciado no modo de manutenção, clique em **modificar**.  
  
        4.  A atualização mais recente deve aparecer na página de recursos. Selecione os outros recursos que você deseja instalar, clique em **próximo**, e, em seguida, clique em **atualizar** para instalar a atualização e os novos recursos.  
  
## Registrando o produto  
 Após a conclusão da instalação, você pode registrar sua cópia do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
#### Para registrar  
  
1.  Abra o **Ajuda** menu e, em seguida, escolha **Registrar produto**.  
  
2.  Insira a chave do produto.  
  
     \(Para obter mais informações, consulte o [Como localizar a chave do produto do Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) e o [Como aplicar as chaves de produto automaticamente durante a implantação do Visual Studio](../Topic/How%20to:%20Automatically%20apply%20product%20keys%20when%20deploying%20Visual%20Studio.md) tópicos.\)  
  
## Consulte também  
 [Instalando o Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)