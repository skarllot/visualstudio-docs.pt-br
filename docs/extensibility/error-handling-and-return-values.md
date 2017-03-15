---
title: Tratamento de erros e valores de retorno | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: 14
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
ms.openlocfilehash: c30c795363738b5715bc6d5c928ba8553d01210b
ms.lasthandoff: 02/22/2017

---
# <a name="error-handling-and-return-values"></a>Tratamento de erros e valores de retorno
Os VSPackages e COM usam a mesma arquitetura de erros. O `SetErrorInfo` e `GetErrorInfo` funções fazem parte da interface de programação de aplicativo (API) do Win32. Qualquer VSPackage no ambiente de desenvolvimento integrado (IDE) pode chamar essas APIs Win32 global para registrar informações de erros ao receber uma notificação de erro. O [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornece assemblies de interoperabilidade para gerenciar informações de erro.  
  
## <a name="interop-methods"></a>Métodos de interoperabilidade  
 Como uma conveniência, o IDE fornece um método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, para usar em vez de chamar as APIs do Win32.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> No código gerenciado usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Quando um erro `HRESULT` chega no nível de onde a mensagem de erro deve ser exibida (geralmente, esse é o objeto implementando um <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>manipulador de comando), o IDE usa outro método, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, para exibir a caixa de mensagem apropriada.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> No código gerenciado usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>  
  
 Como um implementador de VSPackage, seus objetos normalmente implementam `ISupportErrorInfo`. O `ISupportErrorInfo` interface garante que informações de erro avançado podem mover verticalmente a cadeia de chamada. Devem oferecer suporte a objetos que podem ser usados em processos ou threads `ISupportErrorInfo` para garantir que as informações de erros são empacotadas corretamente para o chamador.  
  
 Todos os objetos que estão relacionadas a VSPackages e que estão envolvidas na extensão do IDE, incluindo as fábricas de editor, editores, hierarquias e oferecidos serviços, devem dar suporte a informações de erros. Embora o IDE não requer esses objetos VSPackage implementar `ISupportErrorInfo`, ele sempre é encorajado.  
  
 O IDE é responsável por relatar informações de erro e exibi-la para um usuário de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sempre que um `HRESULT` é propagada para o IDE. O IDE também é o mecanismo para a criação de `ErrorInfo` objetos.  
  
## <a name="general-guidelines"></a>Diretrizes gerais  
 Você pode usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>métodos para definir e relatar os erros que são internos a implementação do VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> No entanto, como regra geral, siga estas diretrizes para lidar com mensagens de erro em seu VSPackage:  
  
-   Implementar `ISupportErrorInfo` em seus objetos COM VSPackage.  
  
-   Criar um mecanismo que chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>método em objetos que implementam <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> de relatório de erros  
  
-   Permitir que o IDE exibir erros aos usuários por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>  
  
## <a name="error-information-in-the-ide"></a>Informações de erro no IDE  
 As regras a seguir indicam como lidar com informações de erro no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE:  
  
-   Como uma estratégia de defesa para garantir que informações de erro obsoletos não é relatada para os usuários, funções que chamam o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>método primeiro deve chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> Passar `null` para limpar mensagens de erro em cache antes de chamar qualquer coisa que pode definir novas informações de erro.  
  
-   Funções que não reportam diretamente as mensagens de erro são permitidas apenas chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>método se eles estão retornando um erro `HRESULT`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> É permitido para limpar o `ErrorInfo` na entrada para uma função ou retornando <xref:Microsoft.VisualStudio.VSConstants.S_OK>.</xref:Microsoft.VisualStudio.VSConstants.S_OK> A única exceção a essa regra é quando uma chamada retornará um erro `HRESULT` do qual a parte destinatária pode recuperar explicitamente ou ignorar com segurança.  
  
-   Qualquer parte que explicitamente ignora um erro `HRESULT` deve chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>método <xref:Microsoft.VisualStudio.VSConstants.S_OK>.</xref:Microsoft.VisualStudio.VSConstants.S_OK> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Caso contrário, o `ErrorInfo` objeto pode ser usado acidentalmente quando outra pessoa gera um erro sem fornecer suas próprias `ErrorInfo`.  
  
-   Todos os métodos que se originam erro `HRESULT` são incentivados a chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>método para fornecer informações de erro avançadas.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Se retornado `HRESULT` é um relacionamento especial `FACILITY_ITF` erro e, em seguida, o método é necessário para fornecer correto `ErrorInfo`objeto. Se o erro retornado é um erro de sistema padrão (por exemplo, <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>e assim por diante) é aceitável para retornar o código de erro sem chamar explicitamente o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> </xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> </xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> </xref:Microsoft.VisualStudio.VSConstants.E_ABORT> </xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> Como uma estratégia de codificação defensiva, quando um erro de origem `HRESULT` (incluindo erros de sistema), sempre chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>método, com `ErrorInfo` descrevendo a falha em mais detalhes, ou `null`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>  
  
-   Todas as funções que retornam um erro foi originado por outra chamada deve passar as informações que foram recebidas de falha do chamam o `HRESULT` sem modificar o `ErrorInfo` objeto.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (automação de componente)](http://msdn.microsoft.com/en-us/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/en-us/03317526-8c4f-4173-bc10-110c8112676a)   
 [Interface ISupportErrorInfo](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)
