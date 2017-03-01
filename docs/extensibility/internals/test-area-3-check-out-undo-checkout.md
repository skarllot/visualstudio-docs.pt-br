---
title: "Área de teste 3: Check out-desfazer check-out | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
caps.latest.revision: 16
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
ms.openlocfilehash: 40c70d0550789c4c082592baa55de47ebd73d9e4
ms.lasthandoff: 02/22/2017

---
# <a name="test-area-3-check-outundo-checkout"></a>Área de teste 3: Check-Out / desfazer check-out
Essa área de plug-in de teste de controle de origem aborda a edição e reverter itens do repositório de versão por meio de **Check-Out** e **desfazer check-out** comandos.  
  
 **Check-Out**: marcas de um item no armazenamento de versão como check-out, modifica a cópia local para leitura/gravação.  
  
 **Desfazer check-out**: marca um item no armazenamento de versão como check-in, reverte a cópia local para o estado antes do check-out (dependendo das opções).  
  
## <a name="command-menu-access"></a>Acesso ao Menu comando  
 O seguinte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] caminhos de menu do ambiente de desenvolvimento integrado são usados nos casos de teste.  
  
##### <a name="check-out"></a>Fazer Check-out:  
  
-   **Arquivo**, **controle de origem**, **Check-Out**.  
  
-   **Arquivo**, **Check-Out**.  
  
-   Menu de atalho, **Check-Out**.  
  
-   Desfazer check-out: **arquivo**, **controle de origem**, **desfazer check-out**.  
  
## <a name="common-expected-behavior"></a>Comportamento esperado comuns  
  
-   Após o check-out de operação, o arquivo de destino (s) e/ou pastas são marcadas como check-out no repositório de versão.  
  
-   O armazenamento de versão atributos o check-out para o usuário correto.  
  
-   A data e hora do check-out estão corretos (de acordo com as configurações do usuário).  
  
## <a name="test-cases"></a>Casos de teste  
 Estes são os casos de teste específicos para a área de teste de check-out/desfazer check-out.  
  
### <a name="case-3a-check-out"></a>Caso 3a: Check-Out  
 Esta seção aborda a operação do comando fazer check-out.  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Check-Out exclusivo (COE) um projeto do cliente|1.  Crie um projeto de cliente.<br />2.  Adicione a solução ao controle de origem.<br />3.  Check-out do projeto inteiro exclusivamente (**arquivo**, **Check-Out**).|Ocorre o check-out.|  
|Check-Out exclusivo (COE) um sistema de arquivos ou projeto da Web do IIS local|1.  Definir a Conexão do servidor Web para compartilhamento de arquivos **ferramentas**, **opções**, **projetos**, **configurações da Web**.<br />2.  Crie um projeto da Web.<br />3.  Adicione a solução ao controle de origem.<br />4.  Check-out do projeto inteiro exclusivamente (**arquivo**, **controle de origem**, **Check-Out**).|Ocorre o check-out.|  
|Check-out de itens de solução em uma solução (novo método para lidar com outros arquivos)|1.  Crie uma solução em branco.<br />2.  Adicione a solução ao controle de origem.<br />3.  Confira a solução.<br />4.  Adicione vários itens de solução.<br />5.  Check-in de todos os itens adicionados recentemente.<br />6.  Selecione vários itens de solução.<br />7.  Check-out dos itens selecionados (Menu de atalho, **Check-Out**).|Arquivos selecionados são verificados.|  
|Check-Out Local Version (se o plug-in em teste dá suporte a esse recurso)|1.  O usuário 1: Crie um projeto do cliente.<br />2.  O usuário 1: Adicione a solução ao controle de origem.<br />3.  O usuário 2: Abra a solução do controle de origem para outro local.<br />4.  O usuário 2: Check-out de um arquivo.<br />5.  O usuário 2: Modificar o arquivo.<br />6.  O usuário 2: Verifique o arquivo.<br />7.  Usuário 1: Verificar a versão local do arquivo (Verifique o **Check Out Local Version** opção em avançada **Check-Out** caixa de diálogo).|A versão local do arquivo foi extraído.<br /><br /> As modificações de usuário 2 não são aplicadas ao arquivo do usuário 1.|  
  
