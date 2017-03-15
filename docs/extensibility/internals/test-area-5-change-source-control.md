---
title: "Área de teste 5: Alterar controle do código-fonte | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
caps.latest.revision: 15
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
ms.openlocfilehash: 68a7b83e0316d6389059fd2196d75703e4e7c2b0
ms.lasthandoff: 02/22/2017

---
# <a name="test-area-5-change-source-control"></a>Área de teste 5: Alterar controle de origem
Essa área de plug-in de teste de controle de origem aborda a alteração do controle de origem por meio de **Change Source Control** comando.  
  
 **Alterar controle de origem** comando fornece quatro funções básicas para o usuário:  
  
-   **Vincule:**  
  
     Permite que um usuário estabelecer ou restabelecer um link de controle de origem entre um projeto/solução e o armazenamento de versão.  
  
-   **Desvincular:**  
  
     Remove uma projeto/solução de controle de origem em uma base por conexão.  
  
-   **Conectar/Desconecte:**  
  
 Alterna o estado conectado ou offline da solução controlada, que é abordado na área 3. Para obter mais informações, consulte [teste área 3: Check-Out / desfazer check-out](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).  
  
## <a name="command-menu-access"></a>Acesso ao Menu comando  
 O seguinte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] caminho de menu do ambiente de desenvolvimento integrado é usado nos casos de teste.  
  
 Alterar controle de origem:**arquivo**, **controle de origem**, **alterar controle de origem**.  
  
## <a name="test-cases"></a>Casos de teste  
 A seguir estão os casos de teste específicos para o **Change Source Control** comando área de teste.  
  
### <a name="case-5a-bind"></a>Caso 5a: associar  
 Ligação permite que o usuário adicione informações de controle de código fonte para os projetos selecionados e as soluções. Normalmente, o usuário é solicitado a identificar um projeto no controle de origem ao qual eles serão adicionados. O usuário não pode criar um novo projeto no controle de origem como parte dessa operação (contraste com adicionar ao controle de origem).  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Vincular a local vazio|1.  Criar um projeto.<br />2.  Adicione a solução ao controle de origem.<br />3.  Abra **Change Source Control** caixa de diálogo (**arquivo**, **controle de origem**, **alterar controle de origem**).<br />4.  Clique em **desassociar**.<br />5.  Aceite a caixa de diálogo de aviso se ela aparecer.<br />6.  Selecione todos os itens.<br />7.  Clique em **ligar**.<br />8.  Navegue até um local vazio em um repositório de controle de origem.<br />9. Clique em **Okey** para fechar o **Change Source Control** caixa de diálogo.<br />10. Clique em **continuar com essas associações** na caixa de diálogo de confirmação.<br />11. Clique em **Okey** na caixa de diálogo de aviso se ela aparecer.<br />12. Check-in de tudo. Se essa etapa for bem-sucedida, continue para a próxima etapa.<br />13. Abra a solução do controle de origem para um novo local.|`Result from Step 12:`<br /><br /> Solução e projeto são associados a e gravados para o novo destino no armazenamento de versão.<br /><br /> Arquivos de solução e projeto são check-in.<br /><br /> Hierarquia de projeto do armazenamento de versão corresponde a hierarquia de pastas do projeto no disco.<br /><br /> `Result from Step 13:`<br /><br /> Todos os itens de projeto são baixados.|  
