---
title: "Instru&#231;&#245;es passo a passo: baixando assemblies por demanda com a API de implanta&#231;&#227;o do ClickOnce | Microsoft Docs"
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
  - "assemblies, baixando [ClickOnce]"
  - "implantação ClickOnce, download sob demanda"
  - "assemblies sob demanda, ClickOnce"
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: baixando assemblies por demanda com a API de implanta&#231;&#227;o do ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Por padrão, todos os assemblies incluídos em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo são baixados quando o aplicativo é executado pela primeira vez.  No entanto, você pode ter partes da aplicação que são usados por um pequeno conjunto de seus usuários.  Nesse caso, você deseja fazer o download de um assembly somente quando você cria um de seus tipos.  A instrução a seguir demonstra como marcar determinados assemblies em seu aplicativo como "opcional", e como baixá\-los usando classes de <xref:System.Deployment.Application> namespace quando o common language runtime \(CLR\) os requer.  
  
> [!NOTE]
>  Seu aplicativo terá executado em confiança total para usar este procedimento.  
  
## Pré-requisitos  
 Você precisará de um dos seguintes componentes para concluir este passo a passo:  
  
-   O SDK do Windows.  O SDK do Windows pode ser baixado do Centro de Download da Microsoft.  
  
-   O Visual Studio.  
  
## Criação de projetos  
  
#### Para criar um projeto que usa um assembly sob demanda  
  
1.  Crie um diretório chamado ClickOnceOnDemand.  
  
2.  Abra o Prompt de comando do Windows SDK ou o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o Prompt de comando.  
  
3.  Mude para o diretório ClickOnceOnDemand.  
  
4.  Gere um par de chaves pública\/privada usando o seguinte comando:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  Usando o bloco de notas ou outro editor de texto, definir uma classe chamada `DynamicClass` com uma propriedade única chamada `Message`.  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-cs[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  Salvar o texto como um arquivo chamado  `ClickOnceLibrary.cs` ou  `ClickOnceLibrary.vb`, dependendo do idioma usado para o diretório ClickOnceOnDemand.  
  
7.  Compile o arquivo em um assembly.  
  
    ```c#  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb#  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  Para obter a chave pública token para o assembly, use o seguinte comando:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Crie um novo arquivo usando seu texto editor e digite o seguinte código.  Esse código cria um aplicativo Windows Forms que baixa o conjunto de ClickOnceLibrary, quando necessário.  
  
     [!code-cs[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. No código, localize a chamada para <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Definir `PublicKeyToken` o valor que você recuperou anteriormente.  
  
12. Salve o arquivo como um  `Form1. cs` ou  `Form1. vb`.  
  
13. Compilá\-lo em um executável usando o comando a seguir.  
  
    ```c#  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb#  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## Marcando os Assemblies como opcional  
  
#### Marcar assemblies como opcionais em seu aplicativo de ClickOnce usando MageUI.exe  
  
1.  Usando MageUI.exe, criar um manifesto de aplicativo, conforme descrito em [Instruções passo a passo: implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  Use as configurações a seguir para obter o manifesto de aplicativo:  
  
    -   Nomeie o manifesto do aplicativo  `ClickOnceOnDemand`.  
  
    -   Sobre o  **arquivos** página, na linha ClickOnceLibrary.dll, defina a  **Tipo de arquivo** coluna para  **Nenhum**.  
  
    -   Sobre o  **arquivos** página, na linha ClickOnceLibrary.dll, tipo  `ClickOnceLibrary.dll` na  **grupo** coluna.  
  
2.  Usando MageUI.exe, criar um manifesto de implantação, conforme descrito em [Instruções passo a passo: implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  Use as configurações a seguir para obter o manifesto de implantação:  
  
    -   Nomeie o manifesto de implantação  `ClickOnceOnDemand`.  
  
## Novo conjunto de teste.  
  
#### Para testar seu assembly sob demanda  
  
1.  Carregar seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] a implantação em um servidor Web.  
  
2.  Iniciar o aplicativo implantado com [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] em um navegador da Web digitando a URL para o manifesto de implantação.  Se você chamar o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo  `ClickOnceOnDemand`e carregá\-lo para o diretório raiz de adatum.com, seu URL ficaria assim:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  Quando o formulário principal for exibida, pressione a <xref:System.Windows.Forms.Button>.  Você deve ver uma seqüência de caracteres em uma janela de caixa de mensagem que diz "Hello, World\!".  
  
## Consulte também  
 <xref:System.Deployment.Application.ApplicationDeployment>