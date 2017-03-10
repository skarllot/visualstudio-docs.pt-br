---
title: "Instru&#231;&#245;es passo a passo: baixando assemblies sat&#233;lite por demanda com a API de implanta&#231;&#227;o do ClickOnce usando o designer | Microsoft Docs"
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
  - "implantação ClickOnce, globalização"
  - "implantação ClickOnce, localização"
  - "ClickOnce, download sob demanda"
  - "localização, Windows Forms"
  - "explicações passo a passo, localização"
  - "Windows Forms, globalização"
  - "Windows Forms, localização"
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: baixando assemblies sat&#233;lite por demanda com a API de implanta&#231;&#227;o do ClickOnce usando o designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Aplicativos do Windows Forms podem ser configurados para várias culturas com o uso de assemblies satélites.  Um *assembly satélite* é um assembly que contém recursos do aplicativo para uma cultura diferente de cultura do padrão do aplicativo.  
  
 Conforme discutido em [Localização de aplicativos ClickOnce](../deployment/localizing-clickonce-applications.md), você pode incluir vários assemblies satélite para várias culturas dentro do mesmo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação.  Por padrão, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] baixará todos os assemblies satélite em sua implantação para o computador cliente, embora um único cliente provavelmente exigirá assembly satélite apenas um.  
  
 Este passo a passo demonstra como marcar seus assemblies satélites como opcional e baixar apenas o assembly precisa de um computador cliente para suas configurações de cultura atual.  
  
> [!NOTE]
>  Para fins de teste, os exemplos de código a seguir programaticamente definem a cultura `ja-JP`.  Consulte a seção "Próximas etapas" neste tópico para obter informações sobre como ajustar esse código para um ambiente de produção.  
  
### Marcar assemblies satélite como opcional  
  
1.  Criar o projeto.  Isso gerará assemblies satélite para todas as culturas que você estiver localizando a.  
  
2.  Clique no nome do projeto no Solution Explorer e clique em **propriedades**.  
  
3.  Clique o **publicar** guia e, em seguida, clique em **arquivos de aplicativo**.  
  
4.  Selecione o **Mostrar todos os arquivos** caixa de seleção para exibir os assemblies satélite.  Por padrão, todos os assemblies satélite serão incluídos na implantação e estará visíveis na caixa de diálogo.  
  
     Um assembly satélite terá um nome no formato *isoCode*\\ApplicationName.resources.dll, onde *isoCode* é um identificador de idioma no formato RFC 1766.  
  
5.  Clique em **novo...** no **Download grupo** lista para cada identificador de idioma.  Quando solicitado a fornecer um nome de grupo de download, insira o identificador de idioma.  Por exemplo, para um assembly satélite japonês, você especificaria o nome do grupo de download `ja-JP`.  
  
6.  Feche o **arquivos de aplicativo** caixa de diálogo.  
  
### Para baixar os assemblies satélite por demanda em c\#  
  
1.  Abra o arquivo Program.cs.  Se você não vir esse arquivo no Solution Explorer, selecione o projeto e sobre o **projeto** menu, clique em **Mostrar todos os arquivos**.  
  
2.  Use o código a seguir para baixar o assembly satélite adequado e iniciar o aplicativo.  
  
     [!code-cs[ClickOnce.SatelliteAssemblies#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]  
  
### Para baixar os assemblies satélite por demanda no Visual Basic  
  
1.  No **propriedades** janela do aplicativo, clique o **aplicativo** guia.  
  
2.  Na parte inferior da página da guia, clique em **Exibir eventos do aplicativo**.  
  
3.  Adicione a instrução imports no início do arquivo Project.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]  
  
4.  Adicione o seguinte código para o `MyApplication` classe.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]  
  
## Próximas etapas  
 Em um ambiente de produção, você provavelmente precisará remover a linha nos exemplos de código que define <xref:System.Threading.Thread.CurrentUICulture%2A> para um valor específico, porque será de máquinas cliente tiver o valor correto definido por padrão.  Quando seu aplicativo é executado em uma máquina cliente japonês, por exemplo, <xref:System.Threading.Thread.CurrentUICulture%2A> será `ja-JP` por padrão.  Definir de forma programática é uma boa maneira de testar seus assemblies satélites antes de implantar seu aplicativo.  
  
## Consulte também  
 [Instruções passo a passo: baixando assemblies satélite por demanda com a API de implantação do ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)   
 [Localização de aplicativos ClickOnce](../deployment/localizing-clickonce-applications.md)