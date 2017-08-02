---
title: "Configuração de criação de projeto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 2538ec8bf94740aeb3f8161e714a3687dd48cf65
ms.lasthandoff: 02/22/2017

---
# <a name="project-configuration-for-building"></a>Configuração de projeto para criação
A lista de configurações de solução para uma determinada solução é gerenciada pela caixa de diálogo Configurações da solução.  
  
 Um usuário pode criar configurações adicionais da solução, cada um com seu próprio nome exclusivo. Quando o usuário cria uma nova configuração de solução, o IDE padrão é o nome de configuração correspondente em projetos ou depuração não se existir nenhum nome correspondente. O usuário pode alterar a seleção para atender aos requisitos específicos, se necessário. A única exceção a esse comportamento é quando o projeto oferece suporte a uma configuração que corresponde ao nome da nova configuração de solução. Por exemplo, suponha que uma solução que contém Projeto1 e Projeto2. Projeto1 tem configurações de projeto MyConfig1, varejo e depuração. Projeto2 tem configurações de projeto MyConfig2, varejo e depuração.  
  
 Se o usuário cria uma nova configuração de solução chamada MyConfig2, Projeto1 associa sua configuração de depuração para a configuração da solução por padrão. Por padrão, Projeto2 também associa sua configuração MyConfig2 para a configuração da solução.  
  
> [!NOTE]
>  Associação diferencia maiusculas de minúsculas.  
  
 Quando o usuário seleciona o **seleção múltipla** item na lista suspensa de configuração, o ambiente exibe uma caixa de diálogo que fornece a lista de configurações disponíveis.  
  
 ![Várias configurações](~/docs/extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs")  
Várias configurações  
  
 Na caixa de diálogo, o usuário pode selecionar uma ou várias configurações. Quando selecionado, os valores de propriedade exibidos na caixa de diálogo páginas de propriedade refletem a interseção dos valores para as configurações selecionadas.  
  
 Consulte [configuração da solução](../../extensibility/internals/solution-configuration.md) para obter informações relacionadas a adicionar e renomear as configurações para soluções e projetos.  
  
 Dependências do projeto e ordem de compilação são independentes de configuração da solução: ou seja, você só pode definir a árvore de uma dependência para todos os projetos na solução. Clicando duas vezes a solução ou projeto e selecionando o **dependências do projeto** ou **ordem de compilação de projeto** opção abre a **dependências do projeto** caixa de diálogo. Ela também pode ser aberta pelo **projeto** menu.  
  
 ![Dependências do projeto](~/docs/extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
Dependências do projeto  
  
 Dependências do projeto determinam a ordem em que os projetos são compilados. Use a guia ordem de compilação na caixa de diálogo para exibir a ordem exata em que projetos dentro de uma solução de compilação e use a guia dependências para modificar a ordem de compilação.  
  
> [!NOTE]
>  Projetos na lista que suas caixas de seleção marcadas, mas aparecem esmaecidos foram adicionados pelo ambiente devido a dependências explícitas especificadas pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency>ou o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency>interfaces e não pode ser alterado.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> </xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> Por exemplo, adicionando uma referência de projeto de um [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projeto para outro projeto automaticamente adiciona uma dependência de compilação que só pode ser removida, exclua a referência. Não não possível selecionar projetos cujas caixas de seleção estão desmarcadas e aparecem esmaecidas porque isso criaria um loop de dependência (por exemplo, Projeto1 seria dependente Projeto2 e Projeto2 seria dependente Projeto1), que poderia parar a compilação.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]processos de compilação incluem a compilação típica e operações de conexão que são chamadas com um único comando de compilação. Dois outros processos de compilação também podem ser suportados: uma operação de limpeza para excluir todos os itens de saída de uma compilação anterior e uma verificação atualizada para determinar se um item de saída em uma configuração foi alterada.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>objetos de retorno correspondente <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>(retornado de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>) para gerenciar seus processos de compilação.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> Para relatar o status de uma operação de compilação enquanto ele está ocorrendo, configurações de fazem chamadas para <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>, uma interface implementada pelo ambiente e qualquer outro objeto interessado em eventos de status de compilação.</xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>  
  
 Depois de criado, as definições de configuração podem ser usadas para determinar se ou não pode ser executados sob o controle do depurador. Implementam configurações <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>para oferecer suporte à depuração.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>  
  
 Depois de implementar as dependências do projeto, você pode manipular programaticamente as dependências por meio do modelo de automação. Você chama <xref:EnvDTE.SolutionBuild.BuildDependencies%2A>no modelo de automação.</xref:EnvDTE.SolutionBuild.BuildDependencies%2A> Não há nenhuma interface de nível de API do VSIP disponível que permitem a manipulação direta de configurações do Gerenciador de compilação da solução e suas propriedades.  
  
 Além disso, você pode fornecer uma grade na janela de dependências do projeto. Para obter mais informações, consulte [propriedades exibir grade](../../extensibility/internals/properties-display-grid.md).  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciar opções de configuração](../../extensibility/internals/managing-configuration-options.md)   
 [Configuração de projeto para gerenciar a implantação](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [Configuração de projeto para saída](../../extensibility/internals/project-configuration-for-output.md)
