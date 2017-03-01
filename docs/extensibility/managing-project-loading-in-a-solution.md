---
title: "Ao carregar o projeto em uma solução de gerenciamento | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
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
ms.openlocfilehash: 7482aa3a8d08827c25de7db34a6f3a426102f57a
ms.lasthandoff: 02/22/2017

---
# <a name="managing-project-loading-in-a-solution"></a>Gerenciando ao carregar o projeto em uma solução
Soluções do Visual Studio podem conter um grande número de projetos. O comportamento do Visual Studio padrão é carregar todos os projetos em uma solução no momento em que a solução for aberta e não para permitir que o usuário acesse qualquer um dos projetos até que todos eles concluiu o carregamento. Quando o processo de carregamento do projeto irão durar mais de dois minutos, uma barra de progresso é exibida mostrando o número de projetos carregado e o número total de projetos. O usuário pode descarregar projetos enquanto estiver trabalhando em uma solução com vários projetos, mas esse procedimento tem algumas desvantagens: os projetos descarregados não são criados como parte de um comando recompilar solução e descrições do tipo IntelliSense tipos e membros de projetos fechados não são exibidos.  
  
 Os desenvolvedores podem reduzir os tempos de carregamento de solução e gerenciar o comportamento de carregamento, criando uma carga de solução gerente de projeto. O Gerenciador de carga de solução pode definir outro projeto Carregando as prioridades de projetos específicos ou tipos de projeto, certifique-se de que os projetos sejam carregados antes de iniciar uma compilação em segundo plano, atrasar o carregamento de plano de fundo até que outras tarefas em segundo plano sejam concluídas e realizar outras tarefas de gerenciamento de carga do projeto.  
  
## <a name="project-loading-priorities"></a>Carregando as prioridades do projeto  
 O Visual Studio define quatro prioridades de carregamento do projeto diferente:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>(o padrão): quando uma solução é aberta, projetos são carregados de forma assíncrona.</xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> Se essa prioridade é definida em um projeto descarregado depois que a solução já está aberta, o projeto será carregado no próximo ponto ocioso.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: quando uma solução for aberta, os projetos são carregados em segundo plano, permitindo que o usuário acessar os projetos que são carregados sem ter que aguardar até que todos os projetos são carregados.</xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: projetos são carregados quando elas são acessadas.</xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> Um projeto é acessado quando o usuário expande o nó do projeto no Solution Explorer, quando um arquivo pertencente ao projeto é aberto quando a solução for aberta porque ele está na lista de documentos abertos (mantida no arquivo de opções de usuário da solução), ou quando outro projeto que está sendo carregado tem uma dependência no projeto. Esse tipo de projeto não é carregado automaticamente antes de iniciar um processo de compilação; o Gerenciador de carga de solução é responsável por garantir que todos os projetos necessários estão carregados. Esses projetos também devem ser carregados antes de iniciar um localizar/substituir em arquivos em toda a solução.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: projetos não devem ser carregados, a menos que o usuário solicita explicitamente.</xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> Esse é o caso quando projetos são descarregados explicitamente.  
  
## <a name="creating-a-solution-load-manager"></a>Criando uma carga de solução manager  
 Os desenvolvedores podem criar Gerenciador de uma carga de solução implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager>e sugerindo que o Visual Studio que o Gerenciador de carga de solução está ativo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager>  
  
#### <a name="activating-a-solution-load-manager"></a>Ativando um Gerenciador de carga de solução  
 O Visual Studio permite que apenas um Gerenciador de carga de solução em um determinado momento, portanto você precisará informar o Visual Studio quando você quiser ativar sua carga de solução gerenciador. Se um segundo Gerenciador de carga de solução for ativado posteriormente, o Gerenciador de solução de carga será desconectada.  
  
 Você deve obter o <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>de serviço e defina o <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>propriedade:</xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> </xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
```c#  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Implementando IVsSolutionLoadManager  
 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A>método é chamado durante o processo de abertura da solução.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> Para implementar esse método, você deve usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport>serviço para definir a prioridade de carga para o tipo de projeto que você deseja gerenciar.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> Por exemplo, o código a seguir define tipos de projeto c# para carregar em segundo plano:  
  
```c#  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>método é chamado quando o Visual Studio está sendo desligado ou quando um pacote diferente como o Gerenciador de carga de solução ativa chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A>com o <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>propriedade.</xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Estratégias para diferentes tipos de Gerenciador de carga de solução  
 Você pode implementar gerenciadores de carga de solução de maneiras diferentes, dependendo dos tipos de soluções que eles devem gerenciar.  
  
 Se o Gerenciador de carga de solução destina-se para gerenciar a solução de carregamento em geral, ele pode ser implementado como parte de um VSPackage. O pacote deve ser definido como autoload adicionando- <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>sobre o VSPackage com um valor de <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>.</xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> </xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> O Gerenciador de carga de solução pode ser ativado no <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>método.</xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>  
  
