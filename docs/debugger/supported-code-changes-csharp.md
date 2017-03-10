---
title: "Altera&#231;&#245;es de c&#243;digo suportadas (C#) | Microsoft Docs"
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
  - "Editar e Continuar [C#], alterações de código com suporte"
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Altera&#231;&#245;es de c&#243;digo suportadas (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Editar e Continuar trata a maioria dos tipos de alterações de código dentro dos corpos do método.  A maioria das alterações fora dos corpos do método e algumas alterações dentro dos corpos do método, no entanto, não podem ser aplicadas durante a depuração.  Para aplicar essas alterações sem suporte, você deverá parar a depuração e reinicializar com uma versão atualizada do código.  
  
 As seguintes alterações não podem ser aplicadas ao código C\# durante uma sessão de depuração:  
  
-   As alterações na instrução atual ou qualquer outra instrução ativa.  
  
     As instruções ativas incluem todas as instruções, em funções na pilha de chamadas, que foram chamadas para acessar a instrução atual.  
  
     A instrução atual é marcada por um plano de fundo amarelo na janela de origem.  Outras instruções ativas são marcadas por um plano de fundo sombreado e são somente leitura.  Essas cores padrão podem ser alteradas na caixa de diálogo **Opções**.  
  
-   Alterando a assinatura de um tipo.  
  
-   Adicionando um método anônimo que captura uma variável que ainda não foram capturada antes.  
  
-   Alterando, removendo ou alterando atributos.  
  
-   Adicionando, removendo ou alterando políticas `using`.  
  
-   Adicionando `foreach`, `using`, ou `lock` em torno da instrução ativa.  
  
## Código não seguro  
 Alterações no código não seguro têm as mesmas limitações que alterações no código seguro, com uma restrição adicional: editar e continuar não dá suporte a alterações no código não seguro é encerrado dentro de um método que contém a`stackalloc`operador.  
  
## Exceções  
 Editar e continuar dá suporte a alterações para`catch`e`finally`bloqueia, exceto que adicionando um`catch`ou`finally`em torno da instrução ativa não é permitido.  
  
## Cenários sem suporte  
 Editar e Continuar não está disponível nos seguintes cenários de depuração:  
  
-   Depurando código LINQ em determinadas circunstâncias.  Para obter mais informações, consulte[Depurando LINQ](../debugger/debugging-linq.md).  
  
    -   Capturando uma variável que ainda não foram capturada antes.  
  
    -   Alterando o tipo de expressão de consulta \(por exemplo, selecione a \= \> Selecionar novo {A \= um}\)  
  
    -   Removendo um`where`que contém uma instrução ativa.  
  
    -   Removendo um`let`que contém uma instrução ativa.  
  
    -   Removendo um`join`que contém uma instrução ativa.  
  
    -   Removendo um`orderby`que contém uma instrução ativa.  
  
-   Depuração de modo misto \(nativo\/gerenciado\).  
  
-   Depuração de SQL.  
  
-   Depurando um despejo do Dr.  Watson.  
  
-   Editando o código após uma exceção sem tratamento, quando a opção "**Voltar para a pilha de chamadas em exceções não tratadas**" não está selecionada.  
  
-   Depurando um aplicativo inserido de tempo de execução.  
  
-   Depurando um aplicativo que tem **Anexar a** em vez de executando o aplicativo escolhendo **Iniciar** no menu **Depurar**.  
  
-   Depurando código otimizado.  
  
-   Depurando uma versão antiga do código depois que uma nova versão não é compilada devido a erros de compilação.  
  
## Consulte também  
 [Editar e continuar \(Visual C\#\)](../debugger/edit-and-continue-visual-csharp.md)   
 [Como usar Editar e Continuar \(C\#\)](../debugger/how-to-use-edit-and-continue-csharp.md)