### <a name="case-3b-disconnected-check-out"></a>Caso 3b: desconectado de Check-out  
 Operando em modo desconectado permite que os usuários algum nível de suporte de controle do código-fonte contínua quando não conectado diretamente a um armazenamento de versão. Isso é feito localmente em cache todas as informações relevantes sobre a solução inscrita e projetos.  
  
 Check-out de operações exclusivo pode ocorrer apenas enquanto estiver conectado ao armazenamento de controle de origem. Compartilhado check-out de operações pode ocorrer a qualquer momento, se conectado ou desconectado. Portanto, quando desconectado do armazenamento de versão, somente o **Check-Out compartilhado** (COS) comando está habilitado. Enquanto estiver desconectado, **desfazer check-out** está desabilitado porque não é possível recuperar a versão antiga para substituir as alterações feitas pelo usuário.  
  
 Quando o usuário se reconecte à versão armazenar, os estados de check-out de todas as soluções inscritas e projetos estão sincronizados. Isso faz as atualizações necessárias para o repositório para os check-outs que o usuário executou. Depois que a sincronização ocorreu, o usuário é capaz de continuar a trabalhar da maneira normal (conectado).  
  
#### <a name="expected-behavior"></a>Comportamento esperado  
  
-   Não é possível usar **Check-Out exclusivamente** comando enquanto estiver desconectado do armazenamento de versão.  
  
-   Não é possível usar **desfazer check-out** comando enquanto estiver desconectado do armazenamento de versão.  
  
-   **Compartilhado Check-Out** comando funciona.  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Enquanto estiver desconectado, check-out de um arquivo, e conecte-se para sincronização|1.  Desconectar um projeto controlado usando a caixa de diálogo Alterar controle de origem (**arquivo**, **controle de origem**, **alterar fonte controlar**l).<br />2.  Check-out um arquivo.<br />3.  Clique em Check-Out (desconectado) na caixa de diálogo de aviso.<br />4.  Edite o arquivo.<br />5.  Conecte usando a caixa de diálogo Alterar controle de origem.<br />6.  Obtenha a versão mais recente do arquivo editado.|Comportamento esperado comuns|  
  
### <a name="case-3c-query-editquery-save-qeqs"></a>Caso 3C: Editar consulta/salvar (QEQS)  
 Itens sob controle de origem são rastreadas para edições, alterações, e salva para ajudar os usuários facilmente gerenciar seus arquivos. Quando um item controlado "check-in" for editado, QEQS intercepta a edição de tentativa e solicita que o usuário se ele deseja fazer check-out do arquivo para editá-lo. Dependendo de **ferramentas**, **opções** configurações, o usuário é forçada a verificar fora o arquivo para editar ou com talvez tenha permissão para editar uma cópia na memória e check-out mais tarde. Se o usuário **ferramentas**, **opções** configuração não está definida para exibir a caixa de diálogo de confirmação e check-out apenas, e, depois, quando o usuário faz sua edição, o arquivo automaticamente, sempre que possível.  
  
#### <a name="expected-behavior"></a>Comportamento esperado  
  
-   Após o check-out de operação, o arquivo de destino (s) e/ou pastas são marcadas como check-out no repositório de versão.  
  
-   O armazenamento de versão atributos o check-out para o usuário correto.  
  
-   A data e hora de check-out estão corretos (de acordo com as configurações do usuário).  
  
-   A cópia local do arquivo de destino ou da pasta é gravável.  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Editar o arquivo de texto que o check-in|1.  Crie um novo projeto que contém um arquivo de texto.<br />2.  Adicione a solução ao controle de origem.<br />3.  Definir **ferramentas**, **opções**, **controle de origem**, **permitir que arquivos sejam editados enquanto somente leitura no disco** para desmarcada.<br />4.  Definir **ferramentas**, **opções**, **controle de origem**, **Prompt para check-out** no **quando o check-in arquivos são editados** caixa de combinação.<br />5.  Definir **ferramentas**, **opções**, **controle de origem**, **Prompt para check-out** no **quando o check-in arquivos são salvos** caixa de combinação.<br />6.  Abra o arquivo de texto no editor, tente digitar o novo texto no arquivo. Se essa etapa for bem-sucedida, continue para a próxima etapa.<br />7.  Clique em **Cancelar** no **Check-out para edição** caixa de diálogo. Se essa etapa for bem-sucedida, continue para a próxima etapa.<br />8.  Definir **ferramentas**, **opções**, **controle de origem**, **permitir que arquivos sejam editados enquanto somente leitura no disco** como marcada.<br />9. Abra o arquivo de projeto no editor, tente digitar o novo texto no arquivo. Se essa etapa for bem-sucedida, continue para a próxima etapa.<br />10. Clique em **editar** no **Check-out para edição** caixa de diálogo. Se essa etapa for bem-sucedida, continue para a próxima etapa.<br />11. Edite o arquivo de texto e tentar salvá-lo.|`Result of step 6:`<br /><br /> Check-out para a caixa de diálogo Editar é exibida.<br /><br /> `Result of step 7:`<br /><br /> O arquivo não é alterado.<br /><br /> `Result of step 9:`<br /><br /> Check-out para a caixa de diálogo Editar é exibida.<br /><br /> `Result of step 10:`<br /><br /> Você pode editar o arquivo de projeto na memória.<br /><br /> `Result of step 11:`<br /><br /> Em Salvar, o Check-out em Salvar caixa de diálogo é exibida.|  
|Editar um arquivo de solução check-in|Repita as etapas conforme descrito em anteriores de teste, mas em vez de modificar um arquivo de texto, modificar a solução alterando propriedades da solução.|Mesmo que o teste anterior|  
|Editar um arquivo de projeto check-in|Repita as etapas conforme descrito na anterior de teste, mas em vez de modificar um arquivo de texto, modificar o projeto alterando propriedades do projeto.|Mesmo que o teste anterior.|  
  