> [!NOTE]
>  Para obter mais informações sobre pacotes realiza o carregamento automático, consulte [VSPackages Carregando](../extensibility/loading-vspackages.md).  
  
 Como o Visual Studio reconhece somente o último solução Gerenciador de carga para ser ativado, gerentes de carga de solução geral sempre devem detectar se há um Gerenciador de carga existente antes de ativar a mesmos. Se chamar GetProperty() no serviço de solução para <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>retorna `null`, não há nenhum Gerenciador de carga de solução ativa.</xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> Se não retornar nulo, verifique se o objeto é o mesmo que o Gerenciador de carga de solução.  
  
 Se o Gerenciador de carga de solução deve gerenciar apenas alguns tipos de solução, o VSPackage pode assinar eventos de carga de solução (chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) e usar o manipulador de eventos para <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>para ativar o Gerenciador de carga de solução.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>  
  
 Se o Gerenciador de carga de solução deve gerenciar apenas soluções específicas, as informações de ativação podem ser persistente como parte do arquivo de solução. Para fazer isso, chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>para a seção de solução de pré-lançamento.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>  
  
 Os gerentes de carga de solução específica devem desativar-se na <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A>manipulador de eventos, para não entrar em conflito com outros gerenciadores de carga de solução.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A>  
  
 Se precisar de um Gerenciador de carga de solução somente para persistir as prioridades do projeto global de carga (por exemplo, propriedades definidas em uma página de opções), você pode ativar o Gerenciador de carga de solução no <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>manipulador de eventos, mantenha a configuração nas propriedades da solução e desativar o Gerenciador de carga de solução.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>  
  
## <a name="handling-solution-load-events"></a>Manipulação de eventos de carga de solução  
 Para assinar eventos de carregamento de solução, chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>quando você ativar o Gerenciador de carga de solução.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> Se você implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, você pode responder a eventos relacionados ao projeto diferente prioridades de carregamento.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Isso é disparado antes de uma solução é aberta.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> Você pode usá-lo para alterar o projeto de carregamento de prioridade para os projetos na solução.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Isso é acionado depois que a solução é completamente carregada, mas antes de plano de fundo de carregamento do projeto começa novamente.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A> Por exemplo, um usuário pode ter acessado como um projeto cuja prioridade de carga é LoadIfNeeded ou o Gerenciador de solução de carga pode ter alterado uma prioridade de carga do projeto para BackgroundLoad, que deve iniciar um carregamento em segundo plano do projeto.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Isso é acionado depois que uma solução totalmente inicialmente é carregada, se ou não há um Gerenciador de carga de solução.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A> Ele também é acionado depois de carga de plano de fundo ou demanda de carga sempre que a solução se tornar totalmente carregada. Ao mesmo tempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid>é reativado.</xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Isso é acionado antes do carregamento de um projeto (ou projetos).</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A> Para garantir que outros processos em segundo plano sejam concluídos antes dos projetos são carregados, defina `pfShouldDelayLoadToNextIdle` para **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Isso é acionado quando um lote de projetos está prestes a ser carregado.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A> Se `fIsBackgroundIdleBatch` for true, os projetos devem ser carregados em segundo plano; se `fIsBackgroundIdleBatch` for false, os projetos devem ser carregados síncrona como resultado de uma solicitação de usuário, por exemplo se o usuário expande um projeto pendentes no Gerenciador de soluções. Você pode implementar isso para fazer o trabalho caro que outra forma precisaria ser feita em <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterOpenProject%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterOpenProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Isso é acionado depois que um lote de projetos foi carregado.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Detectar e gerenciar a solução e o carregamento do projeto  
 Para detectar o estado de carregamento de projetos e soluções, chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A>com os seguintes valores:</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retorna `true` se a solução e todos os seus projetos forem carregados, caso contrário, `false`.</xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retorna `true` se um lote de projetos estão atualmente sendo carregados em segundo plano, caso contrário, `false`.</xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retorna `true` se um lote de projetos estão atualmente sendo carregados síncrona como resultado de um comando de usuário ou outro carregamento explícito, caso contrário, `false`.</xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` retorna `true` se a solução está atualmente sendo fechada, caso contrário, `false`.</xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` retorna `true` se uma solução está atualmente sendo aberta, caso contrário, `false`.</xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>  
  
 Você também pode garantir que os projetos e soluções sejam carregadas (não importa quais são as prioridades de carga de projeto) chamando um dos métodos a seguir:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: chamar esse método força os projetos em uma solução para carregar antes que o método retorna.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: chamar esse método força os projetos `guidProject` carregar antes que o método retorna.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: chamar esse método força o projeto no `guidProjectID` carregar antes que o método retorna.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>  
  
> [!NOTE]
>  . Por padrão somente os projetos que têm a demanda de carga e prioridades de carregamento em segundo plano são carregadas, mas se o <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS>sinalizador é passado para o método, todos os projetos serão carregados, exceto aqueles que são marcados para carregar explicitamente.</xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS>
