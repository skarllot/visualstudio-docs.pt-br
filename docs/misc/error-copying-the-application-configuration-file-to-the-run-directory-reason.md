---
title: "Erro ao copiar o arquivo de configura&#231;&#227;o do aplicativo para o diret&#243;rio de execu&#231;&#227;o. &lt; motivo &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cant_copy_appcfg_file"
ms.assetid: 15699a76-16ef-40a8-8ed4-5eef4d2c0e72
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro ao copiar o arquivo de configura&#231;&#227;o do aplicativo para o diret&#243;rio de execu&#231;&#227;o. &lt; motivo &gt;
O sistema do projeto não é possível copiar um arquivo App. config no diretório do qual o projeto está sendo executado. O processo de compilação falhará se esse erro ocorrer.  
  
 Esse erro ocorre apenas quando estiver criando um arquivo .exe.  
  
 O sistema de compilação tenta localizar um arquivo chamado App. config na pasta raiz do projeto. Esse arquivo, em seguida, será copiado no diretório de saída do projeto; seu nome no diretório de saída será *outputfile.*config.  
  
 Razões para esse erro incluem:  
  
-   espaço em disco insuficiente  
  
-   MAX\_PATH excedido  
  
 Também convém certificar\-se de que não há outra cópia do aplicativo em execução.  
  
## Consulte também  
 [PONTA como: modificar propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)