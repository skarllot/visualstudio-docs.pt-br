---
title: "Parâmetros de contexto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
caps.latest.revision: 13
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 143a8738f2eb6517c1642eafd2b9629e0fa8f84d
ms.lasthandoff: 02/22/2017

---
# <a name="context-parameters"></a>Parâmetros de contexto
No [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE), você pode adicionar assistentes para a **novo projeto**, **Adicionar Novo Item**, ou **Adicionar projeto Sub** caixas de diálogo. Os assistentes adicionados estão disponíveis na **arquivo** menu ou clicando em um projeto no **Solution Explorer**. O IDE passa parâmetros de contexto para a implementação do assistente. Os parâmetros de contexto definem o estado do projeto quando o IDE chama o assistente.  
  
 O IDE inicia assistentes, definindo o <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION>sinalizador na chamada do IDE para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A>método para o projeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> </xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> Quando definido, o projeto deve fazer com que o `IVsExtensibility::RunWizardFile` método a ser executado usando o nome do assistente registrado ou GUID e outros parâmetros de contexto que o IDE passa para ele.  
  
## <a name="context-parameters-for-new-project"></a>Parâmetros de contexto para o novo projeto  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`WizardType`|Tipo de assistente registrado (<xref:EnvDTE.Constants.vsWizardNewProject>) ou o GUID que indica o tipo de assistente.</xref:EnvDTE.Constants.vsWizardNewProject> No [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementação, o GUID para o assistente é {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Uma cadeia de caracteres que é o único [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nome do projeto.|  
|`LocalDirectory`|Local do arquivos de projeto de trabalho.|  
|`InstallationDirectory`|Caminho do diretório a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é a instalação.|  
|`FExclusive`|Sinalizador booleano que indica que o projeto deve fechar soluções abertas.|  
|`SolutionName`|Nome do arquivo de solução sem a parte do diretório ou a extensão. sln. O nome do arquivo. suo também é criado usando `SolutionName`. Quando esse argumento não for uma cadeia de caracteres vazia, o assistente usa <xref:EnvDTE._Solution.Create%2A>antes de adicionar o projeto com <xref:EnvDTE._Solution.AddFromTemplate%2A>.</xref:EnvDTE._Solution.AddFromTemplate%2A> </xref:EnvDTE._Solution.Create%2A> Se esse nome é uma cadeia de caracteres vazia, use <xref:EnvDTE._Solution.AddFromTemplate%2A>sem chamar <xref:EnvDTE._Solution.Create%2A>.</xref:EnvDTE._Solution.Create%2A> </xref:EnvDTE._Solution.AddFromTemplate%2A>|  
|`Silent`|Valor booleano que indica se o assistente deve ser executado silenciosamente como se **concluir** foram clicados (`TRUE`).|  
  
## <a name="context-parameters-for-add-new-item"></a>Parâmetros de contexto para adicionar novo Item  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`WizardType`|Tipo de assistente registrado (<xref:EnvDTE.Constants.vsWizardAddItem>) ou o GUID que indica o tipo de assistente.</xref:EnvDTE.Constants.vsWizardAddItem> No [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementação, o GUID para o assistente é {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Uma cadeia de caracteres que é o único [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nome do projeto.|  
|`ProjectItems`|Local que contém os arquivos de projeto de trabalho.|  
|`ItemName`|Nome do item a ser adicionado. Esse nome é o nome de arquivo padrão ou o nome do arquivo que o usuário digita a partir de **adicionar itens** caixa de diálogo. O nome é baseado nos sinalizadores definidos no arquivo. vsdir. O nome pode ser um valor nulo.|  
|`InstallationDirectory`|Caminho do diretório a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é a instalação.|  
|`Silent`|Valor booleano que indica se o assistente deve ser executado silenciosamente como se **concluir** foram clicados (`TRUE`).|  
  
## <a name="context-parameters-for-add-sub-project"></a>Parâmetros de contexto para adicionar subprojeto  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`WizardType`|Tipo de assistente registrado (<xref:EnvDTE.Constants.vsWizardAddSubProject>) ou o GUID que indica o tipo de assistente.</xref:EnvDTE.Constants.vsWizardAddSubProject> No [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementação, o GUID para o assistente é {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Uma cadeia de caracteres que é o único [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nome do projeto.|  
|`ProjectItems`|Ponteiro para o `ProjectItems` coleção na qual o assistente opera. Esse ponteiro é passado para o Assistente de acordo com a seleção de hierarquia do projeto. Um usuário normalmente seleciona uma pasta na qual colocar o item e, em seguida, chama o projeto **Adicionar Item** caixa de diálogo.|  
|`LocalDirectory`|Local do arquivos de projeto de trabalho.|  
|`ItemName`|Nome do item a ser adicionado. Esse nome é o nome de arquivo padrão ou o nome do arquivo que o usuário digita a partir de **adicionar itens** caixa de diálogo. O nome é baseado nos sinalizadores definidos no arquivo. vsdir. O nome pode ser um valor nulo.|  
|`InstallationDirectory`|Caminho do diretório a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é a instalação.|  
|`Silent`|Valor booleano que indica se o assistente deve ser executado silenciosamente como se **concluir** foram clicados (`TRUE`).|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [Parâmetros personalizados](../../extensibility/internals/custom-parameters.md)   
 [Assistentes](../../extensibility/internals/wizards.md)   
 [Assistente (. Arquivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [Parâmetros de contexto para iniciar assistentes](http://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)
