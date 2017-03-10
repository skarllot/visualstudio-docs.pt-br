---
title: "Como criar um relat&#243;rio de compara&#231;&#227;o de criador de perfil a partir de um prompt de comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como criar um relat&#243;rio de compara&#231;&#227;o de criador de perfil a partir de um prompt de comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode gerar um relatório de Ferramentas de Criação de Perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que compara os dados de desempenho de dois arquivos de dados de perfil \(.VSP ou .VSPS\).  O relatório mostra a mostra as diferenças, as regressões de desempenho e as melhorias que ocorreram de uma sessão de criação de perfil para outra.  Os valores no relatório apresentam a variação, ou modificação, da linha de base do primeiro arquivo que você especificar.  Esta variação é calculada determinando a diferença entre o valor antigo, que é o valor da linha de base, e o valor do resultado de nova análise.  As comparações de dados do criador de perfis podem ser baseadas nas funções no código, em módulos no aplicativo, linhas, ponteiros de declaração \(IPs, em inglês\) e tipos.  
  
 Para listar os identificadores de categorias e campos de comparação, digite a seguinte linha de comando:  
  
 **VSPerfReport \/querydifftables**  *VspFileName1* *VspFileName2*  
  
 Use a seguinte sintaxe para criar relatórios de comparação:  
  
 **VSPerfReport \/diff**  `VspFileName1` *VspFileName2* \[**\/**`Options`\]  
  
 Você pode adicionar opções de tabela a seguir para a linha de comando de **VSPerfReport \/diff** .  
  
|Opção|Descrição|  
|-----------|---------------|  
|**DiffThreshold:**\[*Value*\]|Desconsidere a diferença se ela estiver abaixo de esse valor limite de percentual.  Além disso, os novos dados com valores que estão abaixo de esse limite não aparecerão.|  
|**DiffTable:** *TableName*|Use esta tabela para comparar arquivos.  Por padrão, a tabela de funções é usada.  Especificar o identificador que está listado em **VSPerfReport \/querydifftables**.|  
|**DiffColumn:** *ColumnName*|Use esta coluna para comparar valores.  Por padrão, a coluna de porcentagem exemplos exclusivos é usada.  Especificar o identificador que está listado em **VSPerfReport \/querydifftables**.|