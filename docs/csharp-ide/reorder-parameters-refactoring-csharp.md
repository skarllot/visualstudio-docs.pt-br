---
title: "Reorder Parameters Refactoring (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.reorder"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactoring [C#], Reorder Parameters"
  - "Reorder Parameters refactoring [C#]"
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Reorder Parameters Refactoring (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`Reorder Parameters`é um Visual C\# operação de refatoração que oferece uma maneira fácil para alterar a ordem dos parâmetros para métodos, indexadores e delegados.  `Reorder Parameters`Altera a declaração, e em quaisquer locais onde o membro é chamado, os parâmetros são reorganizados para refletir a nova ordem.  
  
 Para executar o `Reorder Parameters` operação, coloque o cursor sobre ou próximo a um método, indexador ou representante.  Quando o cursor estiver na posição, chamar o `Reorder Parameters` operação pressionando o atalho de teclado ou clicando no comando no menu de atalho.  
  
> [!NOTE]
>  Você não pode reordenar o primeiro parâmetro em um método de extensão.  
  
### Para reordenar parâmetros  
  
1.  Criar uma biblioteca de classe denominada `ReorderParameters`e, em seguida, substitua `Class1` com o seguinte exemplo de código.  
  
    ```c#  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Coloque o cursor na `MethodB`, na declaração do método ou a chamada do método.  
  
3.  Sobre o  **Refactor** menu, clique em  **Reordenar parâmetros**.  
  
     O  **Reordenar parâmetros** caixa de diálogo aparece.  
  
4.  No  **Reordenar parâmetros** caixa de diálogo, selecione `int i` na  **parâmetros de** lista e, em seguida, clique no botão para baixo.  
  
     Como alternativa, você pode arrastar `int i` depois de `bool b` na  **parâmetros de** lista.  
  
5.  No  **Reordenar parâmetros** caixa de diálogo, clique em  **OK**.  
  
     Se o  **Visualizar alterações de referência** opção é selecionada no  **Reordenar parâmetros** caixa de diálogo, o  **Visualizar alterações \- reordenar parâmetros** caixa de diálogo será exibida.  Ele fornece uma visualização das alterações na lista de parâmetros para `MethodB` em que a assinatura e a chamada do método.  
  
    1.  Se o  **Visualizar alterações \- reordenar parâmetros** caixa de diálogo for exibida, clique em  **Aplicar**.  
  
         Neste exemplo, a declaração de método e o método todos os sites de chamada para `MethodB` são atualizados.  
  
## Comentários  
 Você pode reordenar os parâmetros de uma declaração de método ou uma chamada de método.  Posicione o cursor no ou ao lado da declaração de método ou delegate, mas não no corpo.  
  
## Consulte também  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)