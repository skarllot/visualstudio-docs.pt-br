---
title: "Serviços relacionados e Interfaces (VSPackage de controle de origem) | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
caps.latest.revision: 26
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
ms.openlocfilehash: 6d16e8eb229cd5187ae91630d9330a0e0f24eda2
ms.lasthandoff: 02/22/2017

---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Interfaces (VSPackage de controle de origem) e serviços relacionados
Esta seção lista todos os a fonte de controle interfaces relacionadas VSPackage o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]. O controle de origem VSPackage implementa algumas dessas interfaces e usa outras para realizar tarefas de controle de origem.  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfaces implementadas por e para VSPackages de controle de origem  
 As seguintes interfaces são descritas no [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], e o controle de origem VSPackage implementa um subconjunto delas dependendo de seu conjunto de recursos desejado. Algumas interfaces estão marcados como obrigatório e deve ser implementado por todos os controles de fonte VSPackage.  
  
 Para as interfaces que não implementa um pacote, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornece uma implementação padrão. Observe que a implementação padrão é criada para o caso quando nenhum VSPackage é registrado e nenhum projeto é controlado. Um controle de fonte escrito corretamente VSPackage implementa interfaces necessários em vez de deixá-lo para a implementação padrão dessas interfaces.  
  
 Um controle de origem VSPackage deve implementar um serviço particular que encapsula a algumas ou todas as seguintes interfaces.  
  
 Interfaces são:  
  
-   Obrigatório: A entidade apropriada (projeto de controle de origem VSPackage, Stub de controle de origem,) deve implementar a interface.  
  
-   Recomendado: A entidade deve implementar essa interface; Caso contrário, a funcionalidade de controle do código-fonte pode ser limitada.  
  
-   Opcional: a entidade pode implementar essa interface para fornecer um conjunto mais rico de recursos.  
  
|Interface|Finalidade|Implementado por|Implementar?|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2></xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Editores de chamar essa interface antes de modificar ou salvar um arquivo. O controle de origem VSPackage pode extrair o arquivo ou negar a operação se o check-out falhar.|Controle de origem VSPackage|Recomendado|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Essa interface fornece funcionalidade de controle de origem básico para projetos, como registrar e cancelar o registro de projetos com controle de origem e fornecendo suporte para glifos de controle de origem básico.|Controle de origem VSPackage|Necessária|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Essa interface é obtida a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>usando o <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>função, ou simplesmente converter o objeto que implementa `IVsHierarchy` para `IVsSccProject2`.</xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Ele é usado para obter os arquivos sob controle de origem em um projeto ou para informar o projeto do status atual de controle de origem ou local.|Projeto|Necessária|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|O módulo de integração usa essa interface para definir o VSPackage ativo atual.|Controle de origem VSPackage|Necessária|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Essa interface é baseada em um modelo de assinatura. Qualquer VSPackage pode sinalizar que deseja receber eventos de documento e ser informada pelo shell sobre eventos que estão prestes a acontecer. Ele é implementado e tratado por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], que passa a implementação de eventos o `IVsTrackProjectDocumentsEvents2` para o VSPackage.|Stub de controle de origem|Necessária|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|Essa interface fornece processamento em lotes, operações de leitura/gravação sincronizados e um avançado `OnQueryAddFiles` método.|Stub de controle de origem|Necessária|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**Gerenciador de soluções** e projetos chamam esta interface quando novos arquivos são adicionados aos projetos ou quando arquivos e pastas são renomeadas ou excluídas dos projetos. O controle de origem VSPackage pode extrair o arquivo de projeto ou cancelar a operação.|Controle de origem VSPackage|Recomendado|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**Gerenciador de soluções** e projetos de chamar essa interface em resposta às chamadas feitas para os métodos da interface IVstrackProjectDocuments3. O controle de origem VSPackage pode controlar operações em lote, sincronizadas operações de leitura/gravação e trabalhar com mais avançados `OnQueryAddFiles` método.|Controle de origem VSPackage|Recomendado|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|Essa interface oferece suporte para projetos Web gerenciamento de inscrição.|Controle de origem VSPackage|Recomendado|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|Essa interface é usada para recuperar as dicas de ferramentas para os arquivos de controle do código-fonte nos projetos.|Controle de origem VSPackage|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|Essa interface oferece suporte à extensão do namespace.|Controle de origem VSPackage|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|O VSPackage usa essa interface para integrar uma extensão de namespace para o **novo**, **abrir**, ou **salvar** caixas de diálogo. Consequentemente, projetos podem ser automaticamente adicionados ao controle de origem na criação ou adicionados ao controle de origem quando salvar operação estiver em vigor.|Controle de origem VSPackage|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|O VSPackage usa essa interface para definir glifos adicionais como glifos de controle de origem para nós **Solution Explorer**.|Controle de origem VSPackage|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|O **adicionar** caixa de diálogo para projetos Web usa essa interface. Ele fornece métodos para navegar para um local de controle de origem e para abrir um projeto Web adicionado anteriormente no repositório de controle de origem nesse local.|Controle de origem VSPackage|Recomendado|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc></xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|Essa interface oferece suporte para o carregamento assíncrono (em segundo plano) de projetos de controle de origem.|Controle de origem VSPackage|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|Essa interface permite que projetos observar o progresso do carregamento assíncrono iniciado pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|Projeto|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|Essa interface permite que o IDE consultar o controle de origem ativa VSPackage. O IDE consulta o valor de configurações de controle de origem que têm significado, mesmo quando não há nenhum controle de origem ativa que VSPackage é registrado. Essa interface é implementada e manipulada pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].|Stub de controle de origem|Necessária|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|Essa interface é usada no registro de controle da fonte de VSPackage.|Stub de controle de origem|Necessária|  
|<xref:EnvDTE.SourceControl></xref:EnvDTE.SourceControl>|Essa interface é usada na automação. Como tal, ele expõe apenas as funções que podem ser executadas sem exibir nenhuma interface de usuário.|Controle de origem VSPackage|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|Essa interface é usada para salvar a fonte de controle de configurações no arquivo de solução (. sln). As configurações incluem o local do controle de origem e os sinalizadores de status de controle de origem.|Controle de origem VSPackage|Recomendado|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|Essa interface é usada para salvar as configurações de controle de origem no arquivo de opções (. suo) da solução. Isso pode incluir configurações de controle de origem de específicas do usuário, tais como localização de inscrição do usuário atual.|Controle de origem VSPackage|Recomendado|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|Essa interface é usada para monitorar eventos para executar operações como check-in de arquivos de projeto antes de fechar soluções ou obtendo novos arquivos de controle de origem ao abrir um projeto.|Controle de origem VSPackage|Recomendado|  
  
## <a name="see-also"></a>Consulte também  
 [Elementos de design](../../extensibility/internals/source-control-vspackage-design-elements.md)
