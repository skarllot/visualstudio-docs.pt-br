---
title: "Área de teste 1: Adicionar para abrir do controle de origem | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
caps.latest.revision: 20
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
ms.openlocfilehash: 76203dfda5b689cc63cd3fef6e3748e49fc33976
ms.lasthandoff: 02/22/2017

---
# <a name="test-area-1-add-toopen-from-source-control"></a>Área de teste 1: Adicionar / Abrir do controle de origem
Esse controle de origem plug-in de teste área abrange colocando soluções ou projetos sob controle de origem e recuperá-los do controle de origem.  
  
## <a name="command-menu-access"></a>Acesso ao Menu comando  
 O seguinte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] caminhos de menu do ambiente de desenvolvimento integrado são usados nos casos de teste:  
  
-   Para [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], abrir do controle de origem: **arquivo**, **abrir**, **projeto**/**solução**; procure no [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] local.  
  
-   Para outras fonte plug-ins de controle, abra do controle de origem: **arquivo**, **controle de origem**, **abrir do controle de origem**.  
  
-   Adicionar ao controle de origem: **arquivo**, **controle de origem**, **adicionar solução ao arquivo de controle de origem**, **controle de origem**, **adicionar projetos selecionados ao controle de origem**.  
  
-   Menu de atalho (projeto/solução), **adicionar solução ao controle de origem**.  
  
-   Adicionar do controle de origem: **arquivo**, **controle de origem**, **Adicionar projeto do controle de origem**.  
  
-   Para [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], adicionar controle do código-fonte também está disponível no **arquivo**, **adicionar**, **projeto existente**; procure no [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] local.  
  
    > [!NOTE]
    >  Um caminho de um arquivo local ou um local IIS (servidor web) pode ser usado nesse teste.  
  
## <a name="expected-behavior"></a>Comportamento esperado  
  
-   Para cada tipo de projeto com suporte, um usuário deve ser capaz de "Adicionar ao" e "Abrir do" controle de origem.  
  
-   Quando um projeto é adicionado ao controle de origem, um correspondente \< *ProjectName*> os arquivos (arquivo de dica de projeto) é criado. Ele contém informações de conexão e de lista de arquivo de exclusão. Não exclua este arquivo porque ele contém informações específicas do projeto.  
  
-   Quando uma solução é adicionada ao controle de origem, um correspondente \< *SolutionName*>.vssscc (triple S) de arquivo é criado. O arquivo de texto contém informações de conexão e uma lista de arquivos de exclusão, semelhante ao arquivo de dica de projeto. Esse arquivo é temporário e existe somente no banco de dados de controle de origem.  
  
-   Quando uma solução for aberta no controle de origem, uma \< *SolutionName*> arquivo .vsscc (double S) que existe somente no banco de dados de controle de origem é criado localmente em um arquivo temporário. Esse arquivo contém o caminho da pasta de conexão de solução para o arquivo de solução. Esse arquivo é temporário e a cópia local é excluída quando a operação de "Open from Source Control" foi concluída.  
  
-   Depois que um projeto é adicionado ao controle de origem, você pode executar as ações de controle de origem nele (Check-out, Get e assim por diante).  
  
## <a name="test-cases"></a>Casos de teste  
 A seguir estão os casos de teste específicos para adicionar / abrir da área de teste de controle de origem.  
  
### <a name="case-1a-add-solution-to-source-control"></a>Caso 1a: Adicionar solução ao controle de origem  
 Esse caso de teste se concentra na adição de soluções ao controle de origem.  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Adicionar solução contendo um projeto de cliente ao controle de origem|1.  Crie um projeto de cliente.<br />2.  Adicione a solução ao controle de origem (**arquivo**, **controle de origem**, **adicionar solução ao controle de origem**).|Projeto/solução foi adicionado ao controle de origem.|  
|Adicionar solução que contém um sistema de arquivos ou um projeto da Web do IIS local ao controle de origem|1.  Criar um sistema de arquivos ou um projeto da Web do IIS local (use o botão Procurar para apontar para o local do projeto; o caminho determina o tipo de projeto da Web é criado).<br />2.  Adicione a solução ao controle de origem (**arquivo**, **controle de origem**, **adicionar solução ao controle de origem**).|Projeto/solução foi adicionado ao controle de origem.|  
|Adicionar solução contendo um projeto de Site Web remoto ao controle de origem|1.  Crie um projeto de Web Site remoto.<br />2.  Adicione a solução ao controle de origem (**arquivo**, **controle de origem**, **adicionar solução ao controle de origem**).<br />3.  Clique em **Okey** na caixa de diálogo de aviso de acesso do FrontPage.|Solução foi adicionada ao controle de origem.<br /><br /> Projeto de Site remoto não está sob controle de origem. (Projetos de Site remoto devem ser controlados de seu próprio servidor IIS).|  
|Adicionar uma único projeto solução ao controle de origem usando **adicionar projetos selecionados ao controle de origem**.|1.  Crie uma solução de projeto único.<br />2.  Adicione apenas a solução ao controle de origem como uma seleção (**arquivo**, **controle de origem**, **adicionar projetos selecionados ao controle de origem**). Se essa etapa for bem-sucedida, continue para a próxima etapa.<br />3.  Adicionar o projeto ao controle de origem como seleção (**arquivo**, **controle de origem**, **adicionar projetos selecionados ao controle de origem**).<br />4.  Clique em **Sim** para adicionar o projeto no mesmo local.<br />5.  Clique em **Check-Out** na **Check-Out para edição** caixa de diálogo.|`Result from Step 2:`<br /><br /> O projeto e todos os arquivos dentro do projeto têm um check-out do indicador de controle de origem e uma dica de ferramenta exibe "não está sob controle de origem".<br /><br /> `Result from Step 5:`<br /><br /> Arquivo de projeto e solução estão na mesma pasta no controle de origem.|  
|Cancelar a adição de uma solução ao controle de origem|1.  Crie uma solução de projeto único.<br />2.  Tentativa de adicionar o projeto e solução ao controle de origem. Se essa etapa for bem-sucedida, continue para a próxima etapa.<br />3.  Cancele quando estiver no sistema de controle do código-fonte.|`Result from Step 2:`<br /><br /> A caixa de diálogo conjunto de projeto local source control aparece apenas uma vez.<br /><br /> `Result from Step 3:`<br /><br /> Projeto Adicionar cancelado, projeto/solução não está sob controle de origem e todos os adicione menus de controle de origem ainda estiver disponíveis.|  
  
### <a name="case-1b-open-solution-from-source-control"></a>Caso 1b. Abrir Solução do Controle do Código-Fonte  
 Esse caso de teste se concentra em abrir soluções do controle de origem.  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Abra uma solução que contém um projeto de cliente de controle de origem|1.  Crie um projeto de cliente.<br />2.  Adicione a solução ao controle de origem.<br />3.  Feche a solução.<br />4.  Abra a solução do controle de origem para um novo local.|Abrir projeto/solução do controle de origem.|  
|Abra uma solução que contém um local ou um projeto da Web do IIS do controle de origem|1.  Crie um projeto de Web do IIS ou local.<br />2.  Adicione a solução ao controle de origem.<br />3.  Feche a solução.<br />4.  Abra a solução do controle de origem para um novo local.|Abrir projeto/solução do controle de origem.|  
|Abra uma solução que contém um projeto de Web Site remoto do controle de origem|1.  Crie um projeto de Web Site remoto.<br />2.  Adicione a solução ao controle de origem. Se essa etapa for bem-sucedida, continue para a próxima etapa.<br />3.  Feche a solução.<br />4.  Abra a solução do controle de origem para um novo local.|`Result from Step 2:`<br /><br /> Web Site remoto não está sob controle de origem.<br /><br /> `Result from Step 4:`<br /><br /> Solução aberta do controle de origem.<br /><br /> Projeto de Site remoto for carregado, mas não está sob controle de origem.|  
  
### <a name="case-1c-add-solution-from-source-control"></a>Caso 1C: Adicionar solução do controle de origem  
 Esse caso de teste se concentra na adição de soluções de controle de origem.  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Adicionar à solução vazia — uma único projeto solução|1.  Crie uma solução de projeto único.<br />2.  Adicione a solução ao controle de origem.<br />3.  Feche a solução.<br />4.  Crie uma segunda solução vazia.<br />5.  Adicionar a solução anteriormente controlada do controle de origem (**arquivo**, **controle de origem**, **Adicionar projeto do controle de origem**).|O projeto adicionado aparece no **Solution Explorer** e check-in.|  
|Adicionar à solução com um único projeto — único projeto|1.  Crie uma solução com um único projeto.<br />2.  Adicione a solução ao controle de origem.<br />3.  Feche a solução.<br />4.  Crie uma segunda solução vazia.<br />5.  Adicionar a solução anteriormente controlada do controle de origem (**arquivo**, **controle de origem**, **Adicionar projeto do controle de origem**).|O projeto adicionado aparece no **Solution Explorer** e check-in.|  
|Adicionar à solução — solução adicionada ao controle de origem por seleção|1.  Crie uma solução com um projeto.<br />2.  Adicione apenas a solução ao controle de origem como seleção. Se essa etapa for bem-sucedida, continue para a próxima etapa.<br />3.  Feche a solução.<br />4.  Crie uma nova solução.<br />5.  Adicionar a solução anteriormente controlada do controle de origem (**arquivo**, **controle de origem**, **Adicionar projeto do controle de origem**).|`Result from Step 2:`<br /><br /> Projeto não está sob controle de origem.<br /><br /> `Result from Step 5:`<br /><br /> Se a primeira solução tinha itens de solução, eles não podem ser adicionados do controle de origem, para que eles não aparecem.<br /><br /> Projeto de solução primeiro aparece como indisponível.|  
  
## <a name="see-also"></a>Consulte também  
 [Guia de teste para Plug-ins de controle de origem](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
