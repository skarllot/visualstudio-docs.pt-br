---
title: "Atualizando projetos personalizados | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Atualizando sistemas de projeto"
  - "projetos [Visual Studio SDK], atualizando"
  - "projeto de atualização do sistema [Visual Studio]"
ms.assetid: 262ada44-7689-44d8-bacb-9c6d33834d4e
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# Atualizando projetos personalizados
Se você alterar as informações mantidas no arquivo de projeto entre diferentes versões do Visual Studio do seu produto, você precisará dar suporte ao atualizar o arquivo de projeto do ambiente antigo para a nova versão. Para oferecer suporte a atualização que permite que você participe de **Assistente de conversão do Visual Studio**, implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface. Essa interface contém o único mecanismo disponível para a atualização da cópia. A atualização do projeto acontece como parte da solução é aberta. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface é implementada pela fábrica de projeto, ou deve ser pelo menos pode ser obtida da fábrica de projeto.  
  
 O mecanismo antigo que usa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interface ainda é suportada, mas conceitualmente atualiza o sistema de projeto como parte do projeto aberto. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interface, portanto, é chamada pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente mesmo se o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface é chamada ou implementada. Essa abordagem permite que você use <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> para implementar a cópia e apenas partes da atualização de projeto e delegue o resto do trabalho a ser feito no local \(possivelmente no novo local\), o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interface.  
  
 Para uma implementação de exemplo de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, consulte [Exemplos VSSDK](../misc/vssdk-samples.md).  
  
 Os seguintes cenários ocorrem com as atualizações do projeto:  
  
-   Se o arquivo for de um formato mais recente que o projeto pode suportar, ela deve retornar um erro informando isso. Isso pressupõe que a versão mais antiga do produto — por exemplo, Visual Studio .NET 2003 — inclui código para verificar a versão.  
  
-   Se o <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> sinalizador é especificado no <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método, a atualização está prestes a ser implementado como uma atualização in\-loco antes da abertura do projeto.  
  
-   Se o <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> sinalizador é especificado no <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método, a atualização é implementado como uma atualização de cópia.  
  
-   Se o <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> sinalizador é especificado no <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> chamar, então o usuário foi solicitado pelo ambiente de atualizar o arquivo de projeto como uma atualização in\-loco, depois que o projeto é aberto. Por exemplo, o ambiente solicita ao usuário a atualização quando o usuário abre uma versão mais antiga da solução.  
  
-   Se o <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> sinalizador não for especificado no <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> chama, em seguida, você deverá solicitar ao usuário para atualizar o arquivo de projeto.  
  
     Esta é uma mensagem de aviso de atualização exemplo:  
  
     "O projeto '%1' foi criado com uma versão anterior do Visual Studio. Se você abri\-lo com esta versão do Visual Studio, você não poderá abri\-lo com versões anteriores do Visual Studio. Deseja continuar e abrir este projeto?"  
  
### Para implementar IVsProjectUpgradeViaFactory  
  
1.  Implementar o método do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface, especificamente o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método em sua implementação de fábrica de projeto, ou fazer com que as implementações podem ser chamados de sua implementação de fábrica do projeto.  
  
2.  Se você quiser fazer uma atualização in\-loco como parte da solução de abertura, forneça o sinalizador <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> como o `VSPUVF_FLAGS` parâmetro em seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementação.  
  
3.  Se você quiser fazer uma atualização in\-loco como parte da solução de abertura, forneça o sinalizador <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> como o `VSPUVF_FLAGS` parâmetro em seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementação.  
  
4.  Para ambos os as etapas 2 e 3, o arquivo real atualizar etapas usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, podem ser implementados conforme descrito na "Implementando `IVsProjectUpgade`" seção abaixo, ou você pode delegar a atualização real do arquivo para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
5.  Use os métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> para lançar atualização mensagens relacionadas para o usuário usando o Assistente de migração do Visual Studio.  
  
6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> interface é usada para implementar qualquer tipo de atualização de arquivo que precisa acontecer como parte da atualização do projeto. Essa interface não é chamada de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, mas é fornecido como um mecanismo para atualizar os arquivos que fazem parte do sistema do projeto, mas o sistema de projeto principal pode não ser diretamente compatível. Por exemplo, essa situação pode ocorrer se o compilador relacionadas a arquivos e propriedades não são tratadas pela equipe de desenvolvimento mesmo que cuida do resto do sistema de projeto.  
  
## Implementação de IVsProjectUpgrade  
 Se o sistema de projeto implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> apenas, ele não pode participar de **Assistente de conversão do Visual Studio**. No entanto, mesmo se você implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface, você ainda pode delegar a atualização de arquivo para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementação.  
  
#### Para implementar IVsProjectUpgrade  
  
1.  Quando um usuário tenta abrir um projeto, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> método é chamado pelo ambiente depois que o projeto é aberto e antes de qualquer outro usuário ação pode ser executada no projeto. Se o usuário já tinha sido solicitado a atualizar a solução, então o <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> sinalizador é passado a `grfUpgradeFlags` parâmetro. Se o usuário abre um projeto diretamente, tal como usando o **Adicionar projeto existente** comando, então o <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> sinalizador não for passado e o projeto precisa solicitar ao usuário para atualizar.  
  
2.  Em resposta ao <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> chamada, o projeto deve avaliar se o arquivo de projeto é atualizado. Se o projeto não precisa atualizar o projeto para uma nova versão, pode simplesmente retornar o <xref:Microsoft.VisualStudio.VSConstants.S_OK> sinalizador.  
  
