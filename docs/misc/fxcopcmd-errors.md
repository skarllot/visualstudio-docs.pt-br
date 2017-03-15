---
title: "Erros (FxCopCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "erros de FxCopCmd"
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "susanno"
manager: "douge"
---
# Erros (FxCopCmd)
FxCopCmd não considera todos os erros fatais ser.  Se FxCopCmd tem informações suficientes para executar uma análise parcial, executa a análise e informa os erros ocorridos.  O código de erro, que é um número inteiro de 32 bits, contém uma combinação bit a bit de valores numéricos que correspondem aos erros.  
  
 A tabela a seguir descreve os códigos de erro retornados por FxCopCmd:  
  
|Erro|Valor numérico|  
|----------|--------------------|  
|Nenhum erro|0x0|  
|Erro de análise|0x1|  
|Exceções de regra|0x2|  
|Erro de carregamento do projeto|0x4|  
|Erro de assembly load|0x8|  
|Erro de carregamento da biblioteca de regra|0x10|  
|Erro de carregamento de importar relatório|0x20|  
|Erro de saída|0x40|  
|Erro da opção de linha de comando|0x80|  
|Erro de inicialização|0x100|  
|O assembly faz referência ao erro|0x200|  
|BuildBreakingMessage|0x400|  
|Erro desconhecido|0x1000000|  
  
 O erro de análise é retornado para erros fatais.  Indica que a análise não pôde ser concluída.  Quando aplicável, o código de erro também contém a causa subjacente de erro fatal.  As seguintes condições gerenciem erros fatais:  
  
-   A análise não pôde ser executada provocada por falta de entrada.  
  
-   A análise gerou uma exceção que não é tratada por FxCopCmd.  
  
-   O arquivo de projeto especificado não pôde ser localizado ou estiver danificado.  
  
-   A opção de saída não foi especificada ou o arquivo não poderia ser escrito.  
  
    > [!NOTE]
    >  O código de retorno “error” 0x200 de FxCopCmd referências de assembly por si só um aviso em vez de um erro.  Este código de retorno indica que as referências indiretas ausentes foram encontradas mas que poderia tratar as FxCopCmd.  É um aviso de que há uma possibilidade de que alguns resultados da análise poderiam ter sido comprometidos.  Considere o código de retorno de erros de referências assembly como um erro quando for combinado com qualquer outro código de retorno.  
  
## Consulte também  
 [Erros do aplicativo de análise do código](../code-quality/code-analysis-application-errors.md)