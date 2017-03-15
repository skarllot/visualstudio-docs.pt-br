---
title: "Como publicar um aplicativo WPF com estilos visuais habilitados | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
caps.latest.revision: 3
caps.handback.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
---
# Como publicar um aplicativo WPF com estilos visuais habilitados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os estilos visuais permitem a aparência dos controles comuns a alteração com base no tema escolhido pelo usuário.  Por padrão, os estilos visuais não estão habilitados para aplicativos Windows Presentation Foundation \(WPF\), o que habilita você deve manualmente.  No entanto, ativar estilos visuais para um aplicativo de WPF e depois publicar a solução causa um erro.  Este tópico descreve como resolver esse erro e o processo para publicar um aplicativo de WPF com estilos visuais ativados.  Para obter mais informações sobre estilos visuais, consulte [Visual Styles Overview](http://msdn.microsoft.com/pt-br/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e).  Para obter mais informações sobre a mensagem de erro, consulte [Solução de problemas com erros específicos nas implantações do ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).  
  
 Para resolver o erro e publicar a solução, você deve executar as seguintes tarefas:  
  
-   [Publicar a solução sem estilos visuais ativados](#BKMK_publishsolwovs).  
  
-   [Crie um arquivo de manifesto](#BKMK_CreateManifest).  
  
-   [Inserir o arquivo de manifesto no arquivo de solução publicado](#BKMK_embedmanifest).  
  
-   [Assinar os manifestos de aplicativo e implantação](#BKMK_signappdeplyman).  
  
 Em seguida, você pode mover os arquivos publicados ao local de onde você deseja que os usuários finais para instalar o aplicativo.  
  
##  <a name="BKMK_publishsolwovs"></a> Publicar a solução sem estilos visuais ativados  
  
1.  Certifique\-se que o projeto não tem os estilos visuais ativados.  Primeiro, verifique o arquivo de manifesto do projeto para o seguinte XML.  Então, se XML presente, incluindo XML com uma marca de comentário.  
  
     Por padrão, os estilos visuais não são ativados.  
  
    ```  
    <dependency>    <dependentAssembly>      <assemblyIdentity          type="win32"          name="Microsoft.Windows.Common-Controls"          version="6.0.0.0"          processorArchitecture="*"          publicKeyToken="6595b64144ccf1df"          language="*"        />    </dependentAssembly>  </dependency>  
    ```  
  
     Os procedimentos a seguir mostram como abrir o arquivo de manifesto associado com seu projeto.  
  
    ###### Para abrir o arquivo de manifesto em um projeto Visual Basic  
  
    1.  Na barra de menus, escolha **Projeto**, *ProjectName***Propriedades**, onde *ProjectName* é o nome do projeto de WPF.  
  
         As páginas de propriedades para seu projeto de publicam\-se WPF.  
  
    2.  Na guia de **Aplicativo** , escolha **Exibir Configurações do Windows**.  
  
         O arquivo de manifesto .app abre em **Editor de Códigos**.  
  
    ###### Para abrir o arquivo de manifesto em um projeto C\#  
  
    1.  Na barra de menus, escolha **Projeto**, *ProjectName***Propriedades**, onde *ProjectName* é o nome do projeto de WPF.  
  
         As páginas de propriedades para seu projeto de publicam\-se WPF.  
  
    2.  Na guia de **Aplicativo** , anote o nome que aparece no campo manifesto.  Este é o nome do manifesto que está associado com seu projeto.  
  
        > [!NOTE]
        >  Se **Inserir manifesto com configurações padrão** ou **Crie o aplicativo sem o manifesto** aparecem no campo manifesto, estilos visuais não estão ativados.  Se o nome de um arquivo de manifesto aparece no campo manifesto, vá para a próxima etapa deste procedimento.  
  
    3.  Em **Gerenciador de Soluções**, escolha **Mostrar todos os arquivos** \(\).  
  
         Este botão mostrar todos os itens de projeto, incluindo aqueles que foram excluídas e aqueles que são normalmente ocultos.  O arquivo de manifesto aparece como um item de projeto.  
  
2.  Criar e publicar sua solução.  Para obter mais informações sobre como publicar a solução, consulte [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md).  
  
##  <a name="BKMK_CreateManifest"></a> Crie um arquivo de manifesto  
  
1.  Cole o seguinte XML em um arquivo do Bloco De Notas.  
  
     Este XML descreve o assembly que contém controles que suportam estilos visuais.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?><asmv1:assembly manifestVersion="1.0"                xmlns="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  <dependency>    <dependentAssembly>      <assemblyIdentity        type="win32"        name="Microsoft.Windows.Common-Controls"        version="6.0.0.0"        processorArchitecture="*"        publicKeyToken="6595b64144ccf1df"        language="*"        />    </dependentAssembly>  </dependency></asmv1:assembly>  
    ```  
  
2.  No Bloco De Notas, clique **Arquivo**, clique em **Salvar como**.  
  
3.  Na caixa de diálogo **Salvar como** , na lista suspensa de **Salvar como tipo** , **Todos os Arquivos**.  
  
4.  Na caixa de **Nome do arquivo** , nomeie o arquivo e acrescentar .manifest ao final do nome de arquivo.  Por exemplo: themes.manifest.  
  
5.  Escolha o botão de **Procurar nas pastas** , selecione qualquer pasta, e clique em **Salvar**.  
  
    > [!NOTE]
    >  Os procedimentos seguintes assumem que o nome do arquivo é themes.manifest e que o arquivo é salvo no diretório C:\\temp no seu computador.  
  
##  <a name="BKMK_embedmanifest"></a> Inserir o arquivo de manifesto no arquivo de solução publicado  
  
1.  Abra **Prompt de Comando Visual Studio**.  
  
     Para obter mais informações sobre como abrir **Prompt de Comando Visual Studio**, consulte [Prompts de Comando](../Topic/Developer%20Command%20Prompt%20for%20Visual%20Studio.md).  
  
    > [!NOTE]
    >  As etapas restantes tornam as seguintes suposições sobre sua solução:  
    >   
    >  -   O nome da solução é MyWPFProject.  
    > -   A solução é localizada no seguinte diretório: `%UserProfile%\Documents\Visual Studio 2010\Projects\`.  
    >   
    >      A solução é publicado o seguinte diretório: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish`.  
    > -   A versão mais recente dos arquivos de aplicativos publicados está localizada no seguinte diretório: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`  
    >   
    >  Você não precisa usar o nome ou os locais de diretório descrito acima.  O nome e locais descritos acima são usados para ilustrar somente as etapas necessárias para publicar sua solução.  
  
2.  No prompt de comando, altere o caminho para o diretório que contém a versão mais recente dos arquivos de aplicativo publicado.  O exemplo a seguir demonstra essa etapa.  
  
    ```  
    cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"  
    ```  
  
3.  No prompt de comando, execute o seguinte comando inserir o arquivo de manifesto no arquivo executável do aplicativo.  
  
    ```  
    mt –manifest c:\temp\themes.manifest –outputresource:MyWPFApp.exe.deploy  
    ```  
  
##  <a name="BKMK_signappdeplyman"></a> Assinar os manifestos de aplicativo e implantação  
  
1.  No prompt de comando, execute o seguinte comando remova a extensão de `.deploy` do arquivo executável no diretório atual.  
  
    ```  
    ren MyWPFApp.exe.deploy MyWPFApp.exe  
    ```  
  
    > [!NOTE]
    >  Este exemplo assume que apenas um arquivo possui a extensão de arquivo `.deploy` .  Certifique\-se de que você renomear todos os arquivos no diretório que têm a extensão de arquivo `.deploy` .  
  
2.  No prompt de comando, execute o seguinte comando assinar o manifesto do aplicativo.  
  
    ```  
    mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  Este exemplo assume que você assina o manifesto usando o arquivo de `.pfx` do projeto.  Se você não estiver assinando o manifesto, você pode omitir o parâmetro de `–cf` que é usado neste exemplo.  Se você estiver assinando o manifesto com um certificado que requer uma senha, especifique a opção de `–password` \(`For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – passwordPassword`\).  
  
3.  No prompt de comando, execute o seguinte comando adicionar a extensão de `.deploy` para o nome do arquivo que você renomeou em uma etapa anterior deste procedimento.  
  
    ```  
    ren MyWPFApp.exe MyWPFApp.exe.deploy  
    ```  
  
    > [!NOTE]
    >  Este exemplo assume que apenas um arquivo tivesse uma extensão de arquivo `.deploy` .  Certifique\-se de que você renomear todos os arquivos no diretório que anteriormente tinha a extensão de nome de arquivo `.deploy` .  
  
4.  No prompt de comando, execute o seguinte comando assinar o manifesto de implantação.  
  
    ```  
    mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  Este exemplo assume que você assina o manifesto usando o arquivo de `.pfx` do projeto.  Se você não estiver assinando o manifesto, você pode omitir o parâmetro de `–cf` que é usado neste exemplo.  Se você estiver assinando o manifesto com um certificado que requer uma senha, especifique a opção de `–password` , como neste exemplo:`For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – passwordPassword`.  
  
 Depois de executar essas etapas, você pode mover os arquivos publicados ao local de onde você deseja que os usuários finais para instalar o aplicativo.  Se você pretende atualizar geralmente a solução, você pode mover esses comandos em um script e executar script cada vez que você publicar uma nova versão.  
  
## Consulte também  
 [Solução de problemas com erros específicos nas implantações do ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)   
 [Visual Styles Overview](http://msdn.microsoft.com/pt-br/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e)   
 [Enabling Visual Styles](VS|Controls|~\controls\userex\cookbook.htm)   
 [Prompts de Comando](../Topic/Developer%20Command%20Prompt%20for%20Visual%20Studio.md)