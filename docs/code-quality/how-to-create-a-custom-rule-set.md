---
title: "Como criar um conjunto de regras personalizado | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.addremoverulesets"
helpviewer_keywords: 
  - "Development Edition, conjuntos de regra"
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como criar um conjunto de regras personalizado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Em [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)], [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)], e [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], você pode criar e modificar *uma regra personalizada definida* para atender às necessidades de projeto específico associadas à análise de código.  Para criar um conjunto de regra personalizada, você abre um ou mais conjuntos padrão da regra no publicador do conjunto de regra.  Você pode adicionar ou remova as regras específicas e pode modificar a ação que ocorre quando a análise de código determina quais uma regra esteve violada.  
  
 Para criar um novo conjunto de regra personalizada, você salvará o usando um nome de arquivo novo.  O conjunto de regra personalizada é atribuído automaticamente ao projeto.  
  
## Abrindo o publicador do conjunto de regra  
  
#### Para abrir um arquivo do conjunto de regra vazia no publicador do conjunto de regra  
  
1.  No menu de **Arquivo** de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], aponte para **Novo** e clique em **Arquivo**.  
  
2.  Na caixa de diálogo de **Novo Arquivo** , clique em **Geral** na lista de **Modelos Instalados** , e selecione **Conjunto de Regras da Análise de Código**.  
  
3.  O editor do conjunto de regra aparece.  Nenhuma regra é selecionada na lista do publicador.  
  
#### Para criar uma regra personalizada de um único conjunto de regra existente  
  
1.  No Solution Explorer, clique com o botão direito do mouse no projeto e selecione **Propriedades**.  
  
2.  Na guia de **Propriedades** , clique em **Análise de Código**.  
  
3.  Na lista suspensa de **Conjunto de Regras** , siga um destes procedimentos:  
  
    -   Selecione a regra definida que você deseja personalizar.  
  
     \- ou \-  
  
    -   Selecione **\<Procurar…\>** para especificar uma regra existente definida que não está na lista.  
  
4.  Clique **Abrir** para exibir as regras no publicador do conjunto de regra.  
  
#### Para criar uma regra personalizada definida de vários conjuntos de regra  
  
1.  No Solution Explorer, clique com o botão direito do mouse no projeto e selecione **Propriedades**.  
  
2.  Na guia de **Propriedades** , clique em **Análise de Código**.  
  
3.  Selecione **\<Escolha várias define a regra…\>**de **Executar este conjunto de regras**.  
  
4.  Na caixa de diálogo de **Adicionar ou Remover Conjuntos de Regras** , selecione os conjuntos de regra em que você deseja basear o novo conjunto de regras e clique em **OK**.  
  
5.  Salvar o novo conjunto de regras.  
  
     O nome do novo conjunto de regras é selecionado na lista de **Executar este conjunto de regras** .  Você pode alterar o nome para exibição da regra definida na próxima etapa.  
  
6.  \(Opcional\) Para alterar o nome para exibição do conjunto de regras, em menu de **Exibir** , clique em **Janela de Propriedades**.  Digite o nome para exibição na caixa de **Nome** .  
  
7.  Para adicionar, remover, modificar ou regras específicas do código no novo conjunto de regras, clique em **Abrir**.  
  
## Modificando um conjunto de regras  
  
#### Para alterar uma regra definida no publicador do conjunto de regra  
  
-   Para alterar o nome para exibição do conjunto de regras, no menu de **Exibir** , clique em **Janela de Propriedades**.  Digite o nome para exibição na caixa de **Nome** .  Observe que o nome para exibição pode ser diferente do nome do arquivo.  
  
-   Para adicionar todas as regras de grupo para um conjunto de regra personalizada, marque a caixa de seleção do grupo.  Para remover todas as regras de grupo, desmarque a caixa de seleção.  
  
-   Para adicionar uma regra específica ao conjunto de regra personalizada, marque a caixa de seleção da regra.  Para remover a regra do conjunto de regras, desmarque a caixa de seleção.  
  
-   Para modificar a ação tomada quando uma regra é violada em uma análise de código, clique no campo de **Ação** para a regra e selecione um dos seguintes valores:  
  
     **Warn** \- gerencia um aviso.  
  
     **Error** \- gerencia um erro.  
  
     **None** \- desabilita a regra.  Esta ação é a mesma que removendo a regra do conjunto de regras.  
  
## Alterando a exibição de conjunto do editor de regra  
  
#### Para agrupar, filtrar, ou alterar os campos no publicador do conjunto de regras usando a barra de ferramentas do editor de regra  
  
-   Para expandir as regras em todos os grupos, clique **Expandir Tudo**.  
  
-   Para recolher as regras em todos os grupos, clique **Recolher Tudo**.  
  
-   Para alterar o campo que as regras são agrupadas pelo, selecione o campo da lista de **Agrupar por** .  Para exibir as regras não agrupadas **\<Nenhum\>**, selecione.  
  
-   Para adicionar ou remover campos em colunas de regra, clique em **Opções de Coluna**.  
  
-   Para ocultar as regras que não se aplicam à solução atual, **Ocultar as regras que não se aplicam à solução atual**.  
  
-   Para alternar entre a exibição e ocultar as regras que são atribuídas a ação de erro, clique em **Mostrar regras que podem gerar erros de Análise de Código**.  
  
-   Para alternar entre a exibição e ocultar as regras que são atribuídas a ação de aviso, clique em **Mostrar regras que podem gerar avisos de Análise de Código**.  
  
-   Para alternar entre a exibição e ocultar as regras que são atribuídas a ação de **Nenhum** , clique em **Mostrar regras que não estão habilitadas**.  
  
-   Para adicionar ou remover conjuntos de regra padrão da Microsoft para o conjunto atual de regra, clique em **Adicionar ou remover conjuntos de regras filhas**.  
  
## Consulte também  
 [Como configurar a análise de código para um projeto de código gerenciado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Referência do conjunto de regras da análise de código](../code-quality/code-analysis-rule-set-reference.md)