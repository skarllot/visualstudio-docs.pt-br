---
title: "How to: Define and consume activity delegates in the Workflow Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "sdanie"
manager: "erikre"
---
# How to: Define and consume activity delegates in the Workflow Designer
[!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] inclui um novo de designer para fora da caixa para atividades de <xref:System.Activities.Statements.InvokeDelegate> .  Este criador pode ser usado para atribuir os representantes para a atividade que derivam de <xref:System.Activities.ActivityDelegate>, como <xref:System.Activities.ActivityAction> ou <xref:System.Activities.ActivityFunc%601>.  
  
### Defina um representante de atividades  
  
1.  Em [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], selecione **Arquivo**, **Novo**, **Projeto**.  Selecione o nó de **Fluxo de Trabalho** à esquerda, e o modelo de **Aplicativo de console do fluxo de trabalho** à direita.  Nomeie o projeto \(se desejar\) e clique **OK**.  
  
2.  Clique com o botão direito do mouse no projeto em **Gerenciador de Soluções** e selecione **Adicionar**, **Novo Item...** Selecione o nó de **Fluxo de Trabalho** à esquerda, e o modelo de **Atividade** à direita.  Nomeie a nova atividade **MyForEach.xaml** e clique **OK**.  A atividade será aberto no designer de fluxo de trabalho.  
  
3.  No designer de fluxo de trabalho, clique na guia **Argumentos** .  
  
4.  Clique em **Criar Argumento**.  Nomeie o novo argumento **Itens**.  
  
5.  Na coluna de **Tipo de argumento** , **Matriz de T \[\]**.  
  
6.  No navegador de tipo, **Objeto**.  Clique **OK**.  
  
7.  Clique **Criar Argumento** novamente.  Nomeie o novo argumento **Corpo**.  Na coluna de **Direção** para o novo argumento, **Propriedade**.  
  
8.  Na coluna tipo de argumento, selecione **Navegue para tipos…**  
  
9. No navegador de tipo, entre em **ActivityAction** no campo de **Nome de Tipo** .  Selecione **ActivityAction \< T \>** na exibição de árvore.  Selecione **Objeto** na lista suspensa que aparece para atribuir o tipo **ActivityAction\<Object\>** ao argumento.  
  
10. Arraste uma atividade de <xref:System.Activities.Statements.While> da seção de **Fluxo de Controle** da caixa de ferramentas para a superfície de designer.  
  
11. Selecione a atividade de <xref:System.Activities.Statements.While> , e selecione a guia de **Variáveis** .  
  
12. Selecione **Criar Variável**.  Nomeie **Índice**nova variável.  
  
13. Na coluna de **Tipo de variável** , **Int32**.  Deixe **Escopo** como **Quando**, e a placa de coluna de **Padrão** .  
  
14. Defina a propriedade de **Condição** de atividade de <xref:System.Activities.Statements.While> a **index \< Items.Length;**.  
  
15. Arraste uma atividade de <xref:System.Activities.Statements.InvokeDelegate> da seção de **Primitivas** da caixa de ferramentas para **Corpo** de atividade de <xref:System.Activities.Statements.While> .  
  
16. **Corpo** Selecione no representante suspenso.  
  
17. Na grade **Propriedades** para a atividade <xref:System.Activities.Statements.InvokeDelegate>, clique no botão **…** na propriedade **Argumentos Delegados**.  
  
18. Na coluna de **Valor** de argumento nomeado **Argumento**, entre em **Itens índice \[\]**.  Clique **OK** para fechar a caixa de diálogo **DelegateArguments** .  
  
19. Arraste uma atividade de <xref:System.Activities.Statements.Assign> na linha horizontal abaixo de atividade de <xref:System.Activities.Statements.InvokeDelegate> .  A atividade de <xref:System.Activities.Statements.Assign> será criada, e uma atividade de <xref:System.Activities.Statements.Sequence> será criada automaticamente para conter as duas atividades na seção de **Corpo** de atividade de **MyForEach** .  A sequência é necessária pois a seção de **Corpo** pode conter apenas uma única atividade.  Criar automaticamente uma nova atividade de <xref:System.Activities.Statements.Sequence> é um novo recurso de [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)].  
  
20. Defina a propriedade de **A** de atividade de <xref:System.Activities.Statements.Assign> a **índice**.  Defina a propriedade de **Valor** de atividade de **Atribuir** a **index\+1**.  
  
 A atividade personalizado de **MyForEach** chamar agora uma atividade arbitrária uma vez para cada valor passado nele através da coleção de **Items** , com os valores na coleção como entradas para atividades.  
  
### Use a atividade personalizado em um fluxo de trabalho  
  
1.  Compile o projeto pressionando **Ctrl\+Shift\+B**.  
  
2.  Em **Gerenciador de Soluções**, abra **Workflow1.xaml** no designer.  
  
3.  Arraste uma atividade de **MyForEach** da caixa de ferramentas para a superfície de designer.  A atividade será em uma seção da caixa de ferramentas com o mesmo nome que o projeto.  
  
4.  Defina a propriedade de **Itens** de atividade de **MyForEach** a **novo objeto \[\] {1, “ABC”}**.  
  
5.  Arraste uma atividade de <xref:System.Activities.Statements.WriteLine> da seção de **Primitivas** da caixa de ferramentas para a seção de **Delegate:Corpo** de atividade de **MyForEach** .  
  
6.  Defina a propriedade de **Texto** de atividade de <xref:System.Activities.Statements.WriteLine> a **Argument.ToString \(\)**.  
  
 Quando o fluxo de trabalho é executado, o console mostrará o seguinte:  
  
  **1**  
 **ABC**