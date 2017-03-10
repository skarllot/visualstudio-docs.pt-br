---
title: "Especificadores de formato em C# | Microsoft Docs"
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
  - "CSharp"
helpviewer_keywords: 
  - "depurador, especificadores de formato reconhecidos por"
  - "expressões [C#], formatando valores"
  - "especificadores de formato, depurador"
  - "QuickWatch (caixa de diálogo), especificadores de formato em C#"
  - "QuickWatch (caixa de diálogo), usando especificadores de formato"
  - "especificadores"
  - "especificadores, formato de variável de inspeção"
  - "símbolos, formatação de variável de inspeção"
  - "variáveis [depurador], símbolos de variável de inspeção"
  - "símbolos de variável de inspeção"
  - "Janela Inspecionar, especificadores de formato em C#"
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Especificadores de formato em C# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode alterar o formato no qual um valor é exibido no **inspeção** janela usando especificadores de formato. Você também pode usar especificadores de formato no **imediato** janela, o **comando** janela e até mesmo em janelas de origem. Se você pausar em uma expressão nessas janelas, o resultado será exibido em um DataTip. DataTips refletirão o especificador de formato na tela DataTip.  
  
 Para usar um especificador de formato, digite a expressão seguida por uma vírgula. Após a vírgula, adicione o especificador apropriado.  
  
## Usando especificadores de formato  
 Se você tiver o código a seguir:  
  
```  
{ int my_var1 = 0x0065; int my_var2 = 0x0066; int my_var3 = 0x0067; }  
```  
  
 Adicionar o `my_var1` variável à janela Inspeção \(durante a depuração, **Debug \/ Windows \/ Assista \/ Assista 1**\) e defina a exibição hexadecimal \(no **inspeção** janela, a variável e selecione **Exibir Hexadecimal**\). Agora o **inspeção** janela mostra que ela contém o valor 0x0065. Para ver esse valor é expresso como um inteiro decimal em vez de um inteiro hexadecimal, na coluna Nome, após o nome da variável, adicione o especificador de formato decimal: **, d**. A coluna valor agora mostra o valor decimal 101  
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## Especificadores de formato  
 A tabela a seguir mostra os especificadores de formato em c\# reconhecidos pelo depurador.  
  
|Especificador|Formato|Valor original de inspeção|Exibe|  
|-------------------|-------------|--------------------------------|-----------|  
|CA|Forçar a avaliação de uma expressão. Isso pode ser útil quando a avaliação implícita das propriedades e das chamadas de função implícitas é desativada. Consulte [Efeitos colaterais e expressões](../Topic/Side%20Effects%20and%20Expressions.md).|Mensagem "avaliação da função implícita está desativada pelo usuário"|\< valor \>|  
|d|inteiro decimal|0x0065|101|  
|dinâmica|Exibe o objeto especificado usando uma exibição dinâmica|Exibe todos os membros do objeto, incluindo o modo de exibição dinâmico|Exibe somente a visualização dinâmica|  
|h|inteiro hexadecimal|61541|0x0000F065|  
|Nq|cadeia de caracteres sem aspas|"Minha cadeia de caracteres"|Minha cadeia de caracteres|  
|oculto|Exibe todos os membros públicos e não público|Exibe os membros públicos|Exibe todos os membros|  
|bruto|Exibe o item como ele aparece no nó bruto do item. Válido somente em objetos proxy.|Dicionário \< T \>|Exibição bruta do Dictionary \< T \>|  
|resultados|Usado com uma variável de um tipo que implemente IEnumerable ou IEnumerable \< T \>, geralmente o resultado de uma expressão de consulta. Exibe somente os membros que contém o resultado da consulta.|Exibe todos os membros.|Exibe os membros que atendam as condições da consulta.|  
  
## Consulte também  
 [Inspeção e Windows QuickWatch](../debugger/watch-and-quickwatch-windows.md)   
 [Janelas de variável](../Topic/Variable%20Windows.md)