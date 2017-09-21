---
title: "Instru&#231;&#245;es passo a passo: baixando assemblies sat&#233;lite por demanda com a API de implanta&#231;&#227;o do ClickOnce | Microsoft Docs"
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
  - "implantação ClickOnce, download sob demanda"
  - "globalização, ClickOnce"
  - "localização, implantação ClickOnce"
  - "localização, Windows Forms"
  - "assemblies satélites, ClickOnce"
  - "Windows Forms, localização"
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: baixando assemblies sat&#233;lite por demanda com a API de implanta&#231;&#227;o do ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Aplicativos do Windows Forms podem ser configurados para várias culturas com o uso de assemblies satélites. Um *assembly satélite* é um assembly que contém recursos do aplicativo para uma cultura diferente de cultura do padrão do aplicativo.  
  
 Conforme discutido em [Localização de aplicativos ClickOnce](../deployment/localizing-clickonce-applications.md), você pode incluir vários assemblies satélite para várias culturas dentro do mesmo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação. Por padrão, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] baixará todos os assemblies satélite em sua implantação para o computador cliente, embora um único cliente provavelmente exigirá assembly satélite apenas um.  
  
 Este passo a passo demonstra como marcar seus assemblies satélites como opcional e baixar apenas o assembly precisa de um computador cliente para suas configurações de cultura atual. O procedimento a seguir usa as ferramentas disponíveis no [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Você também pode executar essa tarefa em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Consulte também [passo a passo: baixando Assemblies satélite por demanda com o ClickOnce implantação API usando o Designer](http://msdn.microsoft.com/library/ms366788\(v=vs.110\)) ou [passo a passo: baixando Assemblies satélite por demanda com o ClickOnce implantação API usando o Designer](http://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
> [!NOTE]
>  Para fins de teste, o exemplo de código a seguir programaticamente define a cultura `ja-JP`. Consulte a seção "Próximas etapas" neste tópico para obter informações sobre como ajustar esse código para um ambiente de produção.  
  
## Pré-requisitos  
 Este tópico pressupõe que você saiba como adicionar recursos localizados ao seu aplicativo usando o Visual Studio. Para obter instruções detalhadas, consulte [passo a passo: Localizando Windows Forms](https://msdn.microsoft.com/en-us/library/vstudio/y99d1cd3\(v=vs.100\).aspx).  
  
### Para baixar os assemblies satélite por demanda  
  
1.  Adicione o seguinte código ao seu aplicativo para habilitar o download sob demanda dos assemblies satélites.  
  
     [!code-cs[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]
     [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]  
  
2.  Gerar assemblies satélite para seu aplicativo usando [Resgen.exe \(Gerador de Arquivo de Recurso\)](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) ou [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Gerar um manifesto de aplicativo, ou abrir o manifesto do aplicativo existente, usando MageUI.exe. Para obter mais informações sobre essa ferramenta, consulte [MageUI.exe \(Ferramenta de Geração e Edição de Manifesto, cliente gráfico\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md).  
  
4.  Clique o **arquivos** guia.  
  
5.  Clique o **reticências** botão \(**...**\) e selecione o diretório que contém todos os assemblies e arquivos, incluindo os assemblies satélite gerado usando Resgen.exe seu aplicativo. \(Um assembly satélite terá um nome no formato *isoCode*\\ApplicationName.resources.dll, onde *isoCode* é um identificador de idioma no formato RFC 1766.\)  
  
6.  Clique em **popular** para adicionar arquivos à sua implantação.  
  
7.  Selecione o **opcional** caixa de seleção para cada assembly satélite.  
  
8.  Defina o campo de grupo para cada assembly satélite para seu identificador de idioma ISO. Por exemplo, para um assembly satélite japonês, você especificaria o nome de um grupo de download do `ja-JP`. Isso permitirá que o código adicionado na etapa 1 para baixar o assembly satélite adequado, dependendo do usuário <xref:System.Threading.Thread.CurrentUICulture%2A> configuração de propriedade.  
  
## Próximas etapas  
 Em um ambiente de produção, você provavelmente precisará remover a linha no exemplo de código define <xref:System.Threading.Thread.CurrentUICulture%2A> para um valor específico, porque será de máquinas cliente tiver o valor correto definido por padrão. Quando seu aplicativo é executado em uma máquina cliente japonês, por exemplo, <xref:System.Threading.Thread.CurrentUICulture%2A> será `ja-JP` por padrão. Definir esse valor por meio de programação é uma boa maneira de testar seus assemblies satélites antes de implantar seu aplicativo.  
  
## Consulte também  
 [Localização de aplicativos ClickOnce](../deployment/localizing-clickonce-applications.md)