### <a name="case-3d-silent-check-out"></a>Caso 3d: Check-Out silencioso  
 Essa verificação de bastidores subárea cenários onde o **Check-Out** caixa de diálogo não aparecer por usuário **ferramentas**, **opções**, **configurações de controle de origem**.  
  
#### <a name="expected-behavior"></a>Comportamento esperado  
  
-   Após o check-out de operação, o arquivo de destino (s) e/ou pastas são marcadas como check-out no repositório de versão.  
  
-   O armazenamento de versão atributos o check-out para o usuário correto.  
  
-   A data e hora de check-out está correto (de acordo com as configurações do usuário).  
  
-   A cópia local do arquivo de destino ou da pasta é gravável.  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Silenciosa check-out de um arquivo|1.  Definir **ferramentas**, **opções**, **controle de origem** para **arquivos de check-out automaticamente em Editar**.<br />2.  Crie um novo projeto com um arquivo.<br />3.  Adicione a solução ao controle de origem.<br />4.  Check-out do arquivo.|Arquivo check-out silencioso (nenhuma interface do usuário).|  
|Silenciosa check-out de um projeto|1.  Definir **ferramentas**, **opções**, **controle de origem** para **arquivos de check-out automaticamente em Editar**.<br />2.  Crie um novo projeto.<br />3.  Adicione a solução ao controle de origem.<br />4.  Check-out do projeto.|Arquivo check-out silencioso (nenhuma interface do usuário).|  
  
### <a name="case-3e-undo-check-out"></a>Caso 3e: Desfazer Check-Out  
 **Desfazer Check-Out** é usado para cancelar um arquivo com check-out de status e evite fazer check-in das alterações feitas no arquivo.  
  
#### <a name="expected-behavior"></a>Comportamento esperado  
  
-   O padrão baseia-se o usuário **Check-out da versão Local** configuração. Se o usuário escolheu fazer check-out da versão local, o padrão para desfazer check-out é sempre reverter para a versão com check-out.  
  
-   Mediante a aceitação de desfazer, os ícones no **Solution Explorer** são atualizados para afetado arquivos e o item é removido do **check-ins pendentes** janela.  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Desfazer check-out de um único arquivo check-out exclusivo|1.  Crie um projeto de cliente.<br />2.  Adicione a solução ao controle de origem.<br />3.  Check-out de um arquivo exclusivamente.<br />4.  Modificar o arquivo.<br />5.  Desfazer check-out (**arquivo**, **controle de origem**, **desfazer check-out**).|Comportamento esperado comuns.|  
|Desfazer check-out de um único arquivo check-out compartilhado|1.  Crie um projeto de cliente.<br />2.  Adicione a solução ao controle de origem.<br />3.  Check-out de um arquivo compartilhado.<br />4.  Modificar o arquivo.<br />5.  Desfazer check-out (**arquivo**, **controle de origem**, **desfazer check-out**).|Comportamento esperado comuns.|  
|Desfazer check-out de um projeto depois de adicionar arquivos ao projeto|1.  Criar um novo projeto e adicioná-lo ao controle de origem.<br />2.  Check-out do projeto.<br />3.  Adicione um arquivo ao projeto.<br />4.  Desfazer check-out do projeto.|Arquivo adicionado é removido do projeto no Solution Explorer.<br /><br /> Não é check-out do projeto.|  
|Desfazer check-out de um projeto após a exclusão de arquivos do projeto|1.  Criar um novo projeto e adicioná-lo ao controle de origem.<br />2.  Check-out do projeto.<br />3.  Exclua um arquivo do projeto.<br />4.  Desfazer check-out do projeto.|Arquivo excluído aparece sob o projeto no Solution Explorer.<br /><br /> Não é check-out do projeto.|  
  
## <a name="see-also"></a>Consulte também  
 [Guia de teste para Plug-ins de controle de origem](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
