---
title: "Instru&#231;&#245;es passo a passo: criando um bootstrapper personalizado para mostrar um prompt de privacidade | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implantação ClickOnce, pré-requisitos"
  - "dependências [.NET Framework], pacote de inicializador personalizado"
  - "implantando aplicativos [Visual Studio], pré-requisitos personalizados"
  - "pré-requisitos [.NET Framework], pacote de inicializador personalizado"
  - "implantação do Windows Installer, pré-requisitos"
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: criando um bootstrapper personalizado para mostrar um prompt de privacidade
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode configurar aplicativos de ClickOnce para atualizar automaticamente quando os módulos \(assemblies\) com as versões mais recentes do arquivo e versões de montagem se tornam disponíveis.  Para certificar\-se de que seus clientes concorda com esse comportamento, você pode exibir um prompt de privacidade para eles.  Em seguida, eles poderão optar conceder permissão para o aplicativo para atualizar automaticamente.  Se o aplicativo não tiver permissão para atualizar automaticamente, ele não instala.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Pré-requisitos  
 Para completar este passo a passo, são necessários os seguintes componentes:  
  
-   2010, Visual Studio.  
  
## Criando uma caixa de diálogo de consentimento de atualização  
 Para exibir um aviso de privacidade, crie um aplicativo que solicita que o leitor para consentir as atualizações automáticas para o aplicativo.  
  
#### Para criar uma caixa de diálogo de consentimento  
  
1.  No menu **File**, aponte para **New**, e em seguida, clique em **Project**.  
  
2.  No  **Novo projeto** caixa de diálogo, clique em  **Windows**e, em seguida, clique em  **Windowsformuláriosaplicativo**.  
  
3.  Para o  **nome**, digite ConsentDialog e, em seguida, clique em  **OK**.  
  
4.  No designer, clique no formulário.  
  
5.  No  **Propriedades** janela, alterar o  **texto** propriedade à caixa de diálogo de consentimento do Update.  
  
6.  No  **caixa de ferramentas**, expanda  **All Windows Forms**e arraste uma  **rótulo** controle ao formulário.  
  
7.  No designer, clique no controle label.  
  
8.  No  **Propriedades** janela, alterar o  **texto** propriedade em  **aparência** à seguinte:  
  
     O aplicativo que você está prestes a instalar as atualizações mais recentes de procura na Web.  Clicando em "Eu concordo", você pode autorizar o aplicativo para verificar e instalar atualizações automaticamente da Internet.  
  
9. No  **caixa de ferramentas**, arraste um  **caixa de seleção** o controle para o meio do formulário.  
  
10. No  **Propriedades** janela, alterar o  **texto** propriedade em  **Layout** i Agree.  
  
11. No  **caixa de ferramentas**, arraste um  **botão** controle para o canto inferior esquerdo do formulário.  
  
12. No  **Propriedades** janela, alterar o  **texto** propriedade em  **Layout** para prosseguir.  
  
13. No  **Propriedades** janela, alterar o  **\(nome\)** propriedade em  **Design** para ProceedButton.  
  
14. No  **caixa de ferramentas**, arraste um  **botão** o controle para a parte inferior direita do formulário.  
  
15. No  **Propriedades** janela, alterar o  **texto** propriedade em  **Layout** para cancelar.  
  
16. No  **Propriedades** janela, alterar o  **\(nome\)** propriedade em  **Design** para CancelButton.  
  
17. No designer, clique duas vezes o  **I Agree** caixa de seleção para gerar o manipulador de evento CheckedChanged.  
  
