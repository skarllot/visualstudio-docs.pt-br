---
title: 'Como: fornecer contexto para editores | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
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
ms.openlocfilehash: 362cd554e0723b1137d033440c9844d6cf3e59dd
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-provide-context-for-editors"></a>Como: fornecer contexto para editores
Para um editor, o contexto está ativo somente quando o editor tem o foco ou tinha foco imediatamente antes do foco foi movido para uma janela de ferramenta. Você pode fornecer contexto para um editor, fazendo o seguinte:  
  
1.  Crie um recipiente de contexto.  
  
2.  Publica o recipiente de contexto para o identificador de elemento de seleção (SEID).  
  
3.  Manter o contexto no recipiente de.  
  
 Essas tarefas são cobertas por procedimentos a seguir. Para obter mais informações sobre como fornecer o contexto, consulte **programação robusta** mais adiante neste tópico.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Para criar um recipiente de contexto para um editor ou designer  
  
1.  Chamar `QueryService` em seu <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>interface para o <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>service.</xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>  
  
     Um ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>interface é retornada.</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>  
  
2.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A>método para criar um novo recipiente de contexto ou subcontexto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A>  
  
     Um ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>interface é retornada.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>  
  
3.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>método para adicionar atributos, palavras-chave de pesquisa ou palavras-chave F1 para o recipiente de contexto ou subcontexto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>  
  
4.  Se você estiver criando um recipiente subcontexto, chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A>método para vincular o recipiente subcontexto para o recipiente de contexto pai.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A>  
  
5.  Chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>para receber notificação quando o **ajuda dinâmica** janela está prestes a atualizar.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>  
  
     Tendo o **ajuda dinâmica** janela chamar seu editor quando ele estiver pronto para atualizar lhe dá a oportunidade de adiar a alterar o contexto até que a atualização ocorra. Isso pode melhorar o desempenho porque ele permite que você atrasar a execução demorados algoritmos até que o tempo ocioso do sistema está disponível.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>Para publicar o recipiente de contexto para o SEID  
  
1.  Chamar `QueryService` sobre o <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>service para retornar um ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> </xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>  
  
2.  Chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, especificando um identificador de elemento (`elementid` parâmetro) valor de SEID_UserContext para indicar que você está passando o contexto no nível global.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>  
  
3.  Quando o editor ou designer se torna ativo, os valores em seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>objeto são propagadas para a seleção global.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> Você só precisa concluir esse processo uma vez por sessão e, em seguida, armazenar o ponteiro para o contexto global criado quando chamado <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>  
  
### <a name="to-maintain-the-context-bag"></a>Para manter o recipiente de contexto  
  
1.  Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>para garantir que o **ajuda dinâmica** janela chama editor ou designer antes de atualizar.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>  
  
     Para cada pacote de contexto chamado <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>depois que o recipiente de contexto é criado e implementou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, as chamadas IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>para notificar o provedor de contexto que o recipiente de contexto será atualizado.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> Você pode usar essa chamada para alterar os atributos e as palavras-chave no recipiente de contexto e em quaisquer pacotes subcontexto, antes de **ajuda dinâmica** janela atualização ocorrer.  
  
2.  Chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>no conjunto de contexto para indicar que o editor ou designer tem novo contexto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>  
  
     Quando o **ajuda dinâmica** janela chamadas <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>para indicar que está atualizando, editor ou designer possa atualizar o contexto adequadamente para o recipiente de contexto pai e recipientes qualquer subcontexto naquele momento.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>  
  
    > [!NOTE]
    >  O `SetDirty` sinalizador é definido automaticamente como `true` sempre que o contexto é adicionado ou removido do recipiente de contexto. O **ajuda dinâmica** janela apenas chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>no conjunto de contexto se o `SetDirty` sinalizador é definido como `true`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> Ele é zerado `false` após a atualização.  
  
3.  Chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>para adicionar contexto à coleção contexto ativo ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>Remover contexto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>  
  
## <a name="robust-programming"></a>Programação robusta  
 Se você estiver escrevendo seu próprio editor, você deve concluir os procedimentos deste tópico para fornecer contexto para o editor de todos os três.  
  
> [!NOTE]
>  Para ativar corretamente uma janela do editor ou designer e certifique-se de que o roteamento de comando é atualizado corretamente, você deve chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>no componente para que a janela de foco.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>  
  
 O SEID é uma coleção de propriedades que são alteradas com base na seleção. SEID informações estão disponíveis por meio da seleção global. A seleção global é conectada a eventos disparados pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>interface, e tem uma lista de tudo que está selecionado (editor atual, janela de ferramenta atual, hierarquia atual e assim por diante).</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>  
  
 Editores e designers, em qual contexto pode ser alterado sempre que o cursor se move dentro de uma palavra, é ineficiente a atualização constante de recipiente de contexto. Para facilitar a atualização mais eficiente sempre que detectar o cursor movendo dentro do editor ou a janela do designer, você pode chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> Isso permite que você mantenha as alterações de contexto até que haja tempo ocioso e o serviço de contexto do IDE envia notificação para o editor ou designer de **ajuda dinâmica** janela está atualizando. Essa abordagem é usada no procedimento "para manter o recipiente de contexto" neste tópico.  
  
 Depois de fornecer contexto para atividades em seu editor ou designer, você deve fornecer uma palavra-chave do F1 específica para permitir que os usuários obter ajuda sobre o editor ou designer em si.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>
