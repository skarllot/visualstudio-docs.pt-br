---
title: "Área de teste 7: Compartilhamento | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
caps.latest.revision: 11
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
ms.openlocfilehash: a2b5e1b45bd2a8fb82265e945f76519111bf1c6d
ms.lasthandoff: 02/22/2017

---
# <a name="test-area-7-share"></a>Testar área 7: compartilhamento
Essa área de teste abrange itens compartilhamento entre locais por meio de **compartilhamento** comando.  
  
 Uma operação hhare é a aparente eliminação de duplicação de arquivos e itens de pasta entre dois ou mais locais dentro de uma hierarquia de arquivos de controle de origem. Eliminação de duplicação não realmente ocorrer no servidor, mas o usuário verá o mesmo arquivo em dois ou mais locais especificados. Sempre que forem feitas alterações para qualquer um dos itens compartilhados, essas alterações aparecem em todos os outros locais compartilhados.  
  
 Em pastas de compartilhamento funciona se você selecionar uma pasta pelo menos um arquivo sob controle de origem nele. O comando de compartilhamento é desabilitado nas seguintes condições:  
  
-   Se a pasta selecionada é uma pasta vazia.  
  
-   Se há uma pasta real, mas não contém nenhum arquivo de controle de origem.  
  
-   Se houver uma pasta virtual, arquivos sob controle de origem estão nele ou não.  
  
-   Se houver um projeto de Web Site remoto.  
  
## <a name="command-menu-access"></a>Acesso ao Menu comando  
 O seguinte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] caminhos de menu do ambiente de desenvolvimento integrado são usados nos casos de teste.  
  
 Share: **File**->**Source Control**->**Share**.  
  
## <a name="expected-behavior"></a>Comportamento esperado  
  
-   Arquivo compartilhado é exibido no local compartilhado.  
  
-   Exibindo a fonte controle versão store histórico mostra que os arquivos são compartilhados.  
  
-   Editar um arquivo compartilhado edita os locais do arquivo.  
  
## <a name="test-cases"></a>Casos de teste  
 Estes são os casos de teste específicos para a área de teste do compartilhamento.  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Compartilhar um arquivo de um projeto carregado no controle de origem para outro projeto carregado|1.  Crie um novo projeto.<br />2.  Adicione um segundo projeto à solução.<br />3.  Crie um arquivo no segundo projeto com um nome que não está no projeto primeiro.<br />4.  Adicione a solução ao controle de origem.<br />5.  Selecione o projeto primeiro.<br />6.  Open **Share** dialog box (**File** -> **Source Control** -> **Share**).<br />7.  Compartilhe o arquivo do projeto segundo para o primeiro projeto.<br />8.  Aceitar **Check-Out** se solicitado.|Comportamento esperado comuns.|  
|Compartilhar um arquivo de um projeto para outro|1.  Crie um novo projeto.<br />2.  Adicione-o ao controle de origem.<br />3.  Feche a solução.<br />4.  Criar um segundo projeto (nova solução).<br />5.  Adicione a solução ao controle de origem.<br />6.  Selecione o projeto.<br />7.  Abra o **compartilhamento** caixa de diálogo (**arquivo** -> **controle de origem** -> **compartilhamento**).<br />8.  Compartilhe um arquivo do projeto adicionado anteriormente ao projeto aberto.<br />9. Aceitar **Check-Out** se solicitado.|Comportamento esperado comuns.|  
|Compartilhar um arquivo não faz parte do projeto do controle de origem para o projeto carregado no momento|1.  Crie um novo projeto.<br />2.  Adicione a solução ao controle de origem.<br />3.  Adicione um arquivo ao controle de origem que não faz parte do projeto ou da solução.<br />4.  Selecione o projeto e abra o **compartilhamento** caixa de diálogo (**arquivo** -> **controle de origem** -> **compartilhamento**).<br />5.  Selecione um arquivo dentro do **compartilhar** caixa de diálogo que não existem no projeto atual ou da solução e compartilhá-lo.<br />6.  Aceitar **Check-Out** se solicitado.|O repositório de controle de origem executou um Get, portanto o arquivo agora é o local do projeto.|  
|Compartilhamento de arquivos dentro do mesmo projeto em uma pasta diferente|1.  Selecione **Check-out automaticamente** na **ferramentas** -> **opções** -> **Source Control**.<br />2.  Criar um novo projeto e adicioná-lo ao controle de origem.<br />3.  Adicione uma pasta para o projeto.<br />4.  Adicione um arquivo para a pasta e verifique na pasta.<br />5.  Selecione a pasta.<br />6.  Open **Share** dialog box (**File** -> **Source Control** -> **Share**).<br />7.  Arquivo de compartilhamento para a pasta selecionada.|Comportamento esperado comuns.<br /><br /> Pasta deve ser verificada com um arquivo antes de ser usada para compartilhamento.|  
|Compartilhar uma pasta para o projeto carregado — recursiva|1.  Crie um novo projeto.<br />2.  Adicione a solução ao controle de origem.<br />3.  Selecione o projeto.<br />4.  Abra o **compartilhamento** caixa de diálogo (**arquivo** -> **controle de origem** -> **compartilhamento**).<br />5.  Selecione uma pasta.<br />6.  Compartilhe a pasta repetidamente no projeto.|Comportamento esperado comuns.|  
|Compartilhar vários arquivos de um projeto para outro|1.  Crie um novo projeto com vários arquivos.<br />2.  Adicione a solução ao controle de origem.<br />3.  Feche a solução.<br />4.  Crie um novo projeto em uma nova solução.<br />5.  Adicione a solução ao controle de origem.<br />6.  Selecione o projeto.<br />7.  Abra o **compartilhamento** caixa de diálogo (**arquivo** -> **controle de origem** -> **compartilhamento**).<br />8.  Compartilhe vários arquivos do projeto criado anteriormente para o projeto aberto no momento.|Comportamento esperado comuns.|  
  
## <a name="see-also"></a>Consulte também  
 [Guia de teste para Plug-ins de controle de origem](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
