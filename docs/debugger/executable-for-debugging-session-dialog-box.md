---
title: "Caixa de di&#225;logo Execut&#225;vel para Sess&#227;o de Depura&#231;&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.exefordebug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, Caixa de diálogo Executável para Sessão de Depuração"
  - "DLLs, depuração"
  - "arquivos executáveis, especificando durante a depuração"
  - "Caixa de diálogo Executável para Sessão de Depuração"
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Caixa de di&#225;logo Execut&#225;vel para Sess&#227;o de Depura&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Essa caixa de diálogo aparece quando você tenta depurar uma DLL para a qual nenhum executável está especificado.  O Visual Studio não pode iniciar uma DLL diretamente.  Em vez disso, ele iniciará o executável especificado.  Você pode depurar a DLL quando ela for chamada pelo executável.  
  
 **Nome de arquivo executável**  
 Digite o nome do caminho para um executável que chama a DLL que você está depurando.  
  
 **URL em que o projeto pode ser acessado \(somente Servidor ATL\)**  
 Se você estiver depurando um DLL do servidor ATL, digite a URL onde o projeto pode ser localizado.  
  
 Uma vez inseridas, essas configurações são armazenadas nas Páginas de Propriedades do projeto, de modo que você não precise inseri\-las novamente para sessões de depuração subsequentes.  Se você precisar alterar as configurações, poderá abrir as Páginas de Propriedades e alterar os valores.  Para obter mais informações sobre como especificar um executável para a sessão de depuração, consulte [Depurando DLLs](../Topic/How%20to:%20Debug%20Native%20DLLs.md).  
  
## Consulte também  
 [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)