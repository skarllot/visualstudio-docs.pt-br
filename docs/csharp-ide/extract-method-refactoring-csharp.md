---
title: "Refatora&#231;&#227;o Extrair M&#233;todo (C#) | Microsoft Docs"
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
  - "vs.csharp.refactoring.extractmethod"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Refatoração [c#], extrair método"
  - "operação de refatoração Extrair Método [C#]"
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
caps.handback.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Refatora&#231;&#227;o Extrair M&#233;todo (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Extrair método** é uma operação de refatoração que oferece uma maneira fácil para criar um novo método de um fragmento de código em um membro existente.  
  
 Usando  **Extract Method**, você pode criar um novo método, extraindo uma seleção de código de dentro do bloco de código de um membro existente.  O novo método extraído contém o código selecionado e o código selecionado no membro existente é substituído por uma chamada para o novo método.  Transformando um fragmento de código em seu próprio método permite que você rapidamente e reorganizar com precisão o código para melhorar a legibilidade e reutilização.  
  
 **Extrair método** tem os seguintes benefícios:  
  
-   Incentiva práticas de codificação melhor, enfatizando a métodos discretos e reutilizáveis.  
  
-   Incentiva autodescritivo código por meio de organização em boas condições.  
  
     Quando nomes descritivos são métodos utilizados e de alto nível, podem ler mais como uma série de comentários.  
  
-   Incentiva a criação de métodos mais refinados para simplificar a substituição.  
  
-   Reduz a duplicação de código.  
  
### Para usar o Extract Method  
  
1.  Crie um aplicativo de console chamado  `ExtractMethod`e, em seguida, substitua `Program` com o seguinte exemplo de código.  
  
    ```c#  
    class A  
    {  
        const double PI = 3.141592;  
  
        double CalculatePaintNeeded(double paintPerUnit, double radius)  
        {  
            // Select any of the following:  
            // 1. The entire next line of code.  
            // 2. The right-hand side of the next line of code.  
            // 3. Just "PI *" of the right-hand side of the next line  
            //    of code (to see the prompt for selection expansion).  
            // 4.  All code within the method body.  
            // ...Then invoke Extract Method.  
  
            double area = PI * radius * radius;  
  
            return area / paintPerUnit;  
        }  
    }  
    ```  
  
2.  Selecione o fragmento de código que você deseja extrair:  
  
    ```c#  
    double area = PI * radius * radius;  
  
    ```  
  
3.  Sobre o  **Refactor** menu, clique em  **Extract Method**.  
  
     A caixa de diálogo **Extract Method** aparece.  
  
     Como alternativa, você também pode digitar o atalho de teclado CTRL \+ R, M para exibir o  **Extract Method** caixa de diálogo.  
  
     Você pode também direito selecionado de código, aponte para  **Refactor**e, em seguida, clique em  **Extract Method** para exibir o  **Extract Method** caixa de diálogo.  
  
4.  Especifique um nome para o novo método, como  `CircleArea`, no  **Nome do novo método** caixa.  
  
     Uma visualização da nova assinatura de método exibe em  **Visualizar assinatura do método**.  
  
5.  Clique em **OK**.  
  
## Comentários  
 Quando você usa o  **Extract Method** de comando, o novo método é inserido após o membro de origem na mesma classe.  
  
## Tipos parciais  
 Se a classe é um tipo parcial, em seguida,  **Extract Method** gera o novo método imediatamente após o membro de origem.  **Extrair método** determina a assinatura do novo método, criando um método estático quando nenhum dado de ocorrência é referenciado pelo código no novo método.  
  
## Parâmetros de tipo genérico  
 Quando você extrai um método que possui um parâmetro de tipo genérico irrestrita, o código gerado não adicionará o `ref` modificador para esse parâmetro, a menos que um valor é atribuído a ele.  Se o método extraído oferecerá suporte a tipos de referência como o argumento de tipo genérico, você deve adicionar manualmente o `ref` modificador ao parâmetro na assinatura do método.  
  
## Métodos anônimo  
 Se você tentar extrair parte de um método anônimo que inclui uma referência a uma variável local que está declarada ou referenciada fora do método anônimo, em seguida, Visual Studio irá avisá\-lo sobre possíveis alterações semânticas.  
  
 Quando um método anônimo usa o valor de uma variável local, o valor é obtido no momento em que o método anônimo é executado.  Quando um método anônimo é extraído para outro método, o valor da variável local é obtido no momento da chamada para o método extraído.  
  
 O exemplo a seguir ilustra esta alteração de semântica.  Se esse código é executado, em seguida, **11** será impressa no console.  Se você usar  **Extract Method** para extrair a região de código que é marcado por comentários de código em seu próprio método e, em seguida, em seguida, executar o código refatorado, **10** será impressa no console.  
  
```c#  
class Program  
{  
    delegate void D();  
    D d;  
    static void Main(string[] args)  
    {  
        Program p = new Program();  
        int i = 10;  
        /*begin extraction*/  
            p.d = delegate { Console.WriteLine(i++); };  
        /*end extraction*/  
        i++;  
        p.d();  
    }  
}  
```  
  
 Para contornar essa situação, verifique as variáveis locais que são usadas nos campos da classe método anônimo.  
  
## Consulte também  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)