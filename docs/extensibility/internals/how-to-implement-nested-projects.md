---
title: 'Como: implementar projetos aninhados | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
caps.latest.revision: 17
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
ms.openlocfilehash: 83c074fab1b007d8507c45ccd669a195c610fc5d
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-implement-nested-projects"></a>Como: implementar projetos aninhados
Quando você cria um tipo de projeto aninhado existe são uma várias etapas adicionais que devem ser implementadas. Um projeto pai leva em algumas das responsabilidades mesmo que a solução tem para seus projetos aninhados (filho). O projeto pai é um contêiner de projetos semelhantes a uma solução. Em particular, há vários eventos que devem ser gerados pela solução e pelos projetos pai para criar a hierarquia de projetos aninhados. Esses eventos são descritos no seguinte processo para a criação de projetos aninhados.  
  
### <a name="to-create-nested-projects"></a>Para criar projetos aninhados  
  
1.  O ambiente de desenvolvimento integrado (IDE) carrega as informações de inicialização e o arquivo de projeto do projeto pai chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> O projeto pai é criado e adicionado à solução.  
  
    > [!NOTE]
    >  Neste ponto, é muito cedo no processo para o projeto pai criar o projeto aninhado, pois o projeto pai deve ser criado antes que os projetos de filho podem ser criados. Seguindo essa sequência, o projeto pai pode aplicar configurações aos projetos filho e os projetos de filho podem adquirir informações dos projetos pai, se necessário. Essa sequência é se ela é necessária por clientes como o controle do código fonte (SCC) e o Gerenciador de soluções.  
  
     O projeto pai deve aguardar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A>método a ser chamado pelo IDE para criar seu aninhado (filho) projeto ou projetos.</xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A>  
  
2.  O IDE chama `QueryInterface` no projeto pai para <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject> Se essa chamada for bem-sucedida, o IDE chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A>método do pai para abrir todos os projetos aninhados para o projeto pai.</xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A>  
  
3.  As chamadas de projeto pai o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A>método para notificar os ouvintes que aninhado projetos estão prestes a ser criado.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> Por exemplo, o SCC, está escutando a esses eventos para saber se as etapas no processo de criação de projeto e solução estão ocorrendo em ordem. Se as etapas ocorrerão fora de ordem, a solução pode não ser registrada com o controle do código fonte corretamente.  
  
4.  As chamadas de projeto pai <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A>método ou o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A>método em cada um dos seus projetos filho.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A>  
  
     Você passar <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS>para o `AddVirtualProject` método para indicar que o projeto (aninhado) virtual deve ser adicionado à janela do projeto, excluída da compilação, adicionado ao controle do código fonte e assim por diante.</xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> `VSADDVPFLAGS`permite controlar a visibilidade do projeto aninhado e indicar qual funcionalidade está associada a ele.  
  
     Se você recarregar um projeto anteriormente existente filho que tem um GUID armazenado no arquivo de projeto do projeto pai, as chamadas de projeto pai do projeto `AddVirtualProjectEx`. A única diferença entre `AddVirtualProject` e `AddVirtualProjectEX` que `AddVirtualProjectEX` tem um parâmetro para habilitar o projeto pai especificar um por instância `guidProjectID` para o projeto filho habilitar <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A>para funcionar corretamente.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A>  
  
     Se não houver nenhum GUID disponível, como quando você adiciona um novo projeto aninhado, a solução cria um projeto de quando ele é adicionado ao pai. É responsabilidade do projeto pai para manter esse GUID em seu arquivo de projeto do projeto. Se você excluir um projeto aninhado, o GUID para o projeto também pode ser excluído.  
  
5.  O IDE chama o `M:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren` método em cada projeto filho do projeto pai.  
  
     O projeto pai deve implementar `IVsParentProject` para aninhar os projetos. Mas o pai do projeto nunca chamadas `QueryInterface` para `IVsParentProject` mesmo se tiver projetos pai abaixo dele. A solução lida com a chamada para `IVsParentProject` e, se ele é implementado, chama `OpenChildren` para criar os projetos aninhados. `AddVirtualProjectEX`sempre é chamado de `OpenChildren`. Ele nunca deve ser chamado pelo projeto pai para manter a hierarquia de eventos de criação em ordem.  
  
