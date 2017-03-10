---
title: "Refactoring (C#) | Microsoft Docs"
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
  - "vs.csharp.refactoring.preview"
  - "vs.csharp.refactoring.issues"
  - "vs.csharp.refactoring.buildwarning"
  - "VS.PreviewChanges"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactoring [C#]"
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Refactoring (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Refatoração é o processo de melhorar seu código depois que ele foi escrito, alterando a estrutura interna do código sem alterar o comportamento externo do código.  
  
 C\# Visual fornece os seguintes comandos de refatoração sobre o  **refatoração** menu:  
  
-   [Refatoração Extrair Método \(C\#\)](../csharp-ide/extract-method-refactoring-csharp.md)  
  
-   [Refatoração Renomear \(C\#\)](../csharp-ide/rename-refactoring-csharp.md)  
  
-   [Encapsulate Field Refactoring \(C\#\)](../csharp-ide/encapsulate-field-refactoring-csharp.md)  
  
-   [Extract Interface Refactoring \(C\#\)](../csharp-ide/extract-interface-refactoring-csharp.md)  
  
-   [Refatoração Remover Parâmetros \(C\#\)](../csharp-ide/remove-parameters-refactoring-csharp.md)  
  
-   [Reorder Parameters Refactoring \(C\#\)](../csharp-ide/reorder-parameters-refactoring-csharp.md)  
  
## Refatoração de multiprojetos  
 Visual Studio oferece suporte à refatoração multiprojeto para projetos que estão na mesma solução.  Todas as operações de refatoração que corrigir referências em arquivos corrigir essas referências em todos os projetos do mesmo idioma.  Isso funciona para todas as referências de projeto\-para\-projeto.  Por exemplo, se você tiver um aplicativo de console que faz referência a uma biblioteca de classes, quando você renomeia um tipo de biblioteca de classe \(usando o `Rename` operação de refatoração\), as referências ao tipo de biblioteca de classe no aplicativo do console também são atualizadas.  
  
## Visualização de alterações  
 Muitas operações de refatoração fornecem uma oportunidade para que você revise todas as alterações de referência que uma operação de refatoração deve executar no seu código, antes de confirmar essas alterações.  Para essas operações, de refatoração um  **Visualizar alterações de referência** opção aparecerá na caixa de diálogo refatoração.  Após selecionar essa opção e aceitando a operação de refatoração, o  **Caixa de diálogo alterações de visualização** será exibido.  Observe que o  **Preview Changes** caixa de diálogo possui dois modos de exibição.  O modo de exibição inferior exibirá seu código com todas as atualizações de referência devido à operação de refatoração.  Pressionar  **Cancelar** sobre o  **Preview Changes** caixa de diálogo irá parar a operação de refatoração e nenhuma alteração será feita ao seu código.  
  
## Avisos de refatoração  
 Se o compilador não tem um entendimento completo do seu programa, e é possível que o mecanismo de refatoração não pode atualizar as referências apropriadas, a caixa de diálogo de aviso é exibida.  Esta caixa de diálogo de aviso também fornece uma oportunidade para que você visualize seu código no  **Preview Changes** caixa de diálogo antes de você confirmar as alterações.  
  
> [!NOTE]
>  Se um método contém um erro de sintaxe \(que indica que o IDE com um sublinhado ondulado vermelho\), o mecanismo de refatoração não atualizará todas as referências a um elemento dentro desse método.  O exemplo a seguir ilustra esse comportamento.  
  
 Por padrão, se você executar uma operação de refatoração sem visualizá\-lo referência altera um erro de compilação é detectado em seu programa e o ambiente de desenvolvimento exibe essa caixa de diálogo de aviso.  
  
 Se você executar uma operação de refatoração que tenha  **Visualizar alterações de referência** habilitado e um erro de compilação é detectado em seu programa, então o ambiente de desenvolvimento exibirá a seguinte mensagem de aviso na parte inferior a  **Preview Changes** caixa de diálogo, em vez de exibir o  **Aviso de refatoração** caixa de diálogo:  
  
 **Seu projeto ou uma de suas dependências não compila no momento.  As referências não podem ser atualizadas.**  
  
 Este aviso de refatoração só está disponível para refatorar operações que fornecem a  **Visualizar alterações de referência** opção.  
  
## Refatoração tolerante ao erro e os resultados da verificação  
 Refatoração é o erro tolerante a falhas.  Em outras palavras, você pode executar uma refatoração em um projeto que não é possível construir.  No entanto, nesses casos o processo de refatoração pode não atualizar referências ambíguas corretamente.  
  
 O  **Resultados da verificação de** caixa de diálogo pode notificá\-lo se o mecanismo de refatoração detecta erros de compilação ou descobre que uma operação de refatoração inadvertidamente causa uma referência de código para ligar a algo diferente do que ele foi originalmente vinculado \(problema de religação\).  
  
 Para ativar o resultado da verificação de recurso, diante do  **Ferramentas** menu, clique em  **Opções**.  No  **Opções** caixa de diálogo caixa, expanda  **Editor de texto**e em seguida, expanda  **C\#**.  Clique em  **Advanced** e selecione o  **resultados da verificação de refatoração** caixa de seleção.  
  
 O  **Resultados da verificação de** caixa de diálogo distingue a diferença entre dois tipos de problemas de religação.  
  
### Referências cuja definição deixará de ser o símbolo renomeado  
 Esse tipo de problema de religação ocorre quando uma referência não mais se refere a um símbolo renomeado.  Por exemplo, considere o código a seguir:  
  
```c#  
class Example  
{  
    private int a;  
    public Example(int b)  
    {  
        a = b;  
    }  
}  
```  
  
 Se você usar a refatoração para renomear `a` para `b`, essa caixa de diálogo será exibida.  A referência à variável renomeada `a` vincula\-se agora para o parâmetro que é passado para o construtor em vez da ligação ao campo.  
  
### Referências cuja definição se tornará agora o símbolo renomeado  
 Esse tipo de problema de religação ocorre quando uma referência que anteriormente não se refere ao símbolo renomeado agora se referir o símbolo renomeado.  Por exemplo, considere o código a seguir:  
  
```c#  
class Example  
{  
    private static void Method(object a) { }  
    private static void OtherMethod(int a) { }  
    static void Main(string[] args)  
    {  
        Method(5);  
    }  
}  
```  
  
 Se você usar a refatoração para renomear `OtherMethod` para `Method`, essa caixa de diálogo será exibida.  A referência na `Main` refere\-se agora para o método sobrecarregado que aceita um `int` parâmetro em vez do método sobrecarregado que aceita um `object` parâmetro.  
  
## Consulte também  
 [Usando o ambiente de desenvolvimento do Visual Studio c\#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)   
 [Como restaurar trechos de refatoração C\#](../Topic/How%20to:%20Restore%20C%23%20Refactoring%20Snippets.md)