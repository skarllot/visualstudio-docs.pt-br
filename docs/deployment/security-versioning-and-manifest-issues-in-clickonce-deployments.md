---
title: "Problemas de seguran&#231;a, controle de vers&#227;o e manifesto em implanta&#231;&#245;es do ClickOnce | Microsoft Docs"
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
  - "Aplicativos ClickOnce, problemas de manifesto"
  - "Aplicativos ClickOnce, problemas de segurança"
  - "Aplicativos ClickOnce, problemas de controle de versão"
  - "Aplicativos ClickOnce, Controle de Conta de Usuário do Windows Vista"
  - "manifestos [ClickOnce]"
  - "segurança, Aplicativos ClickOnce"
  - "Controle de Conta de Usuário, Aplicativos ClickOnce"
  - "controle de versão, Aplicativos ClickOnce"
  - "Windows 7, implantações ClickOnce"
  - "Windows Vista, implantações ClickOnce"
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Problemas de seguran&#231;a, controle de vers&#227;o e manifesto em implanta&#231;&#245;es do ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Há uma variedade de problemas com [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] segurança, controle de versão do aplicativo e manifesto de sintaxe e semântica que pode causar uma [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação não seja bem\-sucedida.  
  
## ClickOnce e o controle de conta de usuário do Windows Vista  
 Na [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)], aplicativos, por padrão são executados como usuário padrão, mesmo se o usuário atual está conectado com uma conta que tenha permissões de administrador.  Se um aplicativo deve executar uma ação que requer permissões de administrador, ele informa o sistema operacional, que, em seguida, solicita que o usuário insira suas credenciais de administrador.  Esse recurso, o que é chamado de controle de conta de usuário \(UAC\), impede que aplicativos façam alterações que podem afetar todo o sistema operacional sem a aprovação explícita do usuário.  Aplicativos Windows declarar que exigem a elevação de permissões, especificando a `requestedExecutionLevel` o atributo na `trustInfo` seção de manifesto do aplicativo.  
  
 Devido ao risco de expor os aplicativos a ataques de elevação de segurança, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos não é possível solicitar a elevação de permissões se o UAC estiver habilitado para o cliente.  Qualquer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo que tenta definir suas `requestedExecutionLevel` para o atributo `requireAdministrator` ou `highestAvailable` não será instalado em [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].  
  
 Em alguns casos, o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo pode tentar executar com permissões de administrador por causa da lógica de detecção de instalador em [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].  Nesse caso, você pode definir a `requestedExecutionLevel` atributo no manifesto do aplicativo para `asInvoker`.  Isso fará com que o aplicativo seja executado sem elevação. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] adiciona automaticamente esse atributo para todos os manifestos de aplicativo.  
  
 Se você estiver desenvolvendo um aplicativo que requer permissões de administrador para o tempo de vida inteiro do aplicativo, você deve considerar a implantar o aplicativo usando a tecnologia do Windows Installer \(MSI\) em vez disso.  Para obter mais informações, consulte [Noções básicas do Windows Installer](../extensibility/internals/windows-installer-basics.md).  
  
## Aplicativos de confiança on\-line de cotas do aplicativo e parcial  
 Se sua [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo é executado on\-line em vez de através de uma instalação, ele deve caber dentro da cota reservada para os aplicativos on\-line.  Além disso, um aplicativo de rede que é executado em confiança parcial, como com um conjunto restrito de permissões de segurança, não pode ser maior do que metade do tamanho da cota.  
  
 Para obter mais informações e instruções sobre como alterar a cota de inscrição online, consulte [Visão geral do cache do ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## Problemas de versionamento  
 Você pode ter problemas se você atribuir nomes fortes ao seu assembly e incrementa o número de versão do assembly para refletir uma atualização do aplicativo.  Qualquer assembly compilado com uma referência a um assembly de nome forte deve propriamente dito ser recompilado ou assembly irá tentar fazer referência a versão mais antiga.  O assembly fará isso porque o assembly está usando o valor da versão antiga em sua solicitação de ligação.  
  
 Por exemplo, digamos que você tenha um assembly de nome forte em seu próprio projeto com a versão 1.0.0.0.  Após compilar o assembly, adicioná\-lo como uma referência para o projeto que contém o seu aplicativo principal.  Se você atualizar o assembly, incrementa a versão 1.0.0.1 e tenta implantá\-lo sem também recompilar o aplicativo, o aplicativo não poderá carregar o assembly em tempo de execução.  
  
 Este erro pode ocorrer somente se você estiver editando seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestos manualmente; Esse erro não deve ocorrer se você gerar sua implantação usando [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)].  
  
## A especificação do indivíduo.NET Framework Assemblies no manifesto  
 Seu aplicativo falhará carregar se você tiver editado manualmente um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação para fazer referência a uma versão mais antiga de um [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] assembly.  Por exemplo, se você adicionou uma referência ao assembly System.Net para obter uma versão do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] anteriores à versão especificada no manifesto, um erro poderia ocorrer.  Em geral, você não deve tentar especificar referências ao indivíduo [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] assemblies, como a versão do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] contra o qual seu aplicativo é executado é especificada como uma dependência no manifesto do aplicativo.  
  
