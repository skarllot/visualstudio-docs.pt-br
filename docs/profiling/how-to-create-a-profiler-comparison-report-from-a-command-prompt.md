---
title: "Como criar um relatório de comparação de criador de perfil por meio de um prompt de comando | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7535876946968d79e88085eeff486303899b3cdf
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Como criar um relatório de comparação de criador de perfil a partir de um prompt de comando
Você pode gerar um relatório de Ferramentas de criação de perfil de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que compara os dados de desempenho de dois arquivos de dados de criação de perfil (.VSP /ou .VSPS). O relatório mostra as diferenças, regressões de desempenho e as melhorias que ocorreram de uma sessão de criação de perfil para a outra. Os valores no relatório apresentam o delta ou alteração, da linha de base do primeiro arquivo que você especificar. Esse delta é calculado determinando a diferença entre o valor antigo, que é o valor de linha de base e o valor do resultado da nova análise. As comparações de dados do criador de perfil podem ser baseadas nas funções no código, nos módulos no aplicativo, nas linhas, nos IPs (ponteiros de instrução) e nos tipos.  
  
 Para listar os identificadores dos campos e categorias de comparação, digite a seguinte linha de comando:  
  
 **VSPerfReport /querydifftables**  *VspFileName1* *VspFileName2*  
  
 Use a sintaxe a seguir para criar o relatório de comparação:  
  
 **VSPerfReport /diff**  `VspFileName1` *VspFileName2* [**/**`Options`]  
  
 Você pode adicionar opções da tabela a seguir para a linha de comando **VSPerfReport /diff**.  
  
|Opção|Descrição|  
|------------|-----------------|  
|**DiffThreshold:**[*Value*]|Ignore a diferença se ela estiver abaixo desse valor de limite de percentual. Além disso, novos dados com valores abaixo desse limite não aparecerão.|  
|**DiffTable:** *TableName*|Use esta tabela para comparar arquivos. Por padrão, a tabela de funções é usada. Especifique o identificador que está listado em **VSPerfReport /querydifftables**.|  
|**DiffColumn:** *ColumnName*|Use essa coluna para comparar valores. Por padrão, a coluna de porcentagem de amostras exclusivas é usada. Especifique o identificador que está listado em **VSPerfReport /querydifftables**.|
