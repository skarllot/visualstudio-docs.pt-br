---
title: "Erros e avisos de Editar e Continuar (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ENC2001"
  - "ENC1006"
  - "ENC2008"
  - "ENC1009"
  - "ENC1002"
  - "ENC2002"
  - "ENC1011"
  - "ENC1003"
  - "ENC1004"
  - "ENC1008"
  - "ENC1013"
  - "ENC2005"
  - "ENC1010"
  - "ENC2004"
  - "ENC1007"
  - "ENC1005"
  - "ENC2006"
  - "ENC1001"
  - "ENC2007"
  - "ENC2003"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Editar e Continuar [C++], erros e avisos"
  - "erros [C++], Editar e continuar"
  - "erros [depurador], Editar e continuar"
ms.assetid: b5c5e25c-7ca4-4ca9-b91e-e8882de44dae
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "susanno"
manager: "douge"
---
# Erros e avisos de Editar e Continuar (C++)
[!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)] Editar e Continuar permite parar a execução do programa no modo de interrupção, fazer alterações no código de execução e, em seguida, retomar a execução do programa com as alterações recém\-inseridas.  
  
 As edições declarativas de código que afetam a estrutura pública de uma classe são proibidas em geral, e algumas edições que você pode fazer em um método, corpo da propriedade ou declarações privadas dentro de uma classe não são permitidas.  Sempre que possível, Editar e Continuar marca o código que não pode ser editado como cinza claro e exibe uma mensagem de erro.  Para obter mais informações sobre as edições com suporte em Editar e Continuar para [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)], consulte [Editar e continuar \(Visual C\+\+\)](../debugger/edit-and-continue-visual-cpp.md).  
  
 Os erros e avisos de Editar e Continuar podem ser resolvidos de uma das seguintes maneiras:  
  
|Resolução|Números de mensagem de erro e aviso|  
|---------------|-----------------------------------------|  
|Pare a depuração, aplique novamente suas alterações e retome a depuração.|1001, 1002, 1003, 1004, 1005, 1006, 1007, 1008, 1010, 1013, 2003, 2005 Para obter uma lista de erros e as mensagens de aviso nesta categoria, consulte [Reiniciar mensagens de depuração](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_RestartDebuggingMessages).|  
|No menu **Editar**, escolha **Desfazer** e continue a depuração com o código inalterado.<br /><br /> \-Ou\-<br /><br /> Pare a depuração, aplique novamente suas alterações e retome a depuração.|1009, 1011 Para obter uma lista de erros e as mensagens de aviso nesta categoria, consulte [Desfazer ou interromper mensagens](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_UndoOrStopMessages).|  
|Continue a depuração.  Suas alterações serão ignoradas na primeira vez que o código for atingido, mas serão aplicadas em chamadas subsequentes.|2001, 2002, 2004.  Para obter uma lista de erros e as mensagens de aviso nesta categoria, consulte [Aplicar em mensagens das próximas chamadas](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_ApplyAtNextCallMessages).|  
|Execute qualquer outra ação, por exemplo, redefinir pontos de interrupção ou recriar os módulos com a versão atual do [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)].|2007, 2008.  Para obter uma lista de erros e as mensagens de aviso nesta categoria, consulte [Mensagens de outras ações exigidas](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_OtherActionRequiredMessages).|  
  
##  <a name="BKMK_RestartDebuggingMessages"></a> Reiniciar mensagens de depuração  
 As mensagens de erro a seguir devem ser resolvidas interrompendo a sessão de depuração atual, reaplicando as edições realizadas e, em seguida, reiniciando a sessão de depuração.  
  
|||  
|-|-|  
|1001|Não é possível atualizar a conversão para o símbolo: *symbol* \(loc: *location*, thunk: *address*\)|  
|1002|O símbolo de dados mudou: símbolo \(*symbol*\)|  
|1003|Não é possível mapear a conversão para a nova função: *function*|  
|1004|Não é possível abrir o PDB para empacotar tipos: *pdb* \(pdb\)|  
|1005|O símbolo foi renomeado, removido ou modificado: *symbol*|  
|1006|Uma variável global ou estática foi adicionada, renomeada, removida ou alterada para tipo de dados ou inicialização: *symbol* \(referenciado por: *module*\)|  
|1007|Símbolo não definido: *symbol* \(referenciado por: *module*\)|  
|1008|Não é possível executar a inicialização de tempo de execução exigida pelo objeto carregado durante a edição: *module*|  
|1010|Uma variável global ou estática foi adicionada: *variable referenced in file*|  
|1013|O depurador ficou sem memória ao aplicar alterações de código|  
|2003|A alteração da posição de código pode causar erros de manipulação de exceção ou de destruição de variável: *function*|  
|2005|Nova origem contribui para o código.  As informações de número de linha do depurador podem ser afetada: função \(*function*\)|  
  
##  <a name="BKMK_UndoOrStopMessages"></a> Desfazer ou interromper mensagens  
 As mensagens de erro a seguir podem ser resolvidas interrompendo a sessão de depuração atual, reaplicando as edições realizadas e, em seguida, reiniciando a sessão de depuração.  
  
-   No menu Editar, clique em Desfazer.  Você pode retomar a depuração, mas as edições não serão aplicadas.  
  
     \-Ou\-  
  
-   Pare a depuração, aplique novamente as edições e reinicie a depuração.  
  
|||  
|-|-|  
|1009|Uma variável global ou estática foi excluída: *variable referenced in file*|  
|1011|Uma variável global ou estática foi alterada: *variable referenced in file*|  
  
##  <a name="BKMK_ApplyAtNextCallMessages"></a> Aplicar em mensagens das próximas chamadas  
 Você pode continuar a sessão de depuração quando uma das seguintes mensagens de aviso for exibida.  As edições não serão aplicadas quando o código for chamado na primeira vez após a edição; as edições são aplicadas em todas as chamadas subsequentes ao código.  
  
|||  
|-|-|  
|2001|Não é possível encontrar a variável local ou o tipo de dados de variável alterada símbolo \(*symbol*\)|  
|2002|A variável ou a nova variável local excluída exige construção ou destruição: : símbolo \(*symbol*\)|  
|2004|Não é possível lidar com a adição ou com a remoção de uma variável local com um nome já definido mais de uma vez: símbolo \(*symbol*\)|  
  
##  <a name="BKMK_OtherActionRequiredMessages"></a> Mensagens de outras ações exigidas  
 A ação necessária para resolver essas mensagens é descrita depois do texto da mensagem.  
  
|||  
|-|-|  
|2007|Não foi possível mover alguns pontos de interrupção definidos na janela de desmontagem.<br /><br /> Para resolver esse problema, redefina os pontos de interrupção afetados.|  
|2008|Não foi possível carregar símbolos de depuração para o arquivo *file* no módulo *module*<br /><br /> Para resolver esse problema, recompile o módulo especificado com a versão atual do [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].|  
  
## Consulte também  
 [Editar e continuar \(Visual C\+\+\)](../debugger/edit-and-continue-visual-cpp.md)   
 [Editar e continuar](../debugger/edit-and-continue.md)