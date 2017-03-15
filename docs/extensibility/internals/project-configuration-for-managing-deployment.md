---
title: "Configuração de gerenciamento de implantação de projeto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: 8
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
ms.openlocfilehash: 8efa2d638c00e190c847eec9967ca51febfac05b
ms.lasthandoff: 02/22/2017

---
# <a name="project-configuration-for-managing-deployment"></a>Configuração de projeto para gerenciar a implantação
Implantação é o ato de mover fisicamente os itens de saída de um processo de compilação para o local esperado para depuração e a instalação. Por exemplo, um aplicativo Web pode criado em um computador local e colocado no servidor.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]oferece suporte a duas maneiras de projetos pode estar envolvida na implantação:  
  
-   Como o assunto do processo de implantação.  
  
-   Como o Gerenciador do processo de implantação.  
  
 Antes de soluções podem ser implantadas, você deve primeiro adicionar um projeto de implantação para configurar as opções de implantação. Se o projeto de implantação ainda não existir, você será solicitado se deseja criá-lo quando você selecionar **implantar solução** do **criar** menu ou o botão direito do mouse na solução. Clicar em **Sim** abre o **adicionar novo projeto** caixa de diálogo com o **Assistente de implantação remota** projeto selecionado.  
  
 O Assistente de implantação remota solicita o tipo de aplicativo (Windows ou Web), os grupos de saída do projeto para incluir, quaisquer arquivos adicionais que você deseja incluir e o computador remoto que você deseja implantar. A última página do assistente exibe um resumo das opções selecionadas.  
  
 Projetos que são o assunto de um processo de implantação produzem itens de saída devem ser movidos para um ambiente alternativo. Saída de esses itens são descritos como parâmetros para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>interface, cujo principal propósito if permitir que os projetos para o grupo de saídas.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> Para obter mais informações relacionadas à implementação de `IVsProjectCfg2`, consulte [configuração do projeto para a saída](../../extensibility/internals/project-configuration-for-output.md).  
  
 Projetos de implantação, que gerenciem o processo de implantação, habilitar o comando implantar e respondem quando esse comando é selecionado. Implementam projetos de implantação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>interface para realizar a implantação e fazer chamadas para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback>interface relatório implantar eventos de status.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> </xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>  
  
 As configurações podem especificar dependências que afetam suas operações de compilação ou implantação. Compilar ou implantar as dependências são projetos que devem ser criados ou implantados antes ou depois que as configurações se são criadas ou implantadas. Dependências de compilação entre os projetos são descritas com o <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency>da interface e implantar dependências com o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> </xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> Para obter mais informações, consulte [configuração do projeto para criação de](../../extensibility/internals/project-configuration-for-building.md).  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciar opções de configuração](../../extensibility/internals/managing-configuration-options.md)   
 [Configuração de projeto para criação](../../extensibility/internals/project-configuration-for-building.md)   
 [Configuração de projeto para saída](../../extensibility/internals/project-configuration-for-output.md)