## Problemas de análise do manifesto  
 Os arquivos de manifesto que são usados por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] são arquivos XML, e devem ser bem formado e válido: precisam obedecer as regras de sintaxe XML e usar apenas os elementos e atributos definidos no esquema XML relevante.  
  
 Algo que pode causar problemas em um arquivo de manifesto é selecionando um nome para seu aplicativo que contém um caractere especial, como, por exemplo, uma aspa simples ou dupla.  O nome do aplicativo faz parte de sua [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] identidade.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]no momento não analisa as identidades que contêm caracteres especiais.  Se não conseguir ativar seu aplicativo, certifique\-se de que você está usando somente alfabéticos e numéricos para o nome e tenta implantá\-lo novamente.  
  
 Se você tiver editado manualmente seus manifestos de implantação ou aplicativo, você pode ter acidentalmente corrompido\-los.  Manifesto corrompido impedirá um correto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalação.  Você pode depurar tais erros em tempo de execução, clicando em  **detalhes** no  **Erro de ClickOnce** caixa de diálogo e ler a mensagem de erro no log.  O log irá listar uma das seguintes mensagens:  
  
-   Uma descrição do erro de sintaxe e o número da linha e caractere posição onde ocorreu o erro.  
  
-   O nome de um elemento ou atributo usado em violação do esquema do manifesto.  Se você tiver adicionado o XML manualmente para seus manifestos, você terá que comparar as adições os esquemas de manifesto.  Para obter mais informações, consulte [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md) e [Manifesto de aplicativo ClickOnce](../deployment/clickonce-application-manifest.md).  
  
-   Um conflito de ID.  Referências de dependência nos manifestos de implantação e o aplicativo devem ser exclusivas em ambas as suas `name` e `publicKeyToken` atributos.  Se ambos os atributos correspondem entre quaisquer dois elementos dentro de um manifesto, análise de manifesto não terá êxito.  
  
## Precauções ao alterar manualmente os manifestos ou aplicativos  
 Quando você atualiza um manifesto de aplicativo, você deve assinar novamente o manifesto do aplicativo e o manifesto de implantação.  O manifesto de implantação contém uma referência ao manifesto do aplicativo que inclui o hash do arquivo e sua assinatura digital.  
  
### Precauções com o uso do provedor de implantação  
 O [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto de implantação tem um `deploymentProvider` propriedade que aponta para o caminho completo do local de onde o aplicativo deve ser instalado e atendido:  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 Esse caminho é definido quando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cria o aplicativo e é obrigatório para aplicativos instalados.  O caminho aponta para o local padrão onde o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installer instalará o aplicativo e procure atualizações.  Se você usar o **xcopy** comando para copiar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo para um local diferente, mas não alterar o `deploymentProvider` propriedade, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ainda farão referência volta ao local original quando ele tenta baixar o aplicativo.  
  
 Se você deseja mover ou copiar um aplicativo, você deve também atualizar o `deploymentProvider` caminho, para que o cliente realmente instala da nova localização.  Atualizando este caminho é principalmente uma preocupação, se você tiver instalado os aplicativos.  Para aplicativos on\-line que sempre serão inicializados através da URL original, definindo a `deploymentProvider` é opcional.  Se `deploymentProvider` estiver definida, ela será respeitada; Caso contrário, a URL usada para iniciar o aplicativo será usada como a URL base para fazer o download de arquivos do aplicativo.  
  
> [!NOTE]
>  Toda vez que você atualize o manifesto deve também assiná\-lo novamente.  
  
## Consulte também  
 [Solução de problemas de implantações do ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)