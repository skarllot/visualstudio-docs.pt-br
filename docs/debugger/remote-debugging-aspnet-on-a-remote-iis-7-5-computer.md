---
title: "Depura&#231;&#227;o ASP.NET em um servidor remoto 7.5 remota do computador | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "hero-article"
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 8
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depura&#231;&#227;o ASP.NET em um servidor remoto 7.5 remota do computador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode implantar um aplicativo Web ASP.NET em um computador Windows Server 2008 R2 com o IIS 7.5 e configurá\-lo para depuração remota. As instruções a seguir explicam como configurar um aplicativo MVC de 2015 Visual Studio 4.5.2.  
  
## Criar o aplicativo no computador do Visual Studio  
  
1.  Crie um novo aplicativo ASP.NET MVC. \(**Arquivo \/ novo \/ projeto**, em seguida, selecione **Visual C\# \/ Web \/ aplicativo Web ASP.NET** . No **ASP.NET 4.5.2** seção de modelos, selecione **MVC**. Cancelar o **Configurar o Microsoft Azure Web App** página. \) e denomine\- **MyMVC**.  
  
2.  Abra o arquivo HomeController.cs e defina um ponto de interrupção `About()` método.  
  
3.  No **Solution Explorer**,  com o botão direito no nó do projeto e selecione **publicar**.  
  
4.  Para **Selecionar um destino de publicação**, selecione **personalizado** e nomeie o perfil **MyMVC**. Clique em **próximo**.  
  
5.  No **conexão** guia, defina o **método Publish** campo **sistema de arquivos** e **local de destino** campo em um diretório local. Clique em **próximo**.  
  
6.  Definir a configuração **Depurar**. Clique em **publicar**.  
  
     O aplicativo deve ser publicado para o diretório local.  
  
## Implantar o aplicativo no computador remoto do Windows Server  
 Esta seção pressupõe que o computador do Windows Server 2008 R2 já tiver habilitados para IIS.  
  
1.  Instale o ASP.NET:  
  
     **\\V4.0.30319\\aspnet\_regiis.exe \- ir C:\\Windows\\Microsoft.NET\\Framework \(64\)**  
  
2.  Copiar o diretório de projeto do ASP.NET do computador do Visual Studio em um diretório local \(que chamaremos **C:\\Publish**\) no computador Windows Server.  
  
3.  Certifique\-se de que o arquivo Web. config lista a versão correta do .NET Framework.  A versão do .NET Framework instalada por padrão no computador for 4.0.30319, mas criamos um ASP.NET 4.5.2 versão. Se essa versão não estiver instalada no computador do Windows Server, você precisa alterar a versão:  
  
    ```xml  
    <system.web> <authentication mode="None" /> <compilation debug="true" targetFramework="4.0.30319" /> <httpRuntime targetFramework="4.0.30319" /> </system.web>  
  
    ```  
  
4.  Abra o **Serviços de informações da Internet \(IIS\) Manager** e vá para **Sites**.  
  
5.  Com o botão direito do **Default Web Site** nó e selecione **Adicionar aplicativo**.  
  
6.  Definir o **Alias** campo **MyMVC** e o campo de pool de aplicativos para **ASP.NET v 4.0**. Definir o **caminho físico** para **C:\\Publish** \(onde você copiou o diretório de projeto do ASP.NET\).  
  
7.  Para testar a implantação, clique **Default Web Site** e selecione **Procurar**. Você verá a página da web.  
  
## Instalar o depurador remoto no computador do servidor do Windows  
 Para obter instruções sobre como baixar o depurador remoto, consulte [Depuração remota](../debugger/remote-debugging.md).  
  
 Para fazer a depuração remota de aplicativos ASP.NET, você pode iniciar o depurador remoto como um serviço ou executar o aplicativo do depurador remoto como um administrador. Obter detalhes sobre como executar o depurador remoto como um serviço pode ser encontrado em [Depuração remota](../debugger/remote-debugging.md).  
  
## Anexar ao aplicativo ASP.NET de computador do Visual Studio  
  
-   No computador do Visual Studio, abra o **MyMVC** solução.  
  
-   No Visual Studio, clique em **Depurar \/ anexar a processo**.  
  
-   Defina o campo qualificador para **\< nome do computador remoto \>: 4020**.  
  
-   Você deverá ver alguns processos no **processos disponíveis** janela.  
  
-   Verificar  **Mostrar processos de todos os usuários**.  
  
-   Procure **w3wp.exe** e clique em **Attach**.  
  
-   Abra o site do computador remoto. Em um navegador, vá para **http:\/\/\<remote o nome do computador \>**.  
  
-   Você verá a página da web ASP.NET. Clique em **sobre**.  
  
     O ponto de interrupção deve ser atingido no Visual Studio.