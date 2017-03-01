---
title: "Solução (. Arquivos sln) | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d9b2d052f86cf76dcd9e2f97f2ee03eaf07dcf5b
ms.lasthandoff: 02/22/2017

---
# <a name="solution-sln-file"></a>Solução (. Arquivos sln)
Uma solução é uma estrutura para organizar projetos no Visual Studio. A solução mantém as informações de estado para projetos em. sln (baseado em texto, compartilhado) e arquivos. suo (opções de solução de binário, especificada pelo usuário). Para obter mais informações sobre arquivos. suo, consulte [opções de usuário de solução (. Arquivos suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 Se o VSPackage é carregado como resultado sendo referenciado no arquivo. sln, o ambiente chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>para ler o arquivo. sln.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>  
  
 O arquivo. sln contém informações baseadas em texto que o ambiente usa para localizar e carregar os parâmetros de nome-valor para o projeto VSPackages faz referência a ele e os dados persistentes. Quando um usuário abre uma solução, o ambiente percorre o `preSolution`, `Project`, e `postSolution` as informações no arquivo. sln para carregar a solução, projetos na solução e todas as informações persistentes anexada à solução.  
  
 Arquivo de cada projeto contém informações adicionais de leitura pelo ambiente de preencher a hierarquia com itens de projeto. A persistência de dados da hierarquia é controlada pelo projeto; os dados não é normalmente armazenados no arquivo. sln, embora você possa escrever intencionalmente informações do projeto para o arquivo se você optar por fazer isso. Para obter mais informações relacionadas a persistência, consulte [projeto persistência](../../extensibility/internals/project-persistence.md) e [abrindo e salvando itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="solution-file-contents"></a>Conteúdo do arquivo de solução  
 O arquivo consiste em várias seções conforme ilustrado no código a seguir.  
  
```  
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
EndProject  
Global  
  GlobalSection(SolutionNotes) = postSolution  
  EndGlobalSection  
  GlobalSection(SolutionConfiguration) = preSolution  
       ConfigName.0 = Debug  
       ConfigName.1 = Release  
  EndGlobalSection  
  GlobalSection(ProjectDependencies) = postSolution  
  EndGlobalSection  
  GlobalSection(ProjectConfiguration) = postSolution  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86  
  EndGlobalSection  
  GlobalSection(ExtensibilityGlobals) = postSolution  
  EndGlobalSection  
  GlobalSection(ExtensibilityAddIns) = postSolution  
  EndGlobalSection  
EndGlobal  
```  
  
 Para carregar uma solução, o ambiente executa a seguinte sequência de tarefas.  
  
1.  O ambiente lê a seção Global do arquivo. sln e processa todas as seções marcadas `preSolution`. Nesse caso, há uma tal declaração:  
  
    ```  
    GlobalSection(SolutionConfiguration) = preSolution  
         ConfigName.0 = Debug  
         ConfigName.1 = Release  
    ```  
  
     Quando o ambiente lê o `GlobalSection('name')` marca, ele mapeia o nome a um VSPackage usando o registro. O nome da chave deve existir no Registro [HKLM\\<Application id="" registry=""></Application>\>\SolutionPersistence\AggregateGUIDs]. Valor de padrão de chaves é o GUID de pacote (REG_SZ) do VSPackage que escreveu as entradas.  
  
2.  O ambiente carrega o VSPackage, chamadas `QueryInterface` sobre o VSPackage para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>interface e chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>método com os dados na seção para o VSPackage pode armazenar os dados.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> O ambiente se repetir esse processo para cada `preSolution` seção.  
  
3.  O ambiente itera através dos blocos de persistência do projeto. Nesse caso, há um projeto.  
  
    ```  
    Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
    "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
    EndProject  
    ```  
  
     Essa instrução contém o GUID exclusivo do projeto e o GUID do tipo de projeto. Essas informações são usadas pelo ambiente de localizar o arquivo de projeto ou arquivos que pertencem à solução e o VSPackage necessários para cada projeto. O projeto GUID é passado para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>para carregar o VSPackage específico relacionado ao projeto, em seguida, o projeto é carregado pelo VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> Nesse caso, o VSPackage é carregado para este projeto é Visual Basic.  
  
     Cada projeto pode persistir um ID de instância exclusivo do projeto para que possam ser acessado conforme necessário por outros projetos na solução. Idealmente, se a solução e projetos estão sob controle do código fonte, o caminho para o projeto deve ser relativo ao caminho para a solução. Quando a solução é carregada pela primeira vez, os arquivos de projeto não podem ser no computador do usuário. Fazendo com que o arquivo de projeto armazenado no servidor relativo ao arquivo de solução, é relativamente simple para o arquivo de projeto a ser encontrado e copiado para o computador do usuário. Em seguida, ele copia e carrega o restante dos arquivos necessários para o projeto.  
  
4.  O ambiente com base nas informações contidas na seção projeto do arquivo. sln, carrega cada arquivo de projeto. O projeto em si, em seguida, é responsável por preencher a hierarquia de projeto e carregando quaisquer projetos aninhados.  
  
5.  Após o processamento de todas as seções do arquivo. sln, a solução é exibida no Gerenciador de soluções e está pronta para modificação pelo usuário.  
  
 Se qualquer VSPackage que implementa um projeto na solução falhar ao carregar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A>método é chamado e todos os outros projetos na solução recebe uma oportunidade para ignorar as alterações que ele tenha feito durante o carregamento.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> Se ocorrerem erros de análise, tanta informação quanto possível é preservada com os arquivos da solução e o ambiente exibe uma caixa de diálogo avisando o usuário que a solução está corrompida.  
  
 Quando a solução é salvo ou fechada, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A>método é chamado e passado para a hierarquia para ver se as alterações foram feitas para a solução que precisam ser inseridos no arquivo. sln.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> Um valor nulo, passado para `QuerySaveSolutionProps` na <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>, indica que as informações são sendo mantidas para a solução.</xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS> Se o valor não for nulo, as informações persistentes serão para um projeto específico, determinado pelo ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
 Se não houver informações a serem salvas, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>interface é chamada com um ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> O <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>método é chamado pelo ambiente de recuperar os pares nome-valor de `IPropertyBag` de interface e gravar as informações para o arquivo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>  
  
 `SaveSolutionProps`e `WriteSolutionProps` objetos são chamados recursivamente pelo ambiente de recuperar as informações sejam salvos do `IPropertyBag` interface até que todas as alterações foram inseridas no arquivo. sln. Dessa forma, você pode assegurar que as informações serão mantidas com a solução e o tempo disponível do próximo que a solução for aberta.  
  
 Cada VSPackage carregado é enumerado para ver se ele tem algo para salvar o arquivo. sln. Ele é apenas em tempo de carregamento que as chaves do registro são consultadas. O ambiente conhece todos os pacotes carregados porque eles estão na memória no momento em que a solução é salvo.  
  
 Somente o arquivo. sln contém entradas na `preSolution` e `postSolution` seções. Não existem seções semelhantes no arquivo. suo desde que a solução precisa dessas informações para carregar corretamente. O arquivo. suo contém opções específicas do usuário, como anotações particulares, que não devem ser compartilhados ou colocado sob controle do código fonte.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Opções de usuário de solução (. Arquivos suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Soluções](../../extensibility/internals/solutions.md)