6.  O IDE chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>método no projeto filho.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>  
  
7.  As chamadas de projeto pai o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A>método para notificar os ouvintes que foram criados os projetos filho do pai.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A>  
  
8.  O IDE chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A>método no projeto pai depois que todos os projetos filho foram abertos.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A>  
  
     Se ele ainda não existir, o projeto pai cria um GUID para cada projeto aninhado chamando `CoCreateGuid`.  
  
    > [!NOTE]
    >  `CoCreateGuid`uma API COM é chamada quando um GUID deve ser criado. Para obter mais informações, consulte `CoCreateGuid` e GUIDs na biblioteca MSDN.  
  
     O projeto pai armazena esse GUID em seu arquivo de projeto a ser recuperado na próxima vez que ele é aberto no IDE. Consulte a etapa 4 para obter mais informações relacionadas a chamada de `AddVirtualProjectEX` para recuperar o `guidProjectID` para o projeto filho.  
  
9. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>método é chamado para o pai ItemID por convenção delegar para o projeto aninhado.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> O <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>recupera as propriedades do nó que aninha um projeto que você deseja delegar em quando é chamado no pai.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>  
  
     Como projetos pai e filho são instanciados programaticamente, você pode definir propriedades em projetos aninhados neste momento.  
  
    > [!NOTE]
    >  Não só você recebe as informações de contexto do projeto aninhado, mas você também pode perguntar se o projeto pai tem qualquer contexto para aquele item verificando <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> Dessa forma, você pode adicionar atributos adicionais de ajuda dinâmica e opções de menu específicas para projetos aninhados individuais.  
  
10. A hierarquia é criada para exibição no Gerenciador de soluções com uma chamada para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
     Você passa a hierarquia para o ambiente por meio `GetNestedHierarchy` para criar a hierarquia para exibição no Gerenciador de soluções. Dessa forma, a solução sabe que o projeto existe e pode ser gerenciado pelo Gerenciador de compilação para compilar ou pode permitir que os arquivos do projeto para ser colocado sob controle do código fonte.  
  
11. Quando todos os projetos aninhados para Projeto1 tem sido criados, controle é passado de volta para a solução e o processo é repetido para Project2.  
  
     Esse mesmo processo para a criação de projetos aninhados ocorre para um projeto filho que tem um filho. Nesse caso, se BuildProject1, que é um filho do Projeto1, tinha projetos filho, eles seriam criados após BuildProject1 e antes Project2. O processo é recursiva e a hierarquia é criada da parte superior para baixo.  
  
     Quando um projeto aninhado é fechado porque o usuário fechou a solução ou específicos do projeto em si, o outro método em `IVsParentProject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>, é chamado.</xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A> O projeto pai envolve chamadas para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A>método com o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A>e o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A>métodos para notificar os ouvintes para eventos de solução que os projetos aninhados estão sendo fechados.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A>  
  
 Os tópicos a seguir lidam com vários outros conceitos a serem considerados ao implementar projetos aninhados:  
  
 [Considerações para descarregando e recarregando projetos aninhados](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)  
  
 [Suporte do Assistente para projetos aninhados](../../extensibility/internals/wizard-support-for-nested-projects.md)  
  
 [Implementar manipulação de comando para projetos aninhados](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)  
  
 [A caixa de diálogo AddItem de filtragem para projetos aninhados](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)  
  
## <a name="see-also"></a>Consulte também  
 [Adicionando itens a adicionar novo Item caixas de diálogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registrando o projeto e modelos de Item](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Lista de verificação: Criar novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Parâmetros de contexto](../../extensibility/internals/context-parameters.md)   
 [Assistente (. Arquivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
