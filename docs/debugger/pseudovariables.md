---
title: "Pseudovari&#225;veis | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurando [Visual Studio], pseudovariáveis"
  - "pseudovariáveis"
  - "Janela Inspecionar, pseudovariáveis"
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Pseudovari&#225;veis
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

As pseudovariáveis são termos usados para exibir determinadas informações em uma janela de variável ou na caixa de diálogo do **QuickWatch**.  Você pode inserir um pseudovariável da mesma maneira que incorporaria uma variável normal.  As pseudovariáveis não são variáveis, no entanto, e não correspondem aos nomes de variáveis em seu programa.  
  
## Exemplo  
 Suponha que você está escrevendo um aplicativo de código nativo e quer consultar o número de identificadores alocados em seu aplicativo.  Na janela **Inspeção**, você pode inserir a seguinte pseudovariável na coluna **Nome** e então pressionar Return para avaliá\-la:  
  
```  
$handles  
```  
  
 em código nativo, você pode usar as pseudovariáveis mostradas na tabela:  
  
|Pseudovariável|Função|  
|--------------------|------------|  
|`$err`|Exibe o último conjunto de valores de erro com a função SetLastError.  O valor que é exibido representa o que seria retornado pela função GetLastError.<br /><br /> Use `$err,hr` para ver o formulário decodificado deste valor.  Por exemplo, se o erro mais recente fosse 3, `$err,hr` exibiria `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|  
|`$handles`|Exibe o número de manipuladores alocados em seu aplicativo.|  
|`$vframe`|Exibe o endereço do quadro de pilha atual.|  
|`$tid`|Exibe a ID do thread para o thread atual.|  
|`$env`|Exibe o bloco de ambiente no visualizador de cadeia de caracteres.|  
|`$cmdline`|Exibe a cadeia de caracteres de linha de comando que iniciou o programa.|  
|`$pid`|Exibe a identificação do processo.|  
|`$` *registername*<br /><br /> ou<br /><br /> `@` *registername*|Exibe o conteúdo do registro *registername*.<br /><br /> Normalmente, você pode exibir conteúdo do registro simplesmente inserindo o nome do registro.  A única vez que você precisa usar essa sintaxe é quando o nome do registro sobrecarrega um nome de variável.  Se o nome do registro for igual ao nome da variável no escopo atual, o depurador interpretará o nome como um nome de variável.  É nesse momento que `$`*registername* ou `@`*registername* é útil.|  
|`$clk`|Exibe a hora em ciclos de relógio.|  
|`$user`|Exibe uma estrutura com informações de conta para a conta que executa o aplicativo.  Por motivo de segurança, as informações de senha não são exibidas.|  
|`$exceptionstack`|Exibe o rastreamento de pilha da exceção atual de Tempo de Execução do Windows.  O `$ exceptionstack` funciona apenas em aplicativos da Store que estão em execução no Windows 8.1 ou posterior.  `$ exceptionstack` não tem suporte para exceções de C\+\+ e SHE|  
|`$ReturnValue`|Mostra o valor retornado de um método .NET Framework.  Consulte [Examinar valores de retorno de chamadas de método](../Topic/Examine%20return%20values%20of%20method%20calls.md)|  
  
 No C\# e no Visual Basic, você pode usar as pseudovariáveis mostradas na tabela:  
  
|Pseudovariável|Função|  
|--------------------|------------|  
|`$exception`|Exibe informações sobre a última exceção.  Se nenhuma exceção tiver ocorrido, a avaliação `$exception` exibirá uma mensagem de erro.<br /><br /> Somente no Visual C\#, quando o Assistente de Exceção for desabilitado, `$exception` será automaticamente adicionado à janela **Locais** quando ocorrer uma exceção.|  
|`$user`|Exibe uma estrutura com informações de conta para a conta que executa o aplicativo.  Por motivo de segurança, as informações de senha não são exibidas.|  
  
 No Visual Basic, você pode usar as pseudovariáveis mostradas na seguinte tabela:  
  
|Pseudovariável|Função|  
|--------------------|------------|  
|`$delete` ou `$$delete`|Exclui uma variável implícita criada na janela **Imediato**.  A sintaxe é `$delete,` *variável* ou `$delete,` *variável*`.`|  
|`$objectids` ou `$listobjectids`|Exibe todas as IDs de objetos como filhos da expressão especificada.  A sintaxe é `$objectid,` *expressão* ou `$listobjectids,` *expressão*`.`|  
|`$` *N* `#`|Exibe o objeto com a ID de objeto igual a *N*.|  
|`$dynamic`|Exibe o nó especial **Modo de Exibição Dinâmico** para um objeto que implementa `IDynamicMetaObjectProvider`.  Interface.  A sintaxe é `$dynamic,` *object*.  Esse recurso se aplica somente ao código que usa o .NET Framework versão 4.  Consulte [Exibição dinâmica](../Topic/Dynamic%20View.md).|  
  
## Consulte também  
 [Inspeção e Windows QuickWatch](../debugger/watch-and-quickwatch-windows.md)   
 [Janelas de variável](../Topic/Variable%20Windows.md)