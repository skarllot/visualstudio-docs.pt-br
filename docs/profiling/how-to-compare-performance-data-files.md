---
title: Como comparar arquivos de dados de desempenho | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8e02119f15f8505af519e2bd8153e59f5f0aee4a

---
# <a name="how-to-compare-performance-data-files"></a>Como comparar arquivos de dados de desempenho
Você pode comparar os resultados de dois arquivos de dados de criadores de perfil diferentes (.vsp ou .vsps), criando um relatório ou uma exibição de comparação ("Diff"). A comparação mostra as diferenças, regressões de desempenho e as melhorias que ocorreram de uma sessão de criação de perfil para a outra.  
  
 O relatório de Comparação apresenta uma exibição de tabela dos dados. A tabela apresenta o delta ou a alteração da linha de base. Isso é calculado determinando a diferença entre o valor antigo, o valor de linha de base e o valor do resultado da nova análise.  
  
 As comparações de dados do criador de perfil podem ser baseadas nas funções no código, nos módulos no aplicativo, nas linhas, nos IPs (ponteiros de instrução) e nos tipos.  
  
 Um limite pode ser definido para reduzir o ruído e filtrar na exibição de tabela os dados das linhas que não tenham sido alteradas por uma quantidade especificada.  
  
### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Para criar uma exibição de arquivo de comparação para um projeto no Gerenciador de Desempenho  
  
1.  No **Gerenciador de Desempenho**, em **Relatórios**, selecione o arquivo de relatório .vsp ou .vsps que você deseja usar como valores de linha de base para a comparação.  
  
2.  Selecione os arquivos de relatório .vsp ou .vsps que você deseja comparar.  
  
3.  Clique com o botão direito do mouse em um dos arquivos selecionados e, em seguida, clique em **Comparar Relatórios**.  
  
### <a name="to-compare-values"></a>Para comparar valores  
  
1.  Selecione a guia **Relatório de Comparação** na janela de Exibição de Relatório.  
  
2.  Na lista suspensa **Tabela**, selecione a função ou os módulos para comparar.  
  
3.  Na lista suspensa **Coluna**, selecione o valor que você deseja comparar.  
  
4.  (opcional) Digite um valor para **Limite**.  
  
5.  Clique em **Aplicar**.  
  
### <a name="to-compare-report-files"></a>Para comparar arquivos de relatório  
  
1.  No menu **Analisar**, selecione **Comparar Relatórios de Desempenho**.  
  
2.  Na janela **Selecionar arquivos de análise para comparação**, procure e selecione o **Arquivo de Linha de Base** de análise (.vsp ou .vsps) e o **Arquivo de Comparação** (.vsp ou .vsps).  
  
3.  Clique em **OK**.


<!--HONumber=Feb17_HO4-->


