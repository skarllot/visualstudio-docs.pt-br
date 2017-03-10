---
title: "Elemento &lt;entryPoint&gt;(aplicativo ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#commandLine"
  - "urn:schemas-microsoft-com:asm.v2#entryPoint"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Elemento <entryPoint> (manifesto do aplicativo ClickOnce)"
  - "manifestos [ClickOnce], Elemento entryPoint"
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;entryPoint&gt;(aplicativo ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica o assembly que deve ser executado quando este [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo é executado em um computador cliente.  
  
## Sintaxe  
  
```  
  
      <entryPoint  
   name  
>  
   <assemblyIdentity  
      name  
      version  
      processorArchitecture  
      language  
   />  
   <commandLine  
      file  
      parameters  
   />  
   <customHostRequired />  
   <customUX />  
</entryPoint>  
```  
  
## Elementos e atributos  
 O `entryPoint` elemento é obrigatório e está sendo o `urn:schemas-microsoft-com:asm.v2` espaço para nome.  Pode haver apenas um `entryPoint` elemento definido em um manifesto de aplicativo.  
  
 O `entryPoint` elemento tem o atributo a seguir.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`name`|Opcional.  Esse valor não é usado por.NET Framework.|  
  
 `entryPoint`possui os seguintes elementos.  
  
## assemblyIdentity  
 Obrigatório.  A função do `assemblyIdentity` e seus atributos é definida na [Elemento \<assemblyIdentity\>](../deployment/assemblyidentity-element-clickonce-application.md).  
  
 O `processorArchitecture` atributos desse elemento e o `processorArchitecture` atributo definido na `assemblyIdentity` em outro lugar no aplicativo manifesto deve coincidir.  
  
## linha de comando  
 Obrigatório.  Deve ser um filho do `entryPoint` elemento.  Ele não tem nenhum elemento filho e tem os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`file`|Obrigatório.  Uma referência local para a inicialização do assembly para o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  Esse valor não pode conter barra \(\/\) ou separadores de caminho invertida \(\).|  
|`parameters`|Obrigatório.  Descreve a ação a ser executada com o ponto de entrada.  O único valor válido é  `Executar`; Se for fornecida uma seqüência de caracteres em branco,  `Executar` será adotada.|  
  
## customHostRequired  
 Opcional.  Se incluída, especifica que essa implantação contém um componente que será implantado dentro de um host personalizado e não é um aplicativo autônomo.  
  
 Se esse elemento estiver presente, o `assemblyIdentity` e `commandLine` elementos não também devem estar presentes.  Se estiverem, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] irá gerar um erro de validação durante a instalação.  
  
 Este elemento tem nenhum atributo e sem filhos.  
  
## customUX  
 Opcional.  Especifica que o aplicativo está instalado e mantido por um instalador personalizado e não cria uma entrada de menu Iniciar, atalhos ou adicionar ou remover entrada de programas.  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 Um aplicativo que inclui o elemento customUX deve fornecer um instalador personalizado que usa o <xref:System.Deployment.Application.InPlaceHostingManager> classe para executar operações de instalar.  Um aplicativo com este elemento não pode ser instalado clicando duas vezes em seu bootstrapper pré\-requisito de manifesto ou Setup. exe.  O instalador personalizado pode criar entradas do menu Iniciar, atalhos e entradas de adicionar ou remover programas.  Se o instalador personalizado não cria uma entrada de adicionar ou remover programas, ele deve armazenar o identificador de assinatura fornecido pelo <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> propriedade e permitem ao usuário para desinstalar o aplicativo mais tarde, chamando o <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> método.  Para obter mais informações, consulte [Instruções passo a passo: criando um instalador personalizado para um aplicativo ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).  
  
## Comentários  
 Esse elemento identifica o ponto de montagem e de entrada para o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  
  
 Não é possível usar `commandLine` para passar parâmetros para o aplicativo em tempo de execução.  Você pode acessar parâmetros de seqüência de caracteres de consulta para um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] a implantação do aplicativo de <xref:System.AppDomain>.  Para obter mais informações, consulte [Como recuperar informações de cadeia de caracteres de consulta em um aplicativo ClickOnce online](../Topic/How%20to:%20Retrieve%20Query%20String%20Information%20in%20an%20Online%20ClickOnce%20Application.md).  
  
## Exemplo  
 O exemplo de código a seguir ilustra um `entryPoint` elemento em um manifesto de aplicativo para um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  Este exemplo de código é parte de um exemplo maior fornecido para o  [O manifesto de aplicativo de ClickOnce](../deployment/clickonce-application-manifest.md) tópico.  
  
```  
<!-- Identify the main code entrypoint. -->  
<!-- This code runs the main method in an executable assembly. -->  
  <entryPoint>  
    <assemblyIdentity   
      name="MyApplication"   
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
```  
  
## Consulte também  
 [Manifesto de aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)