18. No arquivo de código de Form1, adicione o seguinte código do manipulador de evento CheckedChanged.  
  
     [!code-cs[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]  
  
19. Atualizar o construtor da classe para desativar o  **prosseguir** o botão por padrão.  
  
     [!code-cs[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]  
  
20. No arquivo de código de Form1, adicione o seguinte código para uma variável booleana controlar se o usuário final aceitou atualizações on\-line.  
  
     [!code-cs[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]  
  
21. No designer, clique duas vezes o  **prosseguir** botão para gerar o manipulador de eventos Click.  
  
22. No arquivo de código de Form1, adicione o seguinte código ao manipulador de eventos Click para o  **prosseguir** botão.  
  
     [!code-cs[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]  
  
23. No designer, clique duas vezes o  **Cancelar** botão para gerar o manipulador de eventos Click.  
  
24. No arquivo de código de Form1, adicione o seguinte código para o manipulador de evento Click para o  **Cancelar** botão.  
  
     [!code-cs[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]  
  
25. Atualize o aplicativo para retornar um erro se o usuário final não consentir em atualizações on\-line.  
  
     Visual Basic somente para desenvolvedores:  
  
    1.  Em  **Solution Explorer**, clique em  **ConsentDialog**.  
  
    2.  Sobre o  **projeto** menu, clique em  **Adicionar módulo**e, em seguida, clique em  **Add**.  
  
    3.  No arquivo de código Module1. vb, adicione o código a seguir.  
  
         [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]  
  
    4.  Sobre o  **projeto** menu, clique em  **ConsentDialog propriedades**e, em seguida, clique no  **aplicativo** guia.  
  
    5.  Desmarque a opção  **Ativar estrutura de aplicativos**.  
  
    6.  No  **o objeto de inicialização** menu drop\-down, selecione  **Módulo1**.  
  
        > [!NOTE]
        >  Desativar o application framework desativa recursos, como estilos visuais do Windows XP, os eventos do aplicativo, tela de abertura, o aplicativo de instância única e muito mais.  Para obter mais informações, consulte [Página de Aplicativo, Designer de Projeto \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
     C\# Visual somente para desenvolvedores:  
  
     Abra o arquivo de código Program. cs e adicione o seguinte código.  
  
     [!code-cs[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]  
  
26. Sobre o  **Build** menu, clique em  **Construirsolução**.  
  
## Criação do pacote de Bootstrapper personalizado  
 Para mostrar o prompt de privacidade para os usuários finais, você pode criar um pacote de bootstrapper personalizado para o aplicativo de diálogo de consentimento de atualização e incluí\-lo como um pré\-requisito em todos os seus aplicativos de ClickOnce.  
  
 Esse procedimento demonstra como criar um pacote de bootstrapper personalizado, criando os seguintes documentos:  
  
-   Um Product. XML o arquivo para descrever o conteúdo de bootstrapper de manifesto.  
  
-   Um arquivo de manifesto de Package. XML para listar os aspectos específicos de localização do seu pacote, como, por exemplo, seqüências de caracteres e os termos de licença de software.  
  
-   Um documento para os termos de licença de software.  
  
#### Etapa 1: Criar o diretório de bootstrapper  
  
1.  Crie um diretório chamado UpdateConsentDialog no %PROGRAMFILES%\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages.  
  
    > [!NOTE]
    >  Talvez você precise de privilégios administrativos para criar essa pasta.  
  
2.  No diretório UpdateConsentDialog, crie um subdiretório chamado en.  
  
    > [!NOTE]
    >  Crie um novo diretório para cada localidade.  Por exemplo, você pode adicionar subpastas para as localidades fr e de.  Esses diretórios conteria as seqüências de caracteres de francês e alemão e os pacotes de idiomas, se necessário.  
  
#### Etapa 2: Criar o arquivo de manifesto de arquivo Product. XML  
  
1.  Crie um arquivo de texto chamado  `Product. XML`.  
  
2.  No arquivo Product. XML, adicione o seguinte código XML.  Certifique\-se de que você não substitua o código XML existente.  
  
    ```  
    <Product  
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      ProductCode="Microsoft.Sample.EULA">  
      <!-- Defines the list of files to be copied on build. -->  
      <PackageFiles CopyAllPackageFiles="false">  
        <PackageFile Name="ConsentDialog.exe"/>  
      </PackageFiles>  
  
      <!-- Defines how to run the Setup package.-->  
      <Commands >  
        <Command PackageFile = "ConsentDialog.exe" Arguments=''>  
          <ExitCodes>  
            <ExitCode Value="0" Result="Success" />  
            <ExitCode Value="-1" Result="Fail" String="AU_Unaccepted" />  
            <DefaultExitCode Result="Fail"   
              FormatMessageFromSystem="true" String="GeneralFailure" />  
          </ExitCodes>  
        </Command>  
      </Commands>  
  
    </Product>  
    ```  
  
3.  Salve o arquivo para o diretório de bootstrapper de UpdateConsentDialog.  
  
#### Etapa 3: Criar Package. XML o manifesto de arquivo e o software de termos de licença  
  
1.  Crie um arquivo de texto chamado  `Package. XML`.  
  
2.  No arquivo Package. XML, adicione o seguinte código XML para definir a localidade e incluir os termos de licença de software.  Certifique\-se de que você não substitua o código XML existente.  
  
    ```  
    <Package   
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      Name="DisplayName"  
      Culture="Culture"  
      LicenseAgreement="eula.rtf">  
      <PackageFiles>  
        <PackageFile Name="eula.rtf"/>  
      </PackageFiles>  
  
      <!-- Defines a localizable string table for error messages. -->  
      <Strings>  
        <String Name="DisplayName">Update Consent Dialog</String>  
        <String Name="Culture">en</String>  
        <String Name="AU_Unaccepted">The automatic update agreement is not accepted.</String>  
        <String Name="GeneralFailure">A failure occurred attempting to launch the setup.</String>  
      </Strings>  
    </Package>  
    ```  
  
3.  Salve o arquivo para o subdiretório en no diretório UpdateConsentDialog bootstrapper.  
  
4.  Crie um documento chamado EULA. rtf para os termos de licença de software.  
  
    > [!NOTE]
    >  Os termos de licença de software devem incluir informações sobre licenciamento, garantias, responsabilidades e as leis locais.  Esses arquivos devem ser específicos da localidade, portanto certifique\-se de que o arquivo é salvo em um formato que oferece suporte a caracteres MBCS ou UNICODE.  Consulte seu departamento jurídico sobre o conteúdo dos termos de licença de software.  
  
5.  Salve o documento para o subdiretório en no diretório UpdateConsentDialog bootstrapper.  
  
6.  Se necessário, crie um novo arquivo de manifesto de Package. XML e um novo documento do EULA. rtf para os termos de licença de software para cada localidade.  Por exemplo, se você tiver criado subdiretórios para as localidades de fr e de criar arquivos de manifesto de Package. XML separado e os termos de licença de software e salvá\-los em fr e de subdiretórios.  
  
## Configurando o aplicativo de consentimento de atualização como um pré\-requisito  
 No Visual Studio, você pode definir o aplicativo de atualização de consentimento como pré\-requisito.  
  
#### Para definir o aplicativo de consentimento de atualização como um pré\-requisito.  
  
1.  Em  **Solution Explorer**, clique no nome do seu aplicativo que você deseja implantar.  
  
2.  Sobre o  **projeto** menu, clique em  *ProjectName* **Propriedades**.  
  
3.  Clique no  **Publicar** da página e, em seguida, clique em  **pré\-requisitos**.  
  
4.  Selecione  **atualizar a caixa de diálogo de consentimento**.  
  
    > [!NOTE]
    >  Talvez você precise fechar e reabrir o Visual Studio para ver o diálogo de consentimento de atualização na caixa de diálogo pré\-requisitos.  
  
5.  Clique em **OK**.  
  
## Criar e testar o programa de instalação  
 Depois de definir o aplicativo de atualização de consentimento como pré\-requisito, você pode gerar o installer e o bootstrapper para seu aplicativo.  
  
#### Para criar e testar o programa de instalação clicando\-se não concordo  
  
1.  Em  **Solution Explorer**, clique no nome do seu aplicativo que você deseja implantar.  
  
2.  Sobre o  **projeto** menu, clique em  *ProjectName* **Propriedades**.  
  
3.  Clique no  **Publicar** da página e, em seguida, clique em  **Publicar agora**.  
  
4.  Se a saída de publicar não abrir automaticamente, navegue até a saída de publicar.  
  
5.  Execute o programa Setup. exe.  
  
     O programa de instalação mostra o contrato de licença de software do diálogo de consentimento de atualização.  
  
6.  Leia o contrato de licença de software e, em seguida, clique em  **Aceitar**.  
  
     O aplicativo de caixa de diálogo Atualizar consentimento aparece e mostra o seguinte texto: O aplicativo que você está prestes a instalar verifica as atualizações mais recentes na Web.  Ao clicar em concordo, você pode autorizar o aplicativo para verificar se há atualizações automaticamente na Internet.  
  
7.  Feche o aplicativo ou clique em Cancelar.  
  
     O aplicativo mostra um erro: Ocorreu um erro durante a instalação de componentes do sistema em  *ApplicationName*.  A instalação não pode continuar até que todos os componentes do sistema foi instalados com êxito.  
  
8.  Clique em detalhes para exibir a seguinte mensagem de erro: diálogo de consentimento atualizar componente foi instalado com a seguinte mensagem de erro: "O contrato de atualização automática não será aceito". Falha na instalação os seguintes componentes:\-caixa de diálogo Atualizar consentimento  
  
9. Clique em **Close**.  
  
#### Para criar e testar o programa de instalação clicando em concordo  
  
1.  Em  **Solution Explorer**, clique no nome do seu aplicativo que você deseja implantar.  
  
2.  Sobre o  **projeto** menu, clique em  *ProjectName* **Propriedades**.  
  
3.  Clique no  **Publicar** da página e, em seguida, clique em  **Publicar agora**.  
  
4.  Se a saída de publicar não abrir automaticamente, navegue até a saída de publicar.  
  
5.  Execute o programa Setup. exe.  
  
     O programa de instalação mostra o contrato de licença de software do diálogo de consentimento de atualização.  
  
6.  Leia o contrato de licença de software e, em seguida, clique em  **Aceitar**.  
  
     O aplicativo de caixa de diálogo Atualizar consentimento aparece e mostra o seguinte texto: O aplicativo que você está prestes a instalar verifica as atualizações mais recentes na Web.  Ao clicar em concordo, você pode autorizar o aplicativo para verificar se há atualizações automaticamente na Internet.  
  
7.  Clique em  **I Agree**e, em seguida, clique em  **prosseguir**.  
  
     O aplicativo começa a instalar.  
  
8.  Se for exibida a caixa de diálogo de instalação do aplicativo, clique em  **instalar**.  
  
## Consulte também  
 [Pré\-requisitos de implantação de aplicativos](../deployment/application-deployment-prerequisites.md)   
 [Criando pacotes de bootstrapper](../deployment/creating-bootstrapper-packages.md)   
 [Como criar um manifesto de produto](../deployment/how-to-create-a-product-manifest.md)   
 [Como criar um manifesto de pacote](../deployment/how-to-create-a-package-manifest.md)   
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)