|Vincular a local que está em sincronia com o cliente|1.  Criar um projeto.<br />2.  Adicione a solução ao controle de origem.<br />3.  Criar uma duplicata de solução e projeto no repositório de versão (compartilhar e ramificar se usando [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />4.  Abra **Change Source Control** caixa de diálogo (**arquivo**, **controle de origem**, **alterar controle de origem**).<br />5.  Desassocie todos.<br />6.  Clique em **Okey** para fechar **Change Source Control** caixa de diálogo.<br />7.  Reabra **Change Source Control** caixa de diálogo.<br />8.  Selecione tudo.<br />9. Clique em **ligar**.<br />10. Navegue até o local ramificado da solução e projeto (obtido na etapa 3)<br />11. Clique em **Okey** para fechar o **Change Source Control** caixa de diálogo.<br />12. Obtenha mais recente recursivamente para todos os itens.|Conteúdo do arquivo depois que o get é o mesmo que antes de get.|  
|Vincular a local que está fora de sincronia com o cliente|1.  Criar um projeto.<br />2.  Adicione a solução ao controle de origem.<br />3.  Criar uma duplicata de solução e projeto no repositório de versão (compartilhar e ramificar se usando [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />4.  Modificar arquivos no projeto ramificado no armazenamento de versão.<br />5.  Abra **Change Source Control** caixa de diálogo (**arquivo**, **controle de origem**, **alterar controle de origem**).<br />6.  Desassocie todos.<br />7.  Clique em **Okey** para fechar **Change Source Control** caixa de diálogo.<br />8.  Reabra **Change Source Control** caixa de diálogo.<br />9. Selecione tudo.<br />10. Clique em **ligar**.<br />11. Navegue até ramificado local para a solução e projeto.<br />12. Clique em **Okey** para fechar o **Change Source Control** caixa de diálogo.<br />13. Aceite a caixa de diálogo de aviso se ela aparecer.<br />14. Obtenha mais recente recursiva para todos os itens.|Os arquivos que foram modificados na etapa 4 também são modificados localmente.|  
|Solução de ligação que fosse nunca sob controle de origem|1.  Crie uma pasta vazia no controle de origem.<br />2.  Crie um projeto de cliente.<br />3.  Abra **Change Source Control** caixa de diálogo (**arquivo**, **controle de origem**, **alterar controle de origem**).<br />4.  Vincule a solução vazia local no controle de origem.<br />5.  Clique em **Okey** para fechar o **Change Source Control** caixa de diálogo.<br />6.  Clique em **continuar com essas associações** na caixa de diálogo de confirmação.<br />7.  Clique em **Okey** na caixa de diálogo de aviso se ela aparecer.|Solução é adicionada ao controle de origem.<br /><br /> Solução e projeto são check-out.|  
|Cancelar Bind|1.  Criar um projeto.<br />2.  Adicione a solução ao controle de origem.<br />3.  Abra a caixa de diálogo Alterar controle de origem.<br />4.  Desassocie todos.<br />5.  Clique em **Okey** para fechar a caixa de diálogo. Se essa etapa for bem-sucedida, continue para a próxima etapa.<br />6.  Reabra o **Change Source Control** caixa de diálogo.<br />7.  Vincule a local não relacionada.<br />8.  Clique em **Cancelar**.|`Result from Step 5:`<br /><br /> A solução não está sob controle de origem<br /><br /> `Result from Step 8:`<br /><br /> Solução é ainda não está em controle de origem.|  
  
### <a name="case-5b-unbind"></a>Caso 5b: desvincular  
 Desassocie remove informações de controle de código fonte de projetos e suas soluções. A solução e projetos afetados com base em uma combinação de seleção de usuário e como os itens foram adicionados ao controle de origem.  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Desassociar a solução que contém um sistema de arquivos ou o projeto da Web do IIS local e o projeto de um cliente|1.  Crie um sistema de arquivos ou um projeto da Web do IIS local.<br />2.  Adicione a solução ao controle de origem.<br />3.  Adicione um novo projeto de cliente para a solução.<br />4.  Aceite o Check-Out feito da solução se solicitado.<br />5.  Abra o **Change Source Control** caixa de diálogo.<br />6.  Clique em **desassociar**.<br />7.  Clique em **OK** para fechar a caixa de diálogo.<br />8.  Tentativa de check-out da solução, projeto, itens de solução, itens de projeto.|Solução e projetos não estão sob controle de origem.<br /><br /> Comandos de menu de controle do código-fonte não aparecem.|  
|Desvincular de cancelamento|1.  Criar um projeto.<br />2.  Adicione a solução ao controle de origem.<br />3.  Abra o **Change Source Control** caixa de diálogo.<br />4.  Clique em **desassociar todos**.<br />5.  Clique em **Cancelar**.|Solução estiver sob controle de origem.|  
  
### <a name="case-5c-rebind"></a>Caso 5c: Reassociar  
 Reassociar é simplesmente uma combinação de desvinculação e vincular — o processo de religação uma projeto/solução que era anteriormente no controle de origem e não associados.  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Associar novamente a solução e projetos sem fechar o **Change Source Control** caixa de diálogo|1.  Criar um projeto.<br />2.  Adicione a solução ao controle de origem.<br />3.  Abra o **Change Source Control** caixa de diálogo.<br />4.  Clique em **desassociar**.<br />5.  Selecione todas as linhas.<br />6.  Clique em **ligar**.<br />7.  Clique em **Okey** para fechar o **Change Source Control** caixa de diálogo.<br />8.  Se solicitado, aceite check-out.|Solução e projeto estão sob controle de origem.|  
|Reassociar projeto somente sem fechamento **Change Source Control** caixa de diálogo|1.  Criar um projeto.<br />2.  Adicionar somente o projeto ao controle de origem usando (arquivo-> Source Control-> adicionar projetos selecionados ao controle de origem.<br />3.  Abra a caixa de diálogo Alterar controle de origem.<br />4.  Desassocie apenas o projeto.<br />5.  Associe apenas o projeto.|Solução permanece não controlada.<br /><br /> Projeto permanece controlado.|  
|Reassociar solução somente sem fechamento **Change Source Control** caixa de diálogo|1.  Criar um projeto.<br />2.  Adicionar somente a solução ao controle de origem usando (**arquivo**, **controle de origem**, **adicionar projetos selecionados ao controle de origem**.<br />3.  Abra o **Change Source Control** caixa de diálogo.<br />4.  Desvincular apenas a solução (não feche **Change Source Control** caixa de diálogo.)<br />5.  Associe apenas a solução.<br />6.  Clique em **OK** para fechar a caixa de diálogo.<br />7.  Check-out de solução e itens de solução (se houver.)|Solução permanece controlada.<br /><br /> Projeto permanece não controlado.|  
|Reassociar projeto/solução somente quando estiver na mesma pasta|1.  Criar um projeto.<br />2.  Adicionar somente o projeto ao controle de origem usando (**arquivo**, **controle de origem**, **adicionar projetos selecionados ao controle de origem**.<br />3.  Feche a solução.<br />4.  Crie uma nova solução com pelo menos dois projetos.<br />5.  Adicione a solução ao controle de origem.<br />6.  Adicione o projeto criado na etapa 1 do controle de origem.<br />7.  Se solicitado, aceite o check-out da solução.<br />8.  Check-in da solução inteira.<br />9. Abra o **Change Source Control** caixa de diálogo.<br />10. Selecione o projeto adicionado (da etapa 6) e clique em **Unbind**.<br />11. Clique em **OK** para fechar a caixa de diálogo.<br />12. Se solicitado, aceite o check-out.<br />13. Reabra **Change Source Control** caixa de diálogo.<br />14. Selecione o projeto adicionado (da etapa 6) e clique em **ligar**.<br />15. Selecione o local original.|Solução e projetos permanecem controlados.|  
  
## <a name="see-also"></a>Consulte também  
 [Guia de teste para Plug-ins de controle de origem](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
