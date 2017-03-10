---
title: "Caixa de di&#225;logo Mensagem de Erro de Editar e Continuar | Microsoft Docs"
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
  - "vs.debug.ENC.SupportedButNotAvaiable"
  - "vs.debug.ENC.CannotEditWhileException"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Caixa de diálogo Mensagem de Erro de Editar e Continuar"
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Caixa de di&#225;logo Mensagem de Erro de Editar e Continuar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Essa caixa de diálogo aparece quando você está depurando em uma linguagem que oferece suporte a Editar e Continuar, mas **Editar e Continuar** não está disponível para o tipo de alterações de código que você fez.  A mensagem de erro dentro da caixa fornece uma explicação mais detalhada.  As possíveis razões para ver essa caixa de diálogo incluem:  
  
-   Você tentou editar o código gerenciado quando a depuração não gerenciada foi habilitada.  Editar e Continuar não funcionam com depuração de modo misto.  
  
-   Você tentou editar o código do SQL Server.  
  
-   Você tentou editar o código durante a depuração de um Dr.  Watson.  
  
-   Você tentou editar o código após uma exceção sem tratamento ocorrida e a opção "**Voltar para a pilha de chamadas em exceções não tratadas**" não estava selecionada.  
  
-   Você tentou editar o código ao depurar um aplicativo inserido de tempo de execução.  
  
-   Você tentou editar o código em um programa que você anexou em vez de a partir do menu **Depurar**.  
  
-   Você tentou editar o código otimizado.  
  
-   Você tentou editar o código gerenciado quando o destino é um aplicativo de 64 bits.  Se você desejar usar Editar e Continuar, deve definir o destino como x86. \(*Project* **Propriedades**, guia **Compilar**, configuração **Compilador Avançado**.\).  
  
-   Você tentou editar o código em um assembly que foi modificado durante a depuração e foi recarregado.  
  
-   Você tentou editar o código em um assembly que não foi carregado.  
  
-   Você iniciou a depuração de uma versão antiga do aplicativo \(já que a nova versão tem erros de compilação\).  
  
-   Você tentou editar o código durante a execução.  
  
## Lista UIElement  
 **OK**  
 Saia da caixa de diálogo e cancele a tentativa de edição imediatamente anterior.  
  
## Consulte também  
 [Alterações de código suportadas \(C\+\+\)](../debugger/supported-code-changes-cpp.md)