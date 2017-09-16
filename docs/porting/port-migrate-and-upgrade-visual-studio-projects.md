---
title: Portar, migrar e atualizar projetos do Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 7/24/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 21a413a3e2d17d77fd83d5109587a96f323a0511
ms.openlocfilehash: d637dc2b0349bfe1efbcf55417d4f4bf5817b303
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---

# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Portar, migrar e atualizar projetos do Visual Studio

Geralmente, cada nova versão do Visual Studio dá suporte à maioria dos tipos anteriores de projetos, arquivos e outros ativos. É possível trabalhar com eles [como você sempre trabalhou](../ide/solutions-and-projects-in-visual-studio.md) e, desde que não dependa de recursos mais novos, o Visual Studio preservará a compatibilidade com versões anteriores, como o Visual Studio 2015, Visual Studio 2013 e Visual Studio 2012. (Consulte as [Notas de versão](https://www.visualstudio.com/vs/release-notes/) para saber quais recursos são específicos a quais versões.)

No entanto, o suporte para alguns tipos é alterado ao longo do tempo. Uma versão mais nova do Visual Studio pode não dar mais suporte a determinados tipos ou exigir que eles sejam migrados e atualizados, de modo que não são mais compatíveis com versões anteriores. Para obter o status atual de problemas de migração, consulte o [site Developer Community (Comunidade do Desenvolvedor) do Visual Studio](https://developercommunity.visualstudio.com).

> [!Important]
> Este tópico fornece detalhes apenas para tipos de projeto no Visual Studio de 2017 que envolvem a migração. Ele não inclui os tipos de projeto com suporte que não têm nenhum problema de migração, essa lista é encontrada em [Direcionamento e compatibilidade da plataforma](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs). Observe também que alguns tipos de projeto não têm mais suporte nenhum no Visual Studio 2017 e, portanto, não podem ser migrados.

> [!Important]
> É necessário adicionar as cargas de trabalho apropriadas no instalador do Visual Studio para abrir determinados tipos de projeto. Se você não tiver a carga de trabalho instalada, o Visual Studio relatará um tipo de projeto incompatível ou desconhecido. Nesse caso, verifique as opções de instalação e tente novamente. Novamente, consulte o tópico [Direcionamento e compatibilidade da plataforma](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs) para obter detalhes sobre o suporte ao projeto no Visual Studio 2017.

## <a name="projects"></a>Projetos

A lista a seguir descreve o suporte do Visual Studio 2017 a projetos que foram criados em versões anteriores.

Se você não vir um projeto ou um tipo de arquivo que deveria estar listado aqui, consulte a [versão do Visual Studio 2015 deste tópico](https://msdn.microsoft.com/library/hh266747.aspx) e faça uma observação nos comentários abaixo.

| Tipo de projeto | Suporte |
| --- | --- |
| Projetos do .NET Core (.xproj) | Projetos criados com o Visual Studio 2015 usavam as ferramentas de visualização que incluem um arquivo de projeto .xproj. Ao abrir um arquivo .xproj com o Visual Studio 2017, você deverá migrar o arquivo para o formato .csproj (será feito um backup do arquivo .xproj). Não há suporte para esse formato .csproj em projetos do .NET Core no VS2015 e anterior.  Não há suporte para o formato .xproj no Visual Studio 2017 além da migração para o .csproj. Para obter mais informações, consulte [Migrando projetos do .NET Core para o formato .csproj](https://docs.microsoft.com/dotnet/core/migration/#visual-studio-2017).|
| Aplicativo Web ASP.NET e Aplicativo Web ASP.NET Core com o Application Insights habilitado | Para cada usuário do Visual Studio, as informações de recurso são armazenadas no Registro por instância de usuário. Isso é usado quando o usuário não tem um projeto aberto e deseja pesquisar dados do Azure Application Insights. O Visual Studio 2015 usa um local de Registro diferente do Visual Studio 2017 e não entra em conflito com ele.<br/><br/>Quando um usuário cria um aplicativo Web ASP.NET ou um Aplicativo Web ASP.NET Core, os recursos são armazenados no arquivo .suo. O usuário pode abrir o projeto no Visual Studio 2015 ou 2017 e as informações de recurso serão usadas para ambos, desde que o Visual Studio dê suporte a projetos e soluções usadas em ambas as versões. Os usuários precisarão se autenticarem uma vez em cada produto. Por exemplo, se um projeto for criado com o Visual Studio 2015 e aberto no Visual Studio 2017, o usuário precisará se autenticar no Visual Studio 2017. |
| Formulário da Web ou Windows Form em C#/Visual Basic | É possível abrir o projeto no Visual Studio 2017 e no Visual Studio 2015. |
| Projetos de teste de unidade de banco de dados (.csproj, .vbproj)    | Projetos de teste de Unidade de Dados antigos serão carregados no Visual Studio 2017, mas usarão a versão do GAC de dependências. Para atualizar o projeto de teste de unidade para usar as últimas dependências, clique com o botão direito do mouse no projeto no Gerenciador de Soluções e selecione **Converter para Projeto de Teste de Unidade do SQL Server...**. |
| F# | O Visual Studio 2017 pode abrir projetos criados no Visual Studio 2013 e 2015. No entanto, para habilitar os recursos do Visual Studio 2017 nesses projetos, abra as propriedades do projeto e altere o destino fsharp.core para F# 4.1. Observe também que a opção **Suporte à linguagem F#** no instalador do Visual Studio não é selecionada por padrão com as cargas de trabalho do .NET. Você deve incluí-la selecionando essa opção para a carga de trabalho ou selecionando-a na guia **Componentes individuais** em **Atividades de desenvolvimento**. |
| InstallShield<br/>Instalação do MSI | Projetos do instalador criados no Visual Studio 2010 podem ser abertos em versões posteriores com a ajuda da [extensão Projetos do Instalador do Visual Studio](https://marketplace.visualstudio.com/items?itemName=UnniRavindranathan-MSFT.MicrosoftVisualStudio2013InstallerProjects). Consulte também o [WiX Toolset Visual Studio 2017 Extension](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension) (Extensão do Conjunto de Ferramentas WiX do Visual Studio 2017). O InstallShield Limited Edition não está mais incluído com o Visual Studio. Consulte a [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) sobre a disponibilidade para o Visual Studio 2017. |
| LightSwitch | Não há mais suporte para o LightSwitch no Visual Studio 2017. Projetos criados com o Visual Studio 2012 e anterior abertos no Visual Studio 2013 ou Visual Studio 2015 serão atualizados e podem ser abertos apenas no Visual Studio 2013 ou no Visual Studio 2015 em diante. |
| Ferramentas do Microsoft Azure para Visual Studio | Para abrir esses tipos de projetos, primeiro instale o [SDK do Azure para .NET](http://azure.microsoft.com/downloads/) e, em seguida, abra o projeto. Se necessário, o projeto será atualizado. |
| Estrutura Modelo-Exibição-Controlador (ASP.NET MVC) | Suporte para versões do MVC e para o Visual Studio:<ul><li>O Visual Studio 2010 SP1 dá suporte ao MVC 2 e MVC 3; o suporte MVC 4 é adicionado por meio do [download do ASP.NET 4 MVC 4 para Visual Studio 2010 SP1](https://www.microsoft.com/download/details.aspx?id=30683)</li><li>O Visual Studio 2012 dá suporte apenas ao MVC 3 e ao MVC 4</li><li>O Visual Studio 2013 dá suporte apenas ao MVC 4 e ao MVC 5</li><li>O Visual Studio 2017 e o Visual Studio 2015 dão suporte ao MVC 4 (é possível abrir projetos existentes, mas não criar novos) e ao MVC 5</li></ul><br/><br/>Atualizando versões do MVC:<ul><li>Para obter informações sobre como atualizar automaticamente do MVC 2 para o MVC 3, consulte [Atualizador do aplicativo ASP.NET MVC 3](http://go.microsoft.com/fwlink/?LinkID=238178).</li><li>Para obter informações sobre como atualizar manualmente do MVC 2 para o MVC 3, consulte [Atualizando um projeto ASP.NET MVC 2 para atualização de ferramentas do ASP.NET MVC 3](http://go.microsoft.com/fwlink/?linkid=238178).</li><li>Para obter informações sobre como atualizar manualmente do MVC 3 para o MVC 4, consulte [Atualizando um projeto ASP.NET MVC 3 para o ASP.NET MVC 4](http://www.asp.net/whitepapers/mvc4-release-notes). Se o projeto se destinar ao .NET Framework 3.5 SP1, você deverá redirecioná-lo para usar o .NET Framework 4.</li><li>Para obter informações sobre como atualizar manualmente do MVC 4 para o MVC 5, consulte [Como atualizar um projeto do ASP.NET MVC 4 e API Web para o ASP.NET MVC 5 e API Web 2](https://www.asp.net/mvc/overview/releases/how-to-upgrade-an-aspnet-mvc-4-and-web-api-project-to-aspnet-mvc-5-and-web-api-2)</li></ul> |
| Modelagem | Se você permitir que o Visual Studio atualize o projeto automaticamente, será possível abri-lo no Visual Studio 2015, Visual Studio 2013 ou Visual Studio 2012.<br/><br/>O formato do projeto de modelagem não foi alterado entre o Visual Studio 2015 e o Visual Studio 2017 e pode ser aberto e modificado em qualquer versão. No entanto, há diferenças de comportamento no Visual Studio 2017:<ul><li>Os projetos de modelagem agora são chamados de projetos de “Validação de dependência” nos menus e modelos.</li><li>Não há mais suporte para diagramas UML no Visual Studio 2017. Arquivos UML são listados no Gerenciador de Soluções como antes, mas serão abertos como arquivos XML. Use o Visual Studio 2015 para exibir, criar ou editar diagramas UML.</li><li>No Visual Studio de 2017, a validação de dependências de arquitetura não é mais executada quando o projeto de modelagem é criado. Em vez disso, a validação é executada durante a criação de cada projeto de código. Essa alteração não afeta o projeto de modelagem, mas exige alterações nos projetos de código que estão sendo validados. O Visual Studio 2017 pode fazer as alterações necessárias nos projetos de código automaticamente ([mais informações](http://go.microsoft.com/fwlink/?LinkId=827800)).</li></ul> |
| Instalação MSI (.vdproj) | Consulte Projetos do InstallShield acima. | 
| Office 2007 VSTO | Exige uma atualização unidirecional para o Visual Studio 2017. |
| Office 2010 VSTO | Se o projeto for destinado ao .NET Framework 4, será possível abri-lo no Visual Studio 2010 SP1 e posterior. Todos outros projetos exigem uma atualização unidirecional. |
| SharePoint 2010 | Quando um projeto de solução do SharePoint for aberto com o Visual Studio 2017, ele será atualizado para o SharePoint 2013 ou SharePoint 2016. A carga de trabalho "Desenvolvimento de área de trabalho do .NET" deve ser instalada no Visual Studio 2017 para a atualização.<br/><br/>Para obter mais informações sobre como atualizar projetos do SharePoint, consulte [Atualizar para o SharePoint 2013](https://technet.microsoft.com/library/cc303420.aspx), [Atualizar fluxo de trabalho no SharePoint Server 2013](https://technet.microsoft.com/library/dn133867.aspx) e [Criar o farm do SharePoint Server 2016 para uma atualização de anexação de banco de dados](https://technet.microsoft.com/library/cc263026(v=office.16).aspx). |
| SharePoint 2016 | Projetos de Suplemento do SharePoint criados no Office Developer Tools Visualização 2 não podem ser abertos no Visual Studio 2017. Para resolver isso, você precisará atualizar o `MinimumVisualStudioVersion` para 12.0 e `MinimumOfficeToolsVersion` para 12.2 no arquivo `.csproj` ou `.vbproj`. |
| Silverlight | Não há suporte para projetos do Silverlight no Visual Studio 2017. Para manter os aplicativos do Silverlight, continue a usar o Visual Studio 2015. |
| SQL Server Reporting Services e SQL Server Analysis Services (SSRS, SSDT, SSAS, MSAS) | O suporte para esses tipos de projeto é fornecido por meio de duas extensões na Galeria do Visual Studio: [Projetos de Modelagem do Microsoft Analysis Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects) e [Projetos do Microsoft Reporting Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio). Suporte do SSDT também está incluso com a carga de trabalho de Processamento e Armazenamento de Dados no Visual Studio de 2017. |
| SQL Server Integration Services (SSIS) | Ainda não há suporte disponível para o Visual Studio 2017. Ele será anunciado no [blog do SQL Server Integration Services](https://blogs.msdn.microsoft.com/ssis/). A recomendação atual para SSIS é continuar usando o Visual Studio 2015. |
| Visual C++ | É possível usar o Visual Studio 2017 para abrir soluções e projetos que foram criados no Visual Studio 2015 no estado em que se encontram, mas os projetos criados em versões anteriores do Visual Studio podem exigir a atualização do projeto ou a redefinição do destino para um conjunto de ferramentas mais recente para build com o Visual Studio 2017. Para obter mais informações, consulte [Guia de portabilidade e de atualização do Visual C++](https://docs.microsoft.com/cpp/porting/visual-cpp-porting-and-upgrading-guide). |
| Extensibilidade/VSIX do Visual Studio | Projetos com MinimumVersion 14.0 ou inferior serão atualizados para declarar a MinimumVersion 15.0, que impede que o projeto seja aberto em versões anteriores do Visual Studio. Para permitir que um projeto seja aberto em versões anteriores, defina MinimumVersion como `$(VisualStudioVersion)`. Consulte também [Como migrar projetos de extensibilidade para o Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md). |
| Visual Studio Lab Management | É possível usar o Microsoft Test Manager ou o Visual Studio 2010 SP1 e posterior para abrir ambientes criados em qualquer uma dessas versões. No entanto, para o Visual Studio 2010 SP1, a versão do Microsoft Test Manager deve corresponder à versão do Team Foundation Server para que você possa criar ambientes. |
| Ferramentas do Visual Studio para Apache Cordova |Esse projeto pode ser aberto no Visual Studio 2017, mas não é compatível com versões anteriores. Ao abrir um projeto do Visual Studio 2015, você deverá permitir modificações ao projeto. Isso atualiza o projeto para usar conjuntos de ferramentas em vez de um arquivo `taco.json` para gerenciar o controle de versão da biblioteca do Cordova, suas plataformas e seus plug-ins, bem como suas dependências de nó/npm. Consulte o [guia de migração](https://docs.microsoft.com/visualstudio/cross-platform/tools-for-cordova/first-steps/migrate-from-visual-studio-2015) para obter mais informações. |
| Windows Communication Foundation, Windows Workflow Foundation | É possível abrir esse projeto no Visual Studio 2017, Visual Studio 2015, Visual Studio 2013 e Visual Studio 2012 |
| Windows Presentation Foundation | É possível abrir esse projeto no Visual Studio 2013, Visual Studio 2012 e Visual Studio 2010 SP1. |
| Aplicativos da Windows Store/aplicativos Windows Phone | Não há suporte para projetos da Windows Store 8.1 e 8.0 e do Windows Phone 8.1 e 8.0 no Visual Studio 2017. Para manter esses aplicativos, continue a usar o Visual Studio 2015. Para manter os projetos do Windows Phone 7. x, use o Visual Studio 2012. |