3.  Se o projeto precisa atualizar o tipo de projeto para uma nova versão, ele deve determinar se o arquivo de projeto pode ser modificado, chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> método e passando um valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para o `rgfQueryEdit` parâmetro. O projeto precisa fazer o seguinte:  
  
    -   Se o `VSQueryEditResult` valor retornado no `pfEditCanceled` parâmetro é <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>, em seguida, a atualização pode continuar porque o arquivo de projeto pode ser gravado.  
  
    -   Se o `VSQueryEditResult` valor retornado no `pfEditCanceled` parâmetro é <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> e o `VSQueryEditResult` valor tem o <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit definido, em seguida, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> deve retornar a falha, pois os usuários devem resolver as permissões execute próprios. O projeto deve, em seguida, faça o seguinte:  
  
         Relatar o erro para o usuário ao chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>. e retornar o <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> código de erro para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
    -   Se o `VSQueryEditResult` valor é <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> e o `VSQueryEditResultFlags` valor tem o <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit definido, em seguida, o arquivo de projeto deve fazer check\-out chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> \(<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...\).  
  
4.  Se o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> chamada no arquivo de projeto faz com que o arquivo de check\-out e a versão mais recente a ser recuperada, em seguida, o projeto é descarregado e recarregado. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> método for chamado novamente depois que a outra instância do projeto é criada. Nesta segunda chamada, o arquivo de projeto pode ser gravado em disco; Recomenda\-se que o projeto salvar uma cópia do arquivo de projeto no formato anterior com um. Extensão antigo, faça suas alterações de atualização necessárias e salve o arquivo de projeto no novo formato. Novamente, se qualquer parte do processo de atualização falhar, o método deve indicar falha retornando <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>. Isso faz com que o projeto seja descarregado no Gerenciador de soluções.  
  
     É importante compreender o processo completo que ocorre no ambiente para o caso em que a chamada para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> método \(especificando um valor de ReportOnly\) retorna o <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> e o <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> sinalizadores.  
  
5.  O usuário tenta abrir o arquivo de projeto.  
  
6.  O ambiente chama seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementação.  
  
7.  Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> retorna `true`, em seguida, chama o ambiente seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementação.  
  
8.  O ambiente chama seu <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementação para abri\-lo e inicializar o objeto de projeto, por exemplo, Project1.  
  
9. O ambiente chama seu `IVsProjectUpgrade::UpgradeProject` implementação para determinar se o arquivo de projeto deve ser atualizado.  
  
10. Chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e passar um valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para o `rgfQueryEdit` parâmetro.  
  
11. Retorna o ambiente <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> para `VSQueryEditResult` e o <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit é definido em `VSQueryEditResultFlags`.  
  
12. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementação chama `IVsQueryEditQuerySave::QueryEditFiles` \(<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>\).  
  
 Essa chamada pode causar uma nova cópia do arquivo do projeto para fazer check\-out e recuperar a versão mais recente, bem como a necessidade de recarregar o arquivo de projeto. Neste ponto, uma das duas coisas acontecem:  
  
-   Se você tratar recarregar seu próprio projeto, em seguida, o ambiente chama seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementação \(VSITEMID\_ROOT\). Quando você recebe essa chamada, recarregue a primeira instância do seu projeto \(Project1\) e continuar a atualizar o arquivo de projeto. O ambiente sabe que você manipule sua próprias recarregar projeto se você retornar `true` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> \(<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>\).  
  
-   Se você não tratar recarregar seu próprio projeto, então você retornar `false` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> \(<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>\). Nesse caso, antes de <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>\(<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,\) retorna, o ambiente cria outro novo, a instância do seu projeto, por exemplo, Projeto2, da seguinte maneira:  
  
    1.  O ambiente chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> em seu primeiro objeto de projeto, Projeto1, colocando esse objeto no estado inativo.  
  
    2.  O ambiente chama seu `IVsProjectFactory::CreateProject` implementação para criar uma segunda instância do seu projeto, Projeto2.  
  
    3.  O ambiente chama seu `IPersistFileFormat::Load` implementação para abri\-lo e inicializar o segundo objeto de projeto, Projeto2.  
  
    4.  O ambiente chama `IVsProjectUpgrade::UpgradeProject` pela segunda vez determinar se o objeto de projeto deve ser atualizado. No entanto, essa chamada é feita em um novo, em segundo lugar, a instância do projeto, Projeto2. Esse é o projeto é aberto na solução.  
  
        > [!NOTE]
        >  Na instância que seu primeiro projeto, Projeto1, é colocado no estado inativo, você deverá retornar <xref:Microsoft.VisualStudio.VSConstants.S_OK> da primeira chamada para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> implementação. Consulte [Basic Project](http://msdn.microsoft.com/pt-br/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) para uma implementação de `IVsProjectUpgrade::UpgradeProject`.  
  
    5.  Chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e passar um valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para o `rgfQueryEdit` parâmetro.  
  
    6.  Retorna o ambiente <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> e a atualização pode continuar porque o arquivo de projeto pode ser gravado.  
  
 Se você não atualizar, retornar <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> de `IVsProjectUpgrade::UpgradeProject`. Se nenhuma atualização é necessária ou se você optar por não atualizar, trate o `IVsProjectUpgrade::UpgradeProject` chamada como no\-op. Se você retornar <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>, um nó de espaço reservado é adicionado à solução para seu projeto.  
  
## Consulte também  
 [Visual Studio Conversion Wizard](http://msdn.microsoft.com/pt-br/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Atualizando itens de projeto](../misc/upgrading-project-items.md)   
 [Projetos](../extensibility/internals/projects.md)