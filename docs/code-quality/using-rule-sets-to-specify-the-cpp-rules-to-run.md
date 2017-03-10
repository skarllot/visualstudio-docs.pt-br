---
title: "Usando conjuntos de regras para especificar as regras do C++ para execu&#231;&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Usando conjuntos de regras para especificar as regras do C++ para execu&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Em [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] e em [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)], você pode criar e modificar *uma regra personalizada definida* para atender às necessidades de projeto específico associadas à análise de código.  Para criar um conjunto de regras personalizadas C\+\+, o projeto c criando \/C deve estar aberto no Visual Studio IDE.  Depois você abre uma regra padrão definida no publicador do conjunto de regra e depois adiciona ou remove as regras específicas e altera opcionalmente a ação que ocorre quando a análise de código determina quais uma regra esteve violada.  
  
 Para criar um novo conjunto de regra personalizada, você salvará o usando um nome de arquivo novo.  O conjunto de regra personalizada é atribuído automaticamente ao projeto.  
  
## Abrindo o publicador do conjunto de regra  
  
#### Para criar uma regra personalizada de um único conjunto de regra existente  
  
1.  No Solution Explorer, abra o menu de atalho do projeto e escolha **Propriedades**.  
  
2.  Na guia de **Propriedades** , escolha **Análise de Código**.  
  
3.  Na lista suspensa de **Conjunto de Regras** , siga um destes procedimentos:  
  
    -   Escolha a regra definida que você deseja personalizar.  
  
     \- ou \-  
  
    -   Escolha **\<Procurar…\>** para especificar uma regra existente definida que não está na lista.  
  
4.  Escolha **Abrir** para exibir as regras no publicador do conjunto de regra.  
  
#### Para alterar uma regra definida no publicador do conjunto de regra  
  
-   Para alterar o nome para exibição do conjunto de regras, no menu de **Exibir** , escolha **Janela de Propriedades**.  Digite o nome para exibição na caixa de **Nome** .  Observe que o nome para exibição pode ser diferente do nome do arquivo.  
  
-   Para adicionar todas as regras de grupo para um conjunto de regra personalizada, marque a caixa de seleção do grupo.  Para remover todas as regras de grupo, desmarque a caixa de seleção.  
  
-   Para adicionar uma regra específica ao conjunto de regra personalizada, marque a caixa de seleção da regra.  Para remover a regra do conjunto de regras, desmarque a caixa de seleção.  
  
-   Para modificar a ação tomada quando uma regra é violada em uma análise de código, escolha o mesmo campo de **Ação** para a regra e selecione um dos seguintes valores:  
  
     **Warn** \- gerencia um aviso.  
  
     **Error** \- gerencia um erro.  
  
     **None** \- desabilita a regra.  Esta ação é a mesma que removendo a regra do conjunto de regras.  
  
#### Para agrupar, filtrar, ou alterar os campos no publicador do conjunto de regras usando a barra de ferramentas do editor de regra  
  
-   Para expandir as regras em todos os grupos, escolha **Expandir Tudo**.  
  
-   Para recolher as regras em todos os grupos, escolha **Recolher Tudo**.  
  
-   Para alterar o campo que as regras são agrupadas por, escolha o mesmo campo da lista de **Agrupar por** .  Para exibir as regras não agrupadas, escolha **\<Nenhum\>**.  
  
-   Para adicionar ou remover campos em colunas de regra, escolha **Opções de Coluna**.  
  
-   Para ocultar as regras que não se aplicam à solução atual, escolha **Ocultar as regras que não se aplicam à solução atual**.  
  
-   Para alternar entre a exibição e ocultar as regras que são atribuídas a ação de erro, escolha **Mostrar regras que podem gerar erros de Análise de Código**.  
  
-   Para alternar entre a exibição e ocultar as regras que são atribuídas a ação de aviso, escolha **Mostrar regras que podem gerar avisos de Análise de Código**.  
  
-   Para alternar entre a exibição e ocultar as regras que são atribuídas a ação de **Nenhum** , escolha **Mostrar regras que não estão habilitadas**.  
  
-   Para adicionar ou remover conjuntos de regra padrão da Microsoft para o conjunto atual da regra, escolha **Adicionar ou remover conjuntos de regras filhas**.