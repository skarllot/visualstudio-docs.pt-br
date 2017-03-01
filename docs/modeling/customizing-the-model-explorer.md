---
title: Personalizando o Gerenciador de modelos | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
ms.assetid: d2926444-9408-41d8-a27e-3fd0c416f9ac
caps.latest.revision: 20
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 880b10da32e858ce6e532bc5b8e75227a6e999d7
ms.lasthandoff: 02/22/2017

---
# <a name="customizing-the-model-explorer"></a>Personalizando o Gerenciador de Modelos
Você pode alterar a aparência e comportamento do explorer para o designer de linguagem específica do domínio da seguinte maneira:  
  
-   Altere o título da janela.  
  
-   Altere o ícone de guia.  
  
-   Altere os ícones para nós.  
  
-   Oculte nós.  
  
## <a name="changing-the-window-title"></a>Alterar o título da janela  
 Para alterar o título da janela do explorer gerado, selecione **comportamento do Explorador** no **Gerenciador de DSL**e, em seguida, no **propriedades** janela, defina a **título** propriedade para o título que você deseja.  
  
## <a name="changing-the-tab-icon"></a>Alterar o ícone de guia  
 Para alterar o ícone de guia de soluções, use um ícone 16x16 pixels em um arquivo. bmp. Coloque o arquivo de ícone na pasta \DslPackage\Resources\ e, em seguida, altere o nome de arquivo para **ModelExplorerToolWindowBitmaps.bmp**. Por exemplo, você pode alterar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] setup.ico ícone de arquivo no formato. bmp e renomeie-o para **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. O designer gerado exibirá esse ícone na guia de soluções quando ela estiver encaixada junto com **Solution Explorer**.  
  
## <a name="setting-custom-icons-on-explorer-nodes"></a>Ícones personalizados em nós do Gerenciador de configuração  
 Você pode personalizar nós em suas soluções usando as configurações de nó do explorer. O procedimento a seguir mostra como adicionar um ícone para um nó.  
  
#### <a name="to-add-an-icon-to-an-explorer-node"></a>Para adicionar um ícone para um nó do explorer  
  
1.  Criar um [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] solução usando o modelo de solução de fluxo de tarefa.  
  
2.  Colocar um arquivo. bmp que contém um ícone de 16x16 pixels no **Dsl\Resources** pasta na solução.  
  
3.  No **Gerenciador de DSL**, clique com botão direito **Explorer comportamento** e, em seguida, clique em **adicionar novas configurações do Gerenciador de nó**.  
  
     Um **ExplorerNodeSettings** nó aparece sob o **configurações personalizadas do nó** nó.  
  
4.  Selecione **ExplorerNodeSettings**e, em seguida, o **propriedades** janela, defina **classe** para **ator**.  
  
5.  Definir **exibição do ícone para** para o caminho do arquivo de ícone.  
  
6.  Transformar todos os modelos, compilar e executar a solução.  
  
7.  No designer gerado, abra o diagrama de exemplo.  
  
     O Explorer deverá mostrar três **ator** nós que têm seu ícone.  
  
> [!NOTE]
>  Se você tiver definido um ícone de nó para qualquer elemento que é exibido no Gerenciador de gerado, todos os nós do explorer exibirá o ícone. Se nenhum ícone for definida, os nós exibirá o ícone padrão.  
  
## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Alterar o nome exibido em um nó do Explorer  
 Você pode alterar como os nomes de elementos de modelo são exibidos em suas soluções. O procedimento a seguir mostra como exibir o nome do **tarefa** que é referenciado por uma **comentário** no nó de comentário.  
  
#### <a name="to-display-a-property"></a>Para exibir uma propriedade  
  
1.  Abra a solução que você criou no procedimento anterior.  
  
2.  Verifique se o **comentário** faz referência a uma classe de domínio único, definindo a multiplicidade da função com o nome da propriedade **assuntos** para 0..1. O nome da propriedade deve se tornar **assunto**, e o nome da relação deve se tornar **CommentReferencesSubject**.  
  
3.  No **Gerenciador de DSL**, clique com botão direito **Explorer comportamento** e, em seguida, clique em **adicionar novas configurações do Gerenciador de nó**.  
  
     Um **ExplorerNodeSettings** nó aparece sob o **configurações personalizadas do nó** nó.  
  
4.  Selecione **ExplorerNodeSettings**e, em seguida, o **propriedades** janela, defina **classe** para **comentário**.  
  
5.  Clique com botão direito do **comentário** nó e depois clique em **adicionar novo caminho da propriedade**.  
  
     Um novo nó aparece chamado **propriedade exibida**.  
  
6.  Selecione **propriedade exibida**e, em seguida, no **propriedades** janela, clique no campo de valor de **caminho de propriedade**. Selecione **comentário**, em seguida, **CommentReferencesSubject**, em seguida, **FlowElement**. O caminho resultante deve se parecer com **CommentReferencesSubject.Subject/! Assunto**.  
  
7.  No campo valor do **propriedade**, selecione **nome**.  
  
8.  Transformar todos os modelos, compilar e executar sua solução.  
  
9. No designer gerado, abra o diagrama de exemplo.  
  
10. Desenhar um **comentário conector** entre o elemento de comentário e o **Task1** elemento no diagrama.  
  
     O nó Explorer deve exibir o comentário como **Task1**.  
  
## <a name="hiding-nodes"></a>Ocultar nós  
 Você pode ocultar um nó em seu explorer adicionando seu caminho para o **nós ocultos** nó a **Gerenciador de DSL**. O procedimento a seguir mostra como ocultar **comentário** nós.  
  
#### <a name="to-hide-an-explorer-node"></a>Para ocultar um nó do explorer  
  
1.  Abra a solução que você criou no procedimento anterior.  
  
2.  No **Gerenciador de DSL**, clique com botão direito **Explorer comportamento** e, em seguida, clique em **adicionar novo caminho de domínio**.  
  
     A **caminho do domínio** nó aparece no **nós ocultos**.  
  
3.  Selecione **caminho do domínio**e, em seguida, no **propriedades** janela, clique no campo de valor de **definição de caminho**. Selecione **fluxos**, em seguida, **FlowGraphHasComments**. O caminho resultante deve se parecer com **FlowGraphHasComments.Comments**  
  
4.  Transformar todos os modelos, compilar e executar sua solução.  
  
5.  No designer gerado, abra o diagrama de exemplo.  
  
     O explorer deverá mostrar apenas uma **atores** nó e não deve mostrar o **comentários** nó.  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica do domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
