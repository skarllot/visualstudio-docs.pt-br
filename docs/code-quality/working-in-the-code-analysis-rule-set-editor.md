---
title: "Trabalhando no Editor de Conjunto de Regras de An&#225;lise do C&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.ruleseteditor"
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Trabalhando no Editor de Conjunto de Regras de An&#225;lise do C&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O editor ajustado da regra de análise de código habilita a especificar as regras que são incluídas em um conjunto de regra personalizada e para especificar a ação.  Você também pode especificar a ação a ser tomada quando a análise de código encontrar uma violação da regra.  
  
|Ação|Descrição|  
|----------|---------------|  
|**Warning**|Gerencie um aviso na janela de **Lista de Erros** .|  
|**Error**|Gerencie um erro na janela de **Lista de Erros** .|  
|**None**|Desabilita a regra.|  
  
 O editor exibe as regras em uma estrutura de árvore que agrupa as regras por um campo do conjunto de regras que você especifica.  Para adicionar ou remover regras de um conjunto de regras, execute uma ou mais das seguintes etapas:  
  
-   Marque ou desmarque a caixa de seleção do nó do grupo para adicionar ou remover todas as regras no grupo.  Quando você seleciona um grupo, todas as regras são definidas para a ação de **Aviso** .  
  
-   Clique no campo de **Ação** de um grupo, e especifique a ação a ser aplicado a todas as regras no grupo.  
  
-   Marque ou desmarque a caixa de seleção para uma regra individual.  Quando você seleciona a caixa de seleção para uma regra, a regra está definida como a ação de aviso.  
  
## Barra de ferramentas do editor de regra  
 Você pode usar a barra de ferramentas do editor do conjunto de regras para agrupar, filtrar, e pesquisar os dados que são exibidos na grade de definição da regra.  
  
 A tabela a seguir descreve os controles na barra de ferramentas do editor do conjunto de regra.  
  
|Controle da barra de ferramentas|Descrição|  
|--------------------------------------|---------------|  
|**Expandir tudo**|Mostra as regras em todos os grupos.|  
|**Recolher tudo**|Ocultar as regras em todos os grupos.|  
|**Agrupar por**|Especifica o campo pelo qual as regras são agrupadas.  Clique **\<Nenhum\>** para mostrar as regras sem grupos.|  
|**Opções de coluna**|Especifica os campos de regra para exibir.|  
|**Ocultar as regras que não se aplicam à solução atual**|Mostra ou oculta as regras que não são do mesmo tipo de destino que a solução.|  
|**Mostrar regras que podem gerar erros de análise de código**|Mostra ou oculta as regras que são atribuídas a ação de erro.|  
|**Mostrar regras que podem gerar avisos de análise de código**|Mostra ou oculta as regras que são atribuídas a ação de aviso.|  
|**As regras de apresentação que não estão habilitadas**|Mostra ou oculta as regras que são atribuídas a nenhum a ação.|  
|**Adicionar ou remover conjuntos filhos de regra**|Adiciona ou remove as regras nos clusters selecionados da regra.|  
|**Regras de pesquisa**|Pesquisa todos os valores de campo pela cadeia de caracteres que você especifica.|  
  
## Campos de conjunto da regra  
 Os campos de conjunto da regra exibem informações sobre uma regra definida e podem ser usados para classificar e agrupar a lista da regra.  Para exibir ou ocultar os campos, clique em **Opções de Coluna** na barra de ferramentas do editor de regra e, marque ou desmarque as caixas de seleção de campos para mostrar ou ocultar.  
  
 A tabela a seguir descreve campos de um conjunto de regras.  
  
|Campo|Descrição|  
|-----------|---------------|  
|**ID**|O identificador da regra.|  
|**Category**|Além de sua associação em conjuntos de regra, as regras de análise de código também são agrupadas por categoria.  Para obter mais informações, consulte [Avisos da análise de código para código gerenciado](../code-quality/code-analysis-for-managed-code-warnings.md).|  
|**Name**|O título da regra.|  
|**Namespace**|O namespace da regra.|  
|**Target Type**|Indica se a regra for para nativo, gerenciada, ou código da base de dados.|  
|**Action**|A ação executada quando a regra é violada em uma execução do código.<br /><br /> **Warning** \- gerencia um aviso.<br /><br /> **Error** \- gerencia um erro.<br /><br /> **None** \- desabilita a regra.<br /><br /> Você pode editar o campo de ação.  Defina o valor como nenhum é o mesmo que desmarcando a caixa de seleção para a regra.|  
|**Source Rule Sets**|A regra definida que contém a regra.|  
  
## Conjuntos de regras de classificação e de filtragem  
 Os cabeçalhos da coluna da grade de definição de regra, você pode classificar e filtrar as regras pelos valores do campo.  
  
-   Para classificar as listas do conjunto de regra, clique no cabeçalho da coluna de campo pelo qual você deseja classificar.  Se os conjuntos de regras são agrupados, cada grupo é classificado individualmente.  
  
-   Para filtrar os conjuntos de regra pelo valor de um campo, clique no botão de filtro no cabeçalho da coluna do campo pelo qual você deseja filtrar.  Marque as caixas de seleção dos valores que você deseja mostrar, e desmarque as caixas de seleção dos valores que você deseja ocultar.