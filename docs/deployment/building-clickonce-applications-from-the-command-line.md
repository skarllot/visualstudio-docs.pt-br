---
title: "Compilando aplicativos ClickOnce a partir da linha de comando | Microsoft Docs"
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
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implantação ClickOnce, da linha de comando"
  - "publicando"
  - "publicando, ClickOnce"
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Compilando aplicativos ClickOnce a partir da linha de comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Na [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], você pode construir projetos a partir da linha de comando, mesmo se eles são criados no ambiente de desenvolvimento integrado \(IDE\).  Na verdade, você pode recriar um projeto criado com [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] em outro computador que tenha somente a [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] instalado.  Isso permite que você reproduzir uma compilação usando um processo automatizado, por exemplo, em uma compilação central laboratório ou usar avançada scripting técnicas além do escopo da construção do projeto em si.  
  
## Usando o MSBuild para reproduzir as implantações de aplicativos de ClickOnce  
 Quando você chama o msbuild \/target:publish na linha de comando, ele informa ao sistema MSBuild para construir o projeto e criar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo na pasta publicar.  Isso equivale a selecionar o  **Publicar** comando no IDE.  
  
 Este comando executa o MSBuild. exe, que está no caminho do ambiente de prompt de comando Visual Studio.  
  
 "Destino" é um indicador para MSBuild sobre como processar o comando.  Os principais alvos são o destino de "build" e o destino "Publicar".  O destino de compilação é o equivalente a selecionar a compilação comando \(ou pressionando F5\) no IDE.  Se você quiser apenas criar seu projeto, você pode obter que digitando  `msbuild`.  Esse comando funciona porque o destino de compilação é o destino padrão de todos os projetos gerados por [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Isso significa que você não precisa explicitamente especificar o destino de compilação.  Portanto, digitando  `msbuild` é a mesma operação que digitando  `msbuild /target:build`.  
  
 O  `/target:publish` comando instrui o MSBuild para invocar o destino de publicação.  O destino de publicação depende do destino de compilação.  Isso significa que a operação de publicação é um superconjunto da operação de compilação.  Por exemplo, se você fez uma alteração em um dos arquivos de origem do Visual Basic ou C\#, o assembly correspondente automaticamente ser reconstruído pela operação de publicação.  
  
 Para informações sobre como gerar um completo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação usando a ferramenta de linha de comando Mage para criar seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] de manifesto, consulte [Instruções passo a passo: implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Criando e construindo um aplicativo ClickOnce básico usando o MSBuild  
  
#### Para criar e publicar um projeto de ClickOnce  
  
1.  Clique em  **Novo projeto** partir do  **arquivo** menu.  A caixa de diálogo **New Project** será exibida.  
  
2.  Selecione  **Windows Application** e o nome de  `CmdLineDemo`.  
  
3.  Do  **Build** menu, clique no  **Publicar** comando.  
  
     Esta etapa garante que o projeto está configurado corretamente para produzir uma [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação de aplicativos.  
  
     O Assistente de Publicação aparece.  
  
4.  No Publish Wizard, clique em  **Concluir**.  
  
     Visual Studio gera e exibe a página da Web padrão, chamada Publish.  
  
5.  Salve seu projeto e anote o local da pasta na qual está armazenado.  
  
 As etapas acima criam uma [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o projeto que foi publicado pela primeira vez.  Agora você pode reproduzir a compilação fora do IDE.  
  
#### Para reproduzir a compilação da linha de comando  
  
1.  Exit [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
2.  Do Windows  **Iniciar** menu, clique em  **Todos os programas**, em seguida,  **Visual Studio do Microsoft**, em seguida,  **Visual Studio Tools**, em seguida,  **Visual Studio Prompt de comando**.  Isso deve abrir um prompt de comando na pasta raiz do usuário atual.  
  
3.  No  **Visual Studio Prompt de comando de**, altere o diretório atual para o local do projeto que você acabou de criar acima.  Por exemplo, digite  `chdir Meus Studio\Projects\CmdLineDemo de Documents\Visual`.  
  
4.  Para remover os arquivos existentes, produzidos em "criar e publicar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o projeto," tipo  `rmdir /s publicar`.  
  
     Esta etapa é opcional, mas garante que os novos arquivos todos produzidos pela compilação de linha de comando.  
  
5.  Tipo de  `msbuild /target: publicar`.  
  
 As etapas acima produzirá uma completa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação de aplicativos em uma subpasta do projeto chamada p**blicar**.  CmdLineDemo.application é o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto de implantação.  A pasta CmdLineDemo\_1.0.0.0 contém os arquivos CmdLineDemo.exe e CmdLineDemo.exe.manifest, o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto de aplicativo.  Setup. exe é o bootstrapper, que, por padrão, está configurado para instalar o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  A pasta DotNetFX contém redistribuíveis para o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Este é todo o conjunto de arquivos que você precisa para implantar seu aplicativo pela Web ou via CD\/DVD ou UNC.  
  
## Propriedades de publicação  
 Quando você publica o aplicativo nos procedimentos acima, as propriedades a seguir são inseridas em seu arquivo de projeto, o Assistente de publicação.  Essas propriedades influenciam diretamente como o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo é produzido.  
  
 Em CmdLineDemo.vbproj \/ CmdLineDemo.csproj:  
  
```  
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>  
<GenerateManifests>true</GenerateManifests>  
<TargetZone>LocalIntranet</TargetZone>  
<PublisherName>Microsoft</PublisherName>  
<ProductName>CmdLineDemo</ProductName>  
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>  
<Install>true</Install>  
<ApplicationVersion>1.0.0.*</ApplicationVersion>  
<ApplicationRevision>1</ApplicationRevision>  
<UpdateEnabled>true</UpdateEnabled>  
<UpdateRequired>false</UpdateRequired>  
<UpdateMode>Foreground</UpdateMode>  
<UpdateInterval>7</UpdateInterval>  
<UpdateIntervalUnits>Days</UpdateIntervalUnits>  
<UpdateUrlEnabled>false</UpdateUrlEnabled>  
<IsWebBootstrapper>true</IsWebBootstrapper>  
<BootstrapperEnabled>true</BootstrapperEnabled>  
```  
  
 Você pode substituir qualquer uma dessas propriedades na linha de comando sem alterar o próprio arquivo de projeto.  Por exemplo, a seguir criará o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação de aplicativos sem o bootstrapper:  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 Propriedades de publicação são controladas no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] da  **Publicar**,  **Security**, e  **Signing** páginas de propriedades da  **Project Designer**.  A seguir é uma descrição das propriedades de publicação, juntamente com uma indicação de como cada um é definida em várias páginas de propriedade do designer de aplicativo:  
  
-   `AssemblyOriginatorKeyFile`Determina o arquivo de chave usado para assinar seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestos de aplicativo.  Essa mesma chave também pode ser usado para atribuir um nome forte a seus conjuntos.  Esta propriedade é definida na  **Signing** página da  **Project Designer**.  
  
 As seguintes propriedades são definidas no  **Security** página:  
  
-   **Ativar configurações de segurança de ClickOnce** determina se [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestos são gerados.  Quando um projeto é criado inicialmente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] geração de manifesto está desativado por padrão.  O assistente automaticamente irá ativar esse sinalizador em quando você publica pela primeira vez.  
  
-   **TargetZone** determina o nível de confiança a ser emitido em seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto de aplicativo.  Valores possíveis são "Internet", "LocalIntranet" e "Custom".  Internet e LocalIntranet fará com que um conjunto de permissões padrão a ser emitido em seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto de aplicativo.  LocalIntranet é o padrão, e basicamente significa confiança total.  Custom Especifica que somente as permissões explicitamente especificadas no arquivo app. manifest base devem ser emitido para o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto de aplicativo.  O arquivo app. manifest é um arquivo de manifesto parcial que contém apenas as definições de informações de confiança.  É um arquivo oculto, adicionado automaticamente ao seu projeto, ao configurar permissões na  **Security** página.  
  
 As seguintes propriedades são definidas no  **Publicar** página:  
  
-   `PublishUrl`é o local onde o aplicativo será publicado no IDE.  Ele é inserido o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto de aplicativo, caso nem a `InstallUrl` ou `UpdateUrl` propriedade for especificada.  
  
-   `ApplicationVersion`Especifica a versão do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  Este é um número de versão de quatro dígitos.  Se o último dígito é um "\*", em seguida, a `ApplicationRevision` substituirá o valor inserido no manifesto em tempo de compilação.  
  
-   `ApplicationRevision`Especifica a revisão.  Este é um inteiro que é incrementado cada vez que você publicar no IDE.  Observe que ele não é automaticamente aumentado para compilações realizadas na linha de comando.  
  
-   `Install`Determina se o aplicativo é um aplicativo instalado ou um aplicativo de execução da Web.  
  
-   `InstallUrl`\(não mostrado\) é o local onde os usuários instalarão o aplicativo.  Se especificado, esse valor é gravado na bootstrapper setup. exe, se a `IsWebBootstrapper` propriedade estiver ativada.  Ele também é inserido na se manifesto de aplicativo do `UpdateUrl` não for especificado.  
  
-   `SupportUrl`\(não mostrado\) está no local vinculado no  **Adicionar ou remover programas** caixa de diálogo para um aplicativo instalado.  
  
 As seguintes propriedades são definidas na  **Atualizações de aplicativos** caixa de diálogo, acessada a partir do  **Publicar** página.  
  
-   `UpdateEnabled`Indica se o aplicativo deve verificar as atualizações.  
  
-   `UpdateMode`Especifica uma atualizações de primeiro plano ou atualizações em segundo plano.  
  
-   `UpdateInterval`Especifica a freqüência com que o aplicativo deve verificar atualizações.  
  
-   `UpdateIntervalUnits`Especifica se o `UpdateInterval` valor é em unidades de horas, dias ou semanas.  
  
-   `UpdateUrl`\(não mostrado\) é o local do qual o aplicativo receberá atualizações.  Se especificado, esse valor é inserido no manifesto do aplicativo.  
  
-   As seguintes propriedades são definidas na  **Opções de publicação do** caixa de diálogo, acessada a partir do  **Publicar** página.  
  
-   `PublisherName`Especifica o nome do Editor exibido no prompt mostrado ao instalar ou executar o aplicativo.  No caso de um aplicativo instalado, ele também é usado para especificar o nome da pasta do  **Iniciar** menu.  
  
-   `ProductName`Especifica o nome do produto exibido no prompt mostrado ao instalar ou executar o aplicativo.  No caso de um aplicativo instalado, ele também é usado para especificar o nome do atalho do  **Iniciar** menu.  
  
-   As seguintes propriedades são definidas na  **pré\-requisitos** caixa de diálogo, acessada a partir do  **Publicar** página.  
  
-   `BootstrapperEnabled`Determina se deve gerar o bootstrapper setup. exe.  
  
-   `IsWebBootstrapper`Determina se o bootstrapper setup. exe funciona pela Web ou no modo baseado em disco.  
  
## InstallURL, SupportUrl, PublishURL e UpdateURL  
 A tabela a seguir mostra as quatro opções de URL para a implantação de ClickOnce.  
  
|Opção de URL|Descrição|  
|------------------|---------------|  
|`PublishURL`|Necessário se você estiver publicando o seu aplicativo de ClickOnce para um site da Web.|  
|`InstallURL`|Opcional.  Definir esta opção de URL, se o site de instalação for diferente do `PublishURL`.  Por exemplo, você poderia definir o `PublishURL` um caminho FTP e o conjunto de `InstallURL` para uma URL da Web.|  
|`SupportURL`|Opcional.  Defina essa opção de URL se o site de suporte é diferente de `PublishURL`.  Por exemplo, você poderia definir a `SupportURL` para o site de suporte ao cliente da sua empresa.|  
|`UpdateURL`|Opcional.  Definir esta opção de URL, se o local de atualização for diferente do `InstallURL`.  Por exemplo, você poderia definir o `PublishURL` um caminho FTP e o conjunto de `UpdateURL` para uma URL da Web.|  
  
## Consulte também  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Instruções passo a passo